# audiodata2pcm

encode a `AudioData` frame from [WebCodecs API](https://developer.mozilla.org/en-US/docs/Web/API/WebCodecs_API) to `PCM` format

## Output format

`PCM Signed 16-bit 16kHz` as an `Int16Array`

## Usage

```js
const stream = await navigator.mediaDevices.getUserMedia({ audio: true });

const trackProcessor = new MediaStreamTrackProcessor({
  track: stream.getAudioTracks()[0],
});
trackProcessor.readable.pipeTo(
  new WritableStream({
    write: async (frame) => {
      const data = audiodata2pcm(frame);
      // ...
    },
    close() {
      console.log(`track processor closed`);
    },
  })
);
```

## Credits

GUO YANKE, MIT License
