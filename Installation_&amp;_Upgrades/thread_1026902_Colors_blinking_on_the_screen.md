---
title: "Colors blinking on the screen"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by wilan_ on 2008-12-31
Right after I installed Ubuntu, system didnt run. Instead I had different colors blinking on the screen (red, blue, green, yellow, white). I've tried to install other distros and had the same exact effect. No idea what is the problem. If anyone is familliar with this, please let me know how i can fix it.

---

### Post by estyles on 2008-12-31
> **wilan_ said:**
> Right after I installed Ubuntu, system didnt run. Instead I had different colors blinking on the screen (red, blue, green, yellow, white). I've tried to install other distros and had the same exact effect. No idea what is the problem. If anyone is familliar with this, please let me know how i can fix it.

I don't know what the problem is, but we'll see if I can help at all...  First, do you know what type of video card you have?  Second, can you access your /etc/X11/xorg.conf file and post it here?  If you are dual-booting windows on the machine, you can download Ext2IFS to be able to access your ext2/ext3 partitions and find that file.

When you boot up, can you get to a terminal by pressing Alt+Ctrl+F1 or Alt+Ctrl+F2?  If so, you can log in and type "cat /etc/X11/xorg.conf".  That may give us a clue to what the problem is.  You could also do "nano /etc/X11/xorg.conf" and set it to use VESA, which is like a compatibility mode for video.  I don't know exactly what to do to use VESA, but a google or ubuntu forums search should help with that...

---

### Post by wilan_ on 2008-12-31
I have Nvidia Geforce 8800 GTS.
I am dual-booting with windows. When i select Ubuntu in grub, it shows that cool ubuntu loading bar and then it goes straight to blinking colors. Cant get the terminal.

---

### Post by estyles on 2008-12-31
So, even while the blinking colors are up, hitting Alt+Ctrl+F1 does nothing?

That video card shouldn't cause problems like *that*.  Best thing I can suggest is search on how to enable VESA drivers, then download Ext2IFS in windows and edit your /etc/X11/xorg.conf file on your linux partition (although now that I think about it, I'm not 100% sure that ext2ifs allows you to *write* to ext3 partitions - I know it can read from them...).

I don't know what else might be causing the problem, but video card seems like a good place to start.  If it's caused by any distro that you try to install, then I can't think of anything other than your video card or motherboard that could be causing it.

Another silly thing to try - if you are using an analog cable, unplug it (while the color bars are flashing) and plug in a digitial cable (from your monitor to video card).  If you are using a digital cable, try and analog cable.  It shouldn't do anything different, but my monitor for some reason is much more flaky with Ubuntu if I use an analog cable.

If you don't mind trying one more distro, give Puppy Linux a try.  It's very small and runs entirely in RAM, and I know that it includes an option to start X with VESA drivers enabled.  A quick download and runs right off the LiveCD without having to install.

---

