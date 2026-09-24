# CleanVoice AI — GitHub Pages

A static browser app for speech-focused noise reduction.

## Deploy

Upload these files to the root of a GitHub repository:

- `index.html`
- `manifest.webmanifest`
- `README.md`

Enable **Settings → Pages → Deploy from branch → main → /(root)**.

Then open the generated `https://<user>.github.io/<repo>/` URL. Do not open `index.html` directly from the Files app.

## Processing engine

This build uses `deepfilter-standalone` 1.0.2, a browser/WASM DeepFilterNet3 implementation that accepts a 48 kHz mono Float32 audio buffer and returns enhanced audio. The library/model is loaded from the public ESM CDN on first use.

The app keeps audio processing in the browser. No CleanVoice backend is used.

## Limits / notes

- Maximum input duration: 5 minutes.
- Input must be decodable by the browser's Web Audio API.
- Output is 48 kHz mono 16-bit PCM WAV.
- The reduction slider is intentionally moderate; it controls DeepFilterNet attenuation and a dry/wet blend to reduce artifacts.
- First model load requires internet. Browser HTTP cache may make later loads faster; this is not a guarantee of full offline operation.

## Attribution

DeepFilterNet3 / DeepFilterNet technology is used through the `deepfilter-standalone` package. That package states it is MIT licensed and based on `livekit-deepfilternet3-noise-filter`. See its npm page for attribution and license details.
