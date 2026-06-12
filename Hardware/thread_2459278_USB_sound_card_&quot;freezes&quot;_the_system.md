---
title: "USB sound card &quot;freezes&quot; the system"
date: 2021-03-15
forum: Hardware
---

### Post by piteur on 2021-03-15
Hi everyone,
i've recentely bought the Cuvave Cube Baby,a small and cheap guitar effect. Connecting the effect to a USB port it should become a regular USB sound card with ins and outs.

As for the price, i would not complain in case i won't be able to let it work with Ubuntu, but i would give it a try.

The first time i connected it i've noticed the computer slowed down, then i realized there were some system freeze.

Here's the lsusb output when i plug it in (it's on bus 2 / device 3):

```
joe@extensa:~$ lsusb
Bus 003 Device 002: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 301a:5555   
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

And this is the amixer log (i'm not including all the part relative to my integrated soud card):

```
amixer: Mixer load hw:1 error: Connection timed out
Card hw:1 'Device'/'SmartlinkTechnology USB2.0 Device at usb-0000:00:1d.1-1, full speed'
  Mixer name	: 'USB Mixer'
  Components	: 'USB301a:5555'
  Controls      : 7
amixer: Mixer hw:1 load error: Connection timed out

```

Obviously on the producer site there's no mention about any linux support, and in the download section [http://www.cuvave.com/download](http://www.cuvave.com/download) you see software just for win or mac, no linux.

Do i have any hope? Should i post the question in any audiophile linux forum?

Thanks everyone!

---

