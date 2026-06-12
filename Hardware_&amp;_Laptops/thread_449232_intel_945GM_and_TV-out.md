---
title: "intel 945GM and TV-out"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by janek87 on 2007-05-20
is this impossible to get this work? if i press from laptop Fn+F3 the screen flicks, but no picture in TV...

---

### Post by ramjet_1953 on 2007-05-20
What video driver do you have installed?

915resoloution   or

xserver-xorg-video-intel 

The latter is the newest driver and will probably do what you want.

If you haven't got it installed, copy and paste this into a terminal and after it has finished loading up, re-boot your system.

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

Regards,
Roger :cool:

---

### Post by janek87 on 2007-05-21
i installed xserver-xorg-video and 915 driver, but nothing...

---

### Post by janek87 on 2007-06-01
anybody has a clue?

---

### Post by snifer on 2007-06-01
After plugging your cables, restart X  (you can use ctrl+alt+backspace).
Search the forum, since other people are getting good results by editing xorg.conf.

---

### Post by suoko on 2007-06-02
I have the same card and the tv-out is alwasy enabled .
This happened with new intel xorg drivers (not i810).
However tv image is B/W. I have to find a way to adjust it...

---

### Post by ramjet_1953 on 2007-06-02
Hey suoko!

Could your problem with monochrome output be that you are putting out NTSC video into a PAL receiver?

Regards,
Roger :cool:

---

### Post by awaldram on 2007-06-03
That is the output problem with the I915 chipset ntsc default.
I can't find any utility out there to switch to PAL

---

### Post by suoko on 2007-06-03
> **awaldram said:**
> That is the output problem with the I915 chipset ntsc default.
I can't find any utility out there to switch to PAL

that's what I'm looking for too...
It could also be the output which should be COMPOSITE instead of SVIDEO

I've posted here too but I'm still waiting for a reply...
[http://ubuntuforums.org/showthread.php?t=361124&page=13](http://ubuntuforums.org/showthread.php?t=361124&page=13)

---

### Post by justDIY on 2007-06-10
I just tried my laptop to a TV as well, and have the monochrome picture problem.  Laptop is a compaq nc6320, with 945GM video built in.

First, I can't "switch" to tv output while Ubu is running, I have to do it before the OS boots.  Second, while TV out is active, the lcd panel displays all sorts of weird patterns and colors.

The boot-up screen, ubu logo and progress bar are in color, but as soon as X starts, the display goes BW.   TV is a NTSC tv with s-video input.  I have tried all resolutions between 640x480 and 1400x1050, all are BW.

---

### Post by suoko on 2007-06-15
BUMP!

so there's no way to change tv output from NTSC to PAL ???
have to wait for gutsy?

---

