---
title: "nouveau unknown i2c port"
date: 2012-06-11
forum: Hardware
---

### Post by Stonecold1995 on 2012-06-11
I use Linux (specifically Kubuntu 12.04) on a computer with a GeForce GTX 675M GPU (the computer is the MainGear ex-L 15 SuperStock gaming laptop). The driver I use is nouveau (I don't think a proprietary version for Linux has come out yet). Anyways, every time I boot my computer the kernel spams the system logs with things like this:
[some time] [drm] nouveau 0000:01:00.0: unknown i2c port 49
[some time] [drm] nouveau 0000:01:00.0: unknown i2c port 56
[some time] [drm] nouveau 0000:01:00.0: unknown i2c port 57
[some time] [drm] nouveau 0000:01:00.0: unknown i2c port 48
[some time] [drm] nouveau 0000:01:00.0: unknown i2c port 54

It's repeated over and over, many thousands of times. See [here]("http://s15.postimage.org/sxbg25et7/screenshot1.png") too.

What does this mean? My computer DOES boot, and the graphics look fine. Does it mean the GPU isn't detected and the computer is falling back to integrated graphics? Or is it just a harmless error and I'm freaking out for no reason (I'm freaking out because this GPU is very new and I worry that the nouveau driver for it is very unstable/incomplete). I've done a few tests to see if the GPU works, including using the command *glxgears* (which gave an average of 59.6675 FPS) and *glxinfo | grep direct* (it said direct rendering WAS enabled). However, things like VLC media player, which ran fine on my other computer, struggles playing high quality video files on my new computer (it freezes for about five seconds every couple of minutes), and if I'm right VLC will use hardware acceleration when available. Basically what I want to know is, in this Linux computer, is the GPU active and available to perform hardware acceleration or is the GPU too new and I'll have to wait months/years for a decent nouveau driver to come out or the proprietary one to be released?

I already asked in the Nvidia forums but haven't received a reply yet.

---

### Post by Redblade20XX on 2012-06-11
Most likely the nouveau driver doesn't have full support (yet?) for 3d acceleration for that card. You can check out there main site for any updates though.

-Red

---

### Post by Stonecold1995 on 2012-06-12
Does it have *any* 3D support or does my computer have to fall back to the Intel graphics in my i7?

Is there a way to test the capabilities of my GPU on Linux (it's abilities, not a benchmark)?

---

### Post by Stonecold1995 on 2012-06-12
If I can't fix the problem, is there at least a way to hide those messages (like some way to send anything with a specific string of characters, for example "unknown i2c port", to /dev/null instead of being displayed)?  Because any time I try to log in or do anything when X isn't started, I quickly loose where I am because anything I'm typing is quickly thrown off screen by all the nouveau errors being put out.

---

