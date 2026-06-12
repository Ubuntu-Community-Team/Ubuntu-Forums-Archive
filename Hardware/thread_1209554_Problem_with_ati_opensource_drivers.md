---
title: "Problem with ati opensource drivers"
date: 2009-07-10
forum: Hardware
---

### Post by Shaggin Shea on 2009-07-10
I am running ubuntu 9.04 jaunty. I have an ati card

I have been here and maybe I am missing something 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

This is are the steps I have taken up till now.
 lspci shows the following
Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

My xorg.conf file shows (device section)
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

I can only display 800*600 and maybe 640*480 though I don't want to bother going to a lower resolution.

I have very little in the way of display capabilities and video is not smooth.

glxgears gives me

david@david-desktop-ubuntu904:~$ glxgears
327 frames in 5.0 seconds = 65.191 FPS
360 frames in 5.0 seconds = 71.913 FPS
361 frames in 5.0 seconds = 72.188 FPS
341 frames in 5.0 seconds = 68.041 FPS

If I don't get desktop effects or 3d effects to work that won't be such a big deal.
I'm not sure, but that seems terrible!
The proprietary drivers for my card are a last resort (ati has deemed my card legacy)

---

### Post by Shaggin Shea on 2009-07-10
Does anybody know what to do here?

---

### Post by phantom3113 on 2009-07-10
I'm not sure on the specifics, but ATI seems to have given a huge digital finger to all those using ATI brand cards released anytime before May :-/ So, that basically means that unless you end up really lucky or have a brand new ATI card, you're pretty much screwed graphics-wise in 9.04. I heard about this shortly after Jaunty was released and decided to stick with 8.10 because of it. I won't say it's impossible for a fix, but I believe it to be very VERY unlikely. Thanks a lot, ATI...

Edit: If I recall correctly, it has something to do with a new version of fglrx that just doesn't work with most/all older cards on 9.04. (picture for your viewing pleasure)

---

### Post by Shaggin Shea on 2009-07-11
As I understand it the fglrx driver was the proprietary driver which is in ATI's legacy packages when it comes to drivers. I'm talking about the open source ati driver which should at least give me a better screen resolution. I am not trying to acheive 3d effects, though it would be a nice ADDED bounus. I have tried in the past to install fglrx and found it was troublesome. I may just try it again to give me possibly better 2d perfermance but I would prefer to use the open source raedon!

---

### Post by Shaggin Shea on 2009-07-12
Maybe it has something to do with my screen. I have a citizen LCD screen and know it can support better resolution then 800*600. Here is my full xorg - begining comments

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

