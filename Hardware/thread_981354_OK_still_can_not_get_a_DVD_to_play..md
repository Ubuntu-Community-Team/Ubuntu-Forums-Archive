---
title: "OK still can not get a DVD to play."
date: 2008-11-13
forum: Hardware
---

### Post by rlonnborg on 2008-11-13
Did a fresh install.  When I put the DVD in the first time it said it need the codec.  Pressed continue and it installed the gstreamer and plugin.  Whats the deal.:confused:

---

### Post by taurus on 2008-11-13
Maybe this will help.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by rlonnborg on 2008-11-13
That did help.  It will play maybe a minute, but then it shows a error with gstream.  That is best it has been for two days.

---

### Post by SuperSonic4 on 2008-11-13
What program do you use to play them? I've never had trouble in VLC

```
sudo apt-get install **libdvdcss2** libdvdread3 libdvdnav4 vlc
```

The package in bold is probably most important so you might just want that one if you don't use VLC

---

### Post by taurus on 2008-11-13
Did you install libdvdcss2?  Also, have you tried playing your DVD movie with vlc instead of totem?

---

### Post by rlonnborg on 2008-11-13
OMG it is working.  Thanks guys. There most have been some bad setting in the xserver causing it not to run.  Cause trust me I have tried all of the stuff for the last two days.  Guess it just has to be in the right steps.

---

