---
title: "855gm and svideo &quot;a solution&quot;"
date: 2008-07-05
forum: Hardware
---

### Post by Sirius1977 on 2008-07-05
Hello 855gm users,

here is a possible solution to get the svideo-out working.

1. use i810 driver instead of the actual intel driver
2. add the following lines to the device section:

> Option       "MonitorLayout" "TV,LFP"
Option       "Clone" "yes"

3. get nvtv with i855 patch from here: [http://ubuntuforums.org/showthread.php?t=40865&page=4]("http://ubuntuforums.org/showthread.php?t=40865&page=4")

To get color i have to click on xmode and then select the resolution i want.

If you have a black screen on video playback choose another video output. For me gl works great in vlc.

Hope this helps.

---

### Post by ghthor on 2009-05-31
When I write my own xorg.conf and restart the xorg server I get an error that the device is not present

heres my xorg.conf
```

Section "Device"
   Identifier    "Configured Video Device"    [LEFT]   Driver     "i810"
   Option     "MonitorLayout" "TV,LFP"
   Option     "Clone" "yes"
EndSection

[/LEFT]
Section "Monitor"    [LEFT]    Identifier    "Configured Monitor"[/LEFT]
EndSection    
    [LEFT]Section "Screen"
[/LEFT]
    Identifier    "Default Screen"    [LEFT]    Monitor     "Configured Monitor"[/LEFT]
    Device     "Configured Video Device"
[LEFT]EndSection
[/LEFT]

```

---

### Post by airblade on 2009-12-11
Finally i got the S-VIDEO / TV-OUT working on my Thinkpad R51 (with Intel 82852/855GM).
Thanks to your solution Sirius.

I have tried several distros and versions of Ubuntu.
After reading the [bug-report on launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/6270") and what [Sirius1977 wrote]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/6270/comments/66") **i installed Ubuntu 8.04 i386**.

Then i used [Sirius1977's posted xorg.conf]("http://paste.ubuntuusers.de/389739/") file (copied the whole file to /etc/X11/xorg.conf and restarted the xserver).
This actually got the TV working - altho it didnt have any colors and the resolution was small.

So on, i downloaded [the patched nvtv]("http://ubuntuforums.org/showthread.php?t=849994&highlight=855gm+svideo"), installed the deps (sudo apt-get build-dep nvtv), and compiled it (./configure && cd src && make).

And now, following Sirius1977 instructions, i started the nvtv (sudo ./nvtv) chosed prefered mode ( 1024x768 ) -> xmode. And voila!

Thanks Sirius1977! :)

---

