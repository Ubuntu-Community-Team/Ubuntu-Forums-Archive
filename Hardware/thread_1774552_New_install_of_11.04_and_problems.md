---
title: "New install of 11.04 and problems"
date: 2011-06-03
forum: Hardware
---

### Post by VVAW on 2011-06-03
I installed the l1.04 64 bit after install on laptop dell e6400
I update some drivers I have 3 problems.

1. I have a Hp monitor connected it doesn't connect to it.
2. I don't see a option when I close my lid nothing happens.
3. Appearance I don't see visual effects
4. Also how do I get it back to orignal look I don't like the bar on the side

---

### Post by VVAW on 2011-06-03
problem 1 and 4 I fixed..

Here is info I got

lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GT218 [NVS 3100M] (rev a2)

/usr/lib/nux/unity_support_test -p
Ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no
Please help me out here I need to get this up a running

---

### Post by collisionystm on 2011-06-03
There isn't a 'Visual effects' option anymore. Compiz is already enabled by default.

To get rid of the unity bar, log out, click on your name, at the bottom choose Ubuntu Classic in the drop down, enter your password and login.

Hit the power button in the upper right, click on system settings in the menu. go to monitors, hit detect monitors

---

### Post by VVAW on 2011-06-03
ok I get this 
you need to install the driver if you wish to the unity desktop enable desktop effects or run software that requires 3d acceleration such as games.

I think I got everything working but my 
video problem and closing my lid of my laptop

---

### Post by VVAW on 2011-06-04
tried to get this to work however couldn't go as planned. So I install 10.04 last night in vmplayer I still cant turn on visaul effects 
error 
DESKTOP EFFECTS COULD NOT BE ENABLED.

HOW TO I TROUBLESHOOT ISSUE

---

