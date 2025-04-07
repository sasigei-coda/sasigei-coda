## Hi there 👋

const c = document.querySelector('#c')
const ctx = c.getContext('2d')

const dpr = Math.min(2, window.devicePixelRatio)

c.style.imageRendering = 'pixelated'
c.style.width = '100vw'
c.style.height = '100vh'

let prevTime = 0

const setup = () => {
  c.width = window.innerWidth * dpr
  c.height = window.innerHeight * dpr
  
  ctx.fillStyle = 'black'
  ctx.fillRect(0, 0, c.width, c.height)
}

setup()

function angle(cx, cy, ex, ey) {
  var dy = ey - cy;
  var dx = ex - cx;
  return Math.atan2(dy, dx); // range (-PI, PI]
}


const distance = (x1, y1, x2, y2) => Math.hypot(x2 - x1, y2 - y1);

const grid = (v, a) => {
  return Math.floor((v - a / 2) / a) * a
}

const palettes = [
   [
    // '#001219',
    "#80FFDB",
    "#72EFDD",
    "#64DFDF",
    "#56CFE1",
    "#48BFE3",
    "#4EA8DE",
    "#5390D9",
    "#5E60CE",
    "#6930C3",
    "#7400B8"
  ],
  [
    '#003049',
    '#d62828',
    '#f77f00',
    '#fcbf49',
    '#eae2b7',
  ],


  [
    "#f72585",
    "#b5179e",
    "#3f37c9",
    "#4361ee",
    "#4895ef",
    "#4cc9f0"
  ],

  [
    // '#001219',
    "#4f000b",
    "#720026",
    "#ce4257",
    "#ff7f51",
    "#ff9b54",
    "#4EA8DE",
    "#5390D9",
    "#5E60CE",
    "#6930C3",
    "#7400B8"
  ],

  [
    '#390099',
    '#9e0059',
    '#ff0054',
    '#ff5400',
    '#ffbd00',
  ]
]

let palette = palettes[3]

const points = []

const createPoint = (x, y) => {
  return {
    x,
    y,
    px: x,
    py: y,
    magnitude: 150 + Math.random() * 150
  }
}

for (let y = 0; y < c.height; y+=50) {
  for (let x = 0; x < c.width; x+=50) {
    points.push(createPoint(x, y))
  }
}

const animate = (time) => {
  requestAnimationFrame(animate)
  const delta = time - prevTime
  
  ctx.fillStyle = 'rgba(0, 0, 0, 0.02)'
  ctx.fillRect(0, 0, c.width, c.height)
  
  // const cell = 175
  const cell = 200
  
  const getKey = (x, y) => `${grid(x - cell/2, cell)},${grid(y - cell/2, cell)}`
  
  const spatial =
  html, body {
  margin: 0;
  padding: 0;
  overflow: hidden;
}
<canvas id="c">
