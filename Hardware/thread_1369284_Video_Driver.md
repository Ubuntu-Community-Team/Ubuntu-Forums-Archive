---
title: "Video Driver"
date: 2009-12-31
forum: Hardware
---

### Post by Yitzach on 2009-12-31
I'm running 64 bit 9.10 Karmic. I have an ATI Radeon Xpress 200M graphics card/chipset in a Dell Inspiron 1501 laptop. And I have Google Earth.

Google Earth was flashing parts of frames when the viewer is moving or when the mouse is moving over the view frame.
Ctrl+Alt+F# was not working. I changed to any one of them and I would get a white fuzz that averaged to grey. Ctrl+Alt+F7 would return me to the GUI.
I would get the same grey if I asked the computer to rotate the display.

I had problems loading the proprietary driver from ATI because something was getting in the way. I suspect it was the OS as ATI said that the driver had packages up through Jaunty Jackalope. I searched the forum for [solutions]("http://ubuntuforums.org/showthread.php?t=1259601") and TheFuzz4 suggested envy. Envy loaded but caused boot problems, but it cleared what ever was holding ATI from working. I loaded ATI and it caused boot problems as well. I ran "apt-get install xserver-xorg-video-ati" as suggested by oldos2er in the terminal emulator with the intention of restoring the open source drivers provided in the ISO.

xserver-xorg-video-ati appears to not be the one provided in ISO. Google Earth now runs correctly. The other terminals work correctly except I can't log in because I don't know what to tell it. The screen is distorted as I have a wide screen format and not the 4:3 screen ratio it expects. I can't rotate and the resolution is not the best it can be.

A video driver that didn't cause Oblivion the break loose would be great.

---

### Post by hansdown on 2009-12-31
Hi Yitzach.

I hope this helps.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Yitzach on 2010-01-04
ATI will be of no help in this case as 9.3 is the last version of the driver to support my hardware but does not support my OS.

---

