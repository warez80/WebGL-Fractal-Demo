This readme has been adapted from the `Documentation.txt` file that I originally submitted with this project.

# Fractal Exploration
## by William Brigham, CAP4720 Fall 2019

# Project Proposal
An exploration of different types of fractals and the
ways that they can be rendered.

The goal will be to create examples of fractals from most,
if not all of these categories:
https://en.wikipedia.org/wiki/Fractal#Common_techniques_for_generating_fractals

I would like to demonstrate the computational intensity of
rendering different types of fractals and hopefully be able
to create some original fractals.

These would be implemented in GLSL fragment shaders, probably 
just being rendered on a simple quad mesh.

Ideally, I would just be using the Wikipedia pages for each 
fractal type as a resource. I may end up looking at some 
online papers if I need to and am able to find some.

# Algorithms and Data Structures
All of the fractals shown are rendered onto a single plane
mesh, meaning that all geometry is being constructed in 
real-time.

The 3D fractal demonstration uses the "raymarching" technique
to draw the geometry. This means the use of signed distance
functions and space-deformation functions in order to create
the environment.

The Henon Map and Random Walk demonstrations use a 
double-buffering technique to maintain state. Basically, the
result is rendered into two WebGLRenderTargets, which are
flip-flopped between. This allows the previous frame's output
to be fed into the shader as a uniform, creating a sort of 
feedback buffer. These are referred to as "compute shaders"
within the source code of the project. In both of these demos,
a single particle is being kept track of by using the bottom left
corner pixel color as the particle's information (i.e. position,
color, size, etc.). Everything else is updated by the particle's
data, as well as being augmented by what was previously at the pixel.
This allows the particle to effectively draw on the screen like a pen.

In the Henon Map demo, this particle is randomly re-spawned about
every two seconds. This allows the space to get modeled in a
better visual way without needing many different particles.

The quadtree demo could itself be considered a data-structure,
but no data is actually being stored in it, so `/shrug`.

Some distance functions used in this project are not ones that I came
up with, such as the signed-distance formula for an equilateral triangle. 
There are comments in the source code of this project that
link to where I got these functions from.

# How to run this project
Just open the `project.html` page in a web browser.
