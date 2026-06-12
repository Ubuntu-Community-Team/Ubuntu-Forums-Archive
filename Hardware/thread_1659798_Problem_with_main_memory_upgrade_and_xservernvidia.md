---
title: "Problem with main memory upgrade and xserver/nvidia"
date: 2011-01-04
forum: Hardware
---

### Post by awwylach on 2011-01-04
Hi there,

first of all, happy new year to all.

I have a problem with a memory upgrade and the xserver and/or the nvidia graphics drivers / adapter. I am not much into hardware so I hope somebody can help me on that issue.

Hardware: Asus Notebook z53sv with nvidia geforce 8600M GS 256MB with Ubuntu 8.4.4 LS, Kernel 2.6.24-28

The new memory is ok and brand new, was checked within the store.
2 x 2GB PC2-5300 CL5 20 - Pin S0Dimm

Short story:

Between xmas and new year I had problem with the main memory of that notebook, i suspected the main memory is broken/corrupted. Processes kept segfaulting (like I was not able to restart apache and such), gnome did not work properly like it used to be. Also the windows vista (another partition acted funny and popped up message like 'memory exhausted'. Anyway, I bought new memory, 2 x 2GB. I used to have 2GB of main memory and and thought now it is the best time to upgrade and buy 4GB of main memory.
Result: Problem is fixed and the system is working as it used to be (windows). 
I use the notebook mainly with linux (ubuntu) because it is somekind like a demo machine/private development machine for internet applications. The machine boots up like always and the problem arise when the upsplash screen appears. The complete display is screwed up, it looks a little like mandelbrot graphics, with inverted colors. When I log in all I see is a green screen with a square (that is the mouse pointer). I can not do any actions. That is with the new installed 4GB. If anybody wants to see how the screwed upslash screen looks, let me know, I can email the image (took a photo with my cell).

Then I thought to remove 1 of the 2GB simm to get the old amount of memory like before might fix the problem. And duh, booting up ubuntu, everything works fine again, upsplash screen comes like it used to be and I can login and use gnome.

Can anybody point me out why the installation is not working with 4GB of memory? Is there a problem with the graphics memory / main memory, maybe memory regions overlap, interfers or something.. ? I can not see any errors in the logs (I checked Xorg.0.log, dmesg, etc), no errors at all. All seems to get loaded as it should be.

Are there any adjustments I can do to make that memory upgrade to 4GB again, any config I have to adjust with the nvidia driver? 

I plan to upgrade ubuntu to a more recent version soon but not now. I do not want to break the system now since I am in the middle of a software project and the notebook contains the same system state like my development servers. 

Any hints to get the 4GB working are greatly appreciated. If I can provide any info please let me know.

Thanks in advance. 
AW

---

