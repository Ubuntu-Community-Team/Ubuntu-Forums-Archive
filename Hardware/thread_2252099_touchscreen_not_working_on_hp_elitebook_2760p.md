---
title: "touchscreen not working on hp elitebook 2760p"
date: 2014-11-08
forum: Hardware
---

### Post by ksechnick on 2014-11-08
I recently decided to try ubuntu on my old laptop, an HP elitebook 2760p.  Its one of those with a screen that can flip around to look like a tablet, and has a touchscreen that works with either a stylus or a finger.  Overall, things seem pretty good, except that the touchscreen doesn't work.  It's been a quite a while since I had to do any serious digging to get some hardware to work in Linux (they've done a great job of making it automagik over the years), and I'm kinda at a loss where to start.  The touchscreen doesn't do anything, whether I use my finger or the stylus.

The HP website doesn't have any linux drivers, but they do list a Wacom touchscreen driver for windows.  I tried the Wacom program from the software center and the Calibrate Touchscreen program, and neither detected anything.

I have tried both the standard Unity desktop environment as well as Gnome Shell.  Both environments seem to be working fine, except for the touchscreen.

Does anyone have any ideas that I can try?  I'm sure there is a lot of useful diagnostic information I could provide, if I knew the commands to get it.

Thanks in advance

---

### Post by Tekcronic on 2015-02-24
Found [THIS]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/1392887") bug report in relation.

You might check to see if you have a file called [ ***69-xserver-xorg-input-wacom.rules***]("https://launchpadlibrarian.net/190730991/69-xserver-xorg-input-wacom.rules") in the *** /lib/udev/rules.d/ *** folder.

---

### Post by Michel_Goussu on 2015-06-30
Thank you, the link allowed me to fix the elitebook's touchscreen bug

---

### Post by vq1 on 2015-06-30
elitebook 2730
Ubuntu 14.04

I did Gedit to my wacom.rules and pasted in the text from [https://launchpadlibrarian.net/190730991/69-xserver-xorg-input-wacom.rules](https://launchpadlibrarian.net/190730991/69-xserver-xorg-input-wacom.rules)

After restart my touchscreen still does not work with pen

I am new to ubuntu, is there something I missed or did wrong?

---

