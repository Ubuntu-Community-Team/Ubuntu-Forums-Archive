---
title: "Radeon Mobility 7500 / DRI"
date: 2008-05-17
forum: Hardware
---

### Post by calman on 2008-05-17
[COLOR="Red"]**EDIT: See post #3**[/COLOR]

so I'm using a video card...
```
caleb@ubuntu:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
```

which is probably using the open source radeon driver...
```
caleb@ubuntu:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

```

and I have direct rendering...
```
caleb@ubuntu:~$ glxinfo | grep "direct rendering"
direct rendering: Yes
```

but the problem is, when I run compiz or enable Advanced Desktop Effects, everything gets really weird.  I see bits and pieces of other windows I had open hours or minutes ago.  I had Compiz working before, with someone else's Xorg.conf but watching videos and scrolling webpages was extremely slow, so I'm trying to get the radeon driver working from scratch.  I'm on Hardy.  it's either not configured correctly or I'm using something other than the actual radeon driver (no idea how to check that)

please help!

xorg.conf attached **[COLOR="Red"](before I changed it as stated in post #3)[/COLOR]**

---

### Post by calman on 2008-05-19
bump

---

### Post by calman on 2008-05-19
k, so I figured out I am using the radeon open source driver.  Compiz works fine now, with some tweaks to xorg.conf, but video playback is weird:

Sometimes videos play fine, at good speed and all, but when I move the windows, the window moves without the video.  I cannot make videos transparent with the window.  I cannot zoom in on windows with videos.  This is all in VLC/Totem, I don't know about Flash.

Also, sometimes, seemingly after I have gone a while without rebooting, videos get really really slow.

I still have the extremely slow webpage scrolling problem.

PLEASE help.  There are other people with this problem too...

---

### Post by calman on 2008-05-24
Well, thanks for nothing guys.  Problem never solved...I even tried Xubuntu with no luck.  Compiz has nothing to do with the problem.  It works fine after I reboot, but out of the blue, I don't know what triggers it, Ubuntu just starts getting unbearably slow.  I'm going to XP I guess, since nobody's going to help.

---

