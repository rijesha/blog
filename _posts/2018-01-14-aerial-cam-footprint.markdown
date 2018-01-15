---
layout: post
title: Aerial Camera Ground Footprint with a gimbal 
date: 2018-01-13 00:00:00 -0700
description: Exploring aerial footprints, quaternions, and angles
img: cam_footprint_tester.PNG # Add image post (optional)
tags: [Jekyll, GitHub Pages] # add tag
---
## Questions
* If I have a camera pointing straight down from a UAV what area on the ground will the be captured in the image?
* How does this change if the UAV experiences roll/pitch/yaw?
* What happens if this camera is on a gimbal?

Do you have these questions? Well lets see the answers.

## Preliminary Information
Before we get started it is important to cover a few basics. This tutorial will use the angle units of degrees, distance units of meters, and GPS coordinates in UTM.

It is important that when converting from UTM->WGS84 or WGS84->UTM that all of your units start in the same coordinate systems. This tutorial will not cover how to convert these units, but it is important that all conversions follow the same math and are reversible. (Don't obtain coordinates from different sources or formats because they may have used a slightly dfferent conversion method than what you did.)

In this tutorial I will be using Tait-Bryan angles. This is an angle naming convention so you can use whatever you like. The only changes int he math will be a negative sign here and there. [Angle Conventions](https://en.wikipedia.org/wiki/Euler_angles)

![Tait-Bryan Angle Convention. Courtesy Wikimedia](https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Taitbrianzyx.svg/1225px-Taitbrianzyx.svg.png)


## Basic Ground Footprint
The basic footprint of a camera point straight down is determined by some very basic trigonometry. A camera's sensor and lens combination will produce a certain angle of view (AOV). You can look this up for you camera. AOV can be broken into a horizontal field of view (HFV), and a vertical field of view (VFV). [Check out this wikipedia page for more info](https://en.wikipedia.org/wiki/Field_of_view)

So from our UAV we can make a triangle with the ground.
![The camera angle of view makes a triangle]({{site.baseurl}}/assets/img/simple_triangle.png)

If we cut this triangle, by drawing a line from the UAV to the ground we can get 2 smaller triangles. Each of these smaller triangles are right traingles so we can use trigonometric identities to solve for distance on the ground.
$$a^2 + b^2 = c^2$$

![Screenshot of tester application]({{site.baseurl}}/assets/img/cam_footprint_tester.PNG)


### Setting up the blog site
