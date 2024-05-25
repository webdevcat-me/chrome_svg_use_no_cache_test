# chromium-svg-use-no-cache-test

Illustrative repo demonstrating Chromium caches SVG files referenced externally from `<use>` tags, even when caching is disabled both client and server-side.

## Requirements

- docker

## Usage

1. Use the `npx` script to start the server in a new docker container.

        ./npx -y http-server -c-1

2. Notice `Cache: -1 seconds` in the terminal output (meaning, the http server has disabled caching).
3. Open an incognito tab in Chromium.
4. Press F12 to open the dev console.
5. Click on the Network tab and select 'Disable cache'.
6. Visit `http://localhost:8080/`.
7. Notice the request for `circles-no-cache.svg` in the dev console Network tab.
8. Right-click on the reload icon.
9. Select 'Empty Cache and Hard Reload' from the dropdown list.
10. Notice the absence of a request for `circles-no-cache.svg` in the dev console but the green circle is still visible on the page.

This demonstrates the image is being cached although it shouldn't be.

## System details

Chromium Version 125.0.6422.76 (Official Build) built on Debian 12.5, running on Debian 12.5 (64-bit)

![Version 125.0.6422.76 (Official Build) built on Debian 12.5, running on Debian 12.5 (64-bit)](https://github.com/webdevcat-me/chrome_svg_use_no_cache_test/assets/166856956/35683efb-9e09-443e-bff1-29de9e7a3f94)

## Screenshots

### Initial page load

![Initial page load](https://github.com/webdevcat-me/chrome_svg_use_no_cache_test/assets/166856956/953da1d2-d343-4615-93f8-e8d981db0c2b)

### After page reload

![After page reload](https://github.com/webdevcat-me/chrome_svg_use_no_cache_test/assets/166856956/bfff6642-0d10-4465-bfe0-5663a368c6b9)

## Possibly related issues?

- https://issues.chromium.org/issues/41236370
- https://issues.chromium.org/issues/40140856
