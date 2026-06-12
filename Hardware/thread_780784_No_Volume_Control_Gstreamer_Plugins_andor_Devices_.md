---
title: "No Volume Control Gstreamer Plugins and/or Devices Found"
date: 2008-05-03
forum: Hardware
---

### Post by derubermensch on 2008-05-03
That's the error my volume control applet throws when I try to access its preferences now.  The Sound control panel throws this error on attempting to test sound with Auto-Detect:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

Where should I start?

---

### Post by CJay554 on 2008-05-11
bump

---

### Post by cek1227 on 2008-05-13
I am getting the same error. Who knows what's going on? It just started this week. I install a bunch of GStreamer packages, but nothing is fixing the problem. I get the bongo drums when the logon screen comes up, but then after that, nada.

---

### Post by cek1227 on 2008-05-13
> **cek1227 said:**
> I am getting the same error. Who knows what's going on? It just started this week. I install a bunch of GStreamer packages, but nothing is fixing the problem. I get the bongo drums when the logon screen comes up, but then after that, nada.

This might help:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204667](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204667)

I'll know better after a reboot.

---

