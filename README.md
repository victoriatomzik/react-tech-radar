
<img width="600px" src="https://raw.githubusercontent.com/omerg/react-tech-radar/master/screenshots/Screenshot_1.png">

# React Tech Radar

A library that generates an interactive radar, inspired by [thoughtworks.com/radar](http://thoughtworks.com/radar).

## Installation

Using [npm](https://www.npmjs.com/):

    npm install --save react-tech-radar

## Quick Start

```jsx
import React from 'react';
import Radar from "./components/Radar/Radar";

function App() {

    const setup = {
        rings: ['adopt', 'trial', 'assess', 'hold'],
        quadrants: ['tools', 'techniques', 'platforms', 'languages'],
        data: [
            {
                name: 'D3',
                quadrant: 'tools',
                ring: "assess"

            },
            {
                name: 'TypeScript',
                quadrant: 'languages',
                ring: "trial"
            },
            {
                name: 'Storybook',
                quadrant: 'tools',
                ring: "adopt"
            }
        ]
    };

    return (
        <div className="App">
            <Radar {...setup} />
        </div>
    );
}

export default App;
```

## Props Setup

The following 3 props should be configured in order to setup the tech radar:

 - quadrants
 - rings
 - data

### data

data prop is an array of JSON elements representing the description of technologies.

Elements in the array should be in the following form:

__Example:__
```json5
{
data: [
          {
              name: 'D3',
              quadrant: 'tools',
              ring: "assess"
          },
          {
              name: 'TypeScript',
              quadrant: 'languages',
              ring: "trial"
          },
          {
              name: 'Storybook',
              quadrant: 'tools',
              ring: "adopt"
          }
      ]
}
```

### quadrants

quadrants prop is an array of strings which represent slices of the circular radar. 
Any data element with the matching quadrant value goes into this slice

Elements in the array should be in the following form:

__Example:__
```json5
{
  quadrants: ['tools', 'techniques', 'platforms', 'languages']
}
```

### rings

rings prop is an array of strings which represent at what level these technologies are adopted.
For each element in rings, every quadrant is divided into rings. Innermost ring is the first element of the rings array and 
it usually represents the place for the most adopted technologies.

__Example:__
```json5
{
  rings: ['adopt', 'trial', 'assess', 'hold'],
}
```

## Configuration Options

| Prop         | Description    | Default Value |
| :---         |     :---:      |          ---: |
| width     | The overall width of the main DOM element       | 700px      |
| fontSize     | Font size of elements       | 12px      |
| itemFontSize     | Set this if you want the items to have a different size than titles of quadrants and rings. If not set, defaults to fontSize       | 12px      |
| colorScaleIndex     | A value from 0 to 5 for different collections of colors. See [Storybook Color Schemes](https://react-tech-radar.netlify.com/?path=/story/color-schemes--with-1) section for colors of each option.      |5      |
| radiusDiminish     | Radius of rings is not equal because of this constant. Each radius is x times greater than the outer one and x is this constant.      | 1.5      |

#### Prop Types

```jsx
Radar.propTypes = {
    quadrants: PropTypes.array.isRequired,
    rings: PropTypes.array,
    data: PropTypes.array,
    width: PropTypes.number,
    fontSize: PropTypes.number,
    itemFontSize: PropTypes.number,
    colorScaleIndex: PropTypes.number,
    radiusDiminish: PropTypes.number
};
```

## Storybook

You can see various states of the radar (such as color schemes, results of configurations, etc.) on the [Storybook Page](https://react-tech-radar.netlify.com).

## Google SpreadSheets Integration

If you want a very quick data integration, you can check out the Google Spreadsheets example.

The source code for the example is in [examples](https://raw.githubusercontent.com/omerg/react-tech-radar/master/examples) folder and also there is a running example in [Storybook](https://react-tech-radar.netlify.com).

If you plug in [this data](https://docs.google.com/spreadsheets/d/1YXkrgV7Y6zShiPeyw4Y5_19QOfu5I6CyH5sGnbkEyiI/) you'll see [this visualization](https://react-tech-radar.netlify.com/?path=/story/basics--with-data-from-google-spreadsheet)

## License

[MIT](./LICENSE)
