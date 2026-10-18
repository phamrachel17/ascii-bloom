# ASCII Bloom

Draw flowers in the air. A webcam toy that tracks your hand: pinch and drag to draw a line, and ASCII flowers bloom along it. Pinch once to grow a single large flower. The flowers are real photos, cut out and converted to characters in the browser.

## Run it

The camera only works over `https://` or `localhost`, so serve the folder instead of opening the file directly:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000> and allow camera access. With no camera, drag with the mouse to draw.

## Controls

| Action | How |
| --- | --- |
| Draw a line of flowers | Pinch thumb and index finger, move, release (or mouse drag) |
| Grow one large flower | Pinch and release without moving (or click) |
| Clear | Make a fist and hold, or press `C` |
| Hide controls for recording | `H` |
| Fullscreen | `F` |
| Status readout | `D` |

Sound is off by default. Turn it on with **Sound**: each flower plays a Rhodes-style electric-piano note through a Dm9 → G13 → Cmaj9 → Am9 progression.

## How it works

- Hand tracking: [MediaPipe Hand Landmarker](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker), loaded from jsDelivr.
- Each flower photo is cut out of its background in the browser, shrunk to a character grid, and drawn with `.:-=+*#%@` by brightness, plus `/ | \ -` along strong edges. Colours come from the photo.
- Sound is synthesised with the Web Audio API; there are no audio files.

Everything lives in `index.html`; flower photos are in `src/`.

## Photo credits

All flower photos are from Wikimedia Commons:

| Flower | Author | License | Source |
| --- | --- | --- | --- |
| Lily (*Lilium auratum*) | Sherwin Carlquist | CC BY 4.0 | [Commons](https://commons.wikimedia.org/wiki/File:(Lilium_auratum_close-up_in_Nikko_Botanical_Garden,_Japan)_-_DPLA_-_17647662f34cfdb4ccf074e6634b3d4b.jpg) |
| Orchid | Mustang Joe | CC0 | [Commons](https://commons.wikimedia.org/wiki/File:White_Orchid2.jpg) |
| Plum blossom | 酎犬 八号 | CC BY 2.0 | [Commons](https://commons.wikimedia.org/wiki/File:ShiraUme_C1_Japan_Flower_02-2005.jpg) |
| Rose | Jamie Street | CC0 | [Commons](https://commons.wikimedia.org/wiki/File:Romantic_rose_from_above_(Unsplash).jpg) |
| Pansy | globalquiz.org | CC BY 3.0 | [Commons](https://commons.wikimedia.org/wiki/File:Another_pansy_close-up.jpg) |
| Spider lily | Yūshi Ishizaki (Naturalis Biodiversity Center) | Public domain | [Commons](https://commons.wikimedia.org/wiki/File:Naturalis_Biodiversity_Center_-_RMNH.ART.751_-_Lycoris_radiata_Herb._-_Y%C5%ABshi_Ishizaki_-_Cock_Blomhoff_Collection_-_pencil_drawing_-_water_colour.jpg) |

The files in `src/` are Wikimedia's resized previews of these photos; cropping, cut-out and ASCII conversion happen in the browser.
