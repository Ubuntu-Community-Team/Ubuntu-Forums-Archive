---
title: "Resolution / aspect ratio problem on a widescreen laptop"
date: 2008-08-19
forum: Hardware
---

### Post by GulGhan on 2008-08-19
Hi,

I'm fairly new to Ubuntu and Linux in general, and I thought someone here might be able to help me out with a small problem I've got. But first, my situation: I've installed Ubuntu 8.04.1 on a Packard Bell laptop. Ubuntu runs in the monitor's native resolution of 1400x900, and there are plenty of other display modes to choose from in System | Preferences | Screen Resolution. The refresh rate is only 50 Hz, but I've read that that's caused by the nvidia drivers I'm using (it was 60 Hz before), and this doesn't really bother me. What bothers me is this:

When I use wine to start a game that wants to run in a different resolution than 1400x900, say 800x600, what happens is that the whole screen is being used horizontally to display a line of 800 pixels, and then it also tries to use 600 pixels vertically to display the image (which isn't possible because the aspect ratio isn't 4:3). The result is that I can't see the lower part of the image. I wouldn't really mind if the image was stretched, or if there were black borders of unused space on the screen, but I would like to see the entire image.

I've made a few attempts at correcting this by changing xorg.conf. From the beginning there was almost no information in the Monitor and Screen sections of the file, just some generic values for the mandatory fields. I've been looking for a possible option for one of those two sections that might determine the monitors behavior when it has to display an image with a different aspect ratio, but no luck so far.

I can print out the contents of configuration files, but like I said, there's nothing in xorg.conf so this seems pointless.

Any advice on this or pointers as to where the solution can be found would be greatly appreciated.
Big thanks in advance to anyone taking the time to reply.

---

