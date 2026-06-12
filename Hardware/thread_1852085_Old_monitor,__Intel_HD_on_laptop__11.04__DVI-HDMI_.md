---
title: "Old monitor,  Intel HD on laptop / 11.04 / DVI-HDMI screen flicker"
date: 2011-09-29
forum: Hardware
---

### Post by tearsinrain on 2011-09-29
Hey guys,

I am running Ubuntu 11.04 on an HP with Intel Core i3 / Intel HD graphics.

When I tried hooking up my old Samsung SyncMaster 204B in Windows 7 the (external) screen flickered and blacked out a lot.

Looking for solutions I found this post at [another forum]("http://www.nvnews.net/vbulletin/showthread.php?t=82982"):

> This is how you edit your xorg.conf to activate reduced blanking:

1) Generate the appropriate Modeline:
$ cvt 1600 1200 60 -r
This creates the following output (well not exactly, I edited the comment and the mode name):
# 1600x1200 59.92 Hz (CVT 1.92M3-R) hsync: 74.01 kHz; pclk: 130.25 MHz
ModeLine "1600x1200_59.92_rb"  130.25  1600 1648 1680 1760  1200 1203 1207 1235 +hsync -vsync
Add these two lines in /etc/X11/xorg.conf in Section "Monitor".

In Section "Screen" add to each mode list "1600x1200_59.92_rb" as first entry.

In Section "Device" add this line:
  Option       "ExactModeTimingsDVI"   "yes"
This forces the driver to use the exact mode line and not the closest  setting retrieved from EDID (I had quite a hard time figuring that out.)

How to check if Reduced Blanking was activated (apart from the absence of blackouts :-) ) :
Monitor info in the OSD shows a line frequency of 74.1 kHz. (Without Reduced Blanking: 74.9)

Thanks a lot to users pe1chl and kulick from whose postings I got this wisdom.

Enjoy!
Andy a.k.a. WakeFossilThe issue seems to be that the model didn't do well with full resolution DVI/HDMI so the mode has to be changed. This worked in Windows through the Intel control panel.

So, finally, the problem: I don't know how to do something like the operations in the above quote in 11.04, mostly because the xorg.conf file doesn't seem to be used.

Any ideas on activating "reduced blanking" for an external monitor?

Cheers,

tir

---

