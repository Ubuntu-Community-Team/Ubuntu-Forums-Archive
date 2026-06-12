---
title: "Resolution Problem: Dell gx620 (Intel 945) - 800x600 max"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by gvanessen on 2009-11-05
Hello,

I have a Dell GX620 with an Intel 645 chipset (no video card) and a Dell E716fp monitor (optimum resolution: 1280x1024).

I've done a fresh install but my screen resolution is stuck 800x600, and I can't get beyond this resolution, whatever I try.

This is my xorg file:

> Section "Device"
Identifier "Intel 945G "
Driver "intel"
EndSection

Section "Monitor"
	Identifier	"Dell E716fp"
EndSection


Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 945G Integrated Graphics Controller"
Monitor "Dell E716fp"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600"
EndSubSection
EndSection

Any suggestions how fix this?

Many thanks in advance

---

### Post by gvanessen on 2009-11-05
Anybody with a suggestion?

---

### Post by Unovert on 2009-12-07
Have u seen this?
[http://www.linuxquestions.org/questions/linux-newbie-8/screen-resolution-problem-in-ubuntu-362160/](http://www.linuxquestions.org/questions/linux-newbie-8/screen-resolution-problem-in-ubuntu-362160/)
 
Most blogs seem to suggest Modifying xorg.conf file (Display setting). 
 
I have the same issue on Dell D830: Ubuntu, /etc/X11 folder does not have xorg.conf or any other config file. There must be a command to restart X11 config proces which will generate xorg.conf file.

---

### Post by georgemc on 2009-12-07
Hi,

This post helped me to get from 800x600 to 1280x1024 on 9.04.

[http://ubuntuforums.org/showthread.php?p=8302145#post8302145](http://ubuntuforums.org/showthread.php?p=8302145#post8302145)

I found that I had to modify xorg.conf to reflect my monitor settings in "Section Monitor" properly, especially the Horizontal and Vertical refresh.  That seemed to make a big difference.

Also "xrandr" is your friend.  You can easily play with different screen sizes and see what the system thinks is available.

Cheers

---

