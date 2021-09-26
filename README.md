# openlayers-indoorequal ![build](https://img.shields.io/github/workflow/status/indoorequal/openlayers-indoorequal/CI) [![npm](https://img.shields.io/npm/v/openlayers-indoorequal)](https://www.npmjs.com/package/openlayers-indoorequal)


openlayers-indoorequal is an [OpenLayers][ol] library to display indoor data from [indoor=][].

The work is currently in progress.

It provides:

*   a default style of the indoor tiles
*   a way to customize the style
*   a level control to change the level displayed on the map
*   a programatic API to list the levels available and set the level displayed

[**See the demo**](https://indoorequal.github.io/openlayers-indoorequal).

## Install

**With NPM**

    npm install --save openlayers-indoorequal

## Example

Get your free key at [indoorequal.com](https://indoorequal.com).

```javascript
import Map from 'ol/Map';
import TileLayer from 'ol/layer/Tile';
import OSM from 'ol/source/OSM';
import Style from 'ol/style/Style';
import Fill from 'ol/style/Fill.js';
import IndoorEqual, { LevelControl } from 'openlayers-indoorequal';
import 'openlayers-indoorequal/openlayers-indoorequal.css';

const apiKey = '<your-indoorequal-api-key>';

const map = new Map({
  target: 'map',
  layers: [
    new TileLayer({
      source: new OSM(),
    }),
  ],
});

const indoorEqual = new IndoorEqual(map, { apiKey });

const control = new LevelControl(indoorEqual);
map.addControl(control);
```

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

#### Table of Contents

*   [LevelControl](#levelcontrol)
    *   [Parameters](#parameters)
*   [IndoorEqual](#indoorequal)
    *   [Parameters](#parameters-1)
    *   [setStyle](#setstyle)
        *   [Parameters](#parameters-2)
*   [IndoorEqual#change:levels](#indoorequalchangelevels)
*   [IndoorEqual#levelchange](#indoorequallevelchange)

### LevelControl

**Extends Control**

A control to display the available levels

#### Parameters

*   `indoorEqual` **[IndoorEqual](#indoorequal)** the IndoorEqual instance
*   `options` **[object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)**  (optional, default `{}`)

    *   `options.target` **[url](https://developer.mozilla.org/docs/Web/API/URL/URL)?** Specify a target if you want the control to be rendered outside of the map's viewport.

Returns **[LevelControl](#levelcontrol)** `this`

### IndoorEqual

**Extends BaseObject**

Load the indoor= source and layers in your map.

#### Parameters

*   `map` **[object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** the OpenLayers instance of the map
*   `options` **[object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)**  (optional, default `{}`)

    *   `options.url` **[url](https://developer.mozilla.org/docs/Web/API/URL/URL)?** Override the default tiles URL (<https://tiles.indoorequal.org/>).
    *   `options.apiKey` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** The API key if you use the default tile URL (get your free key at [indoorequal.com](https://indoorequal.com)).

Returns **[IndoorEqual](#indoorequal)** `this`

#### setStyle

Set the style for displayed features. This function takes a feature and resolution and returns an array of styles. If set to null, the layer has no style (a null style), so only features that have their own styles will be rendered in the layer. Call setStyle() without arguments to reset to the default style. See module:ol/style for information on the default style.

##### Parameters

*   `styleFunction` **[function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function)** the style function

### IndoorEqual#change:levels

Emitted when the list of available levels has been updated

Type: [array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)

### IndoorEqual#levelchange

Emitted when the current level has been updated

Type: [string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)

## Develop

**Run tests**

    yarn test [--watch]

**Build a new version**

    yarn build

**Generate the documentation**

    yarn doc

## License

BSD

[indoor=]: https://indoorequal.org/

[ol]: https://openlayers.org/
