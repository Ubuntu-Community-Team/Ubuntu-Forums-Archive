---
title: "Ubuntu 8.04 / nvidia 8800M GTX driver woes"
date: 2008-11-17
forum: Hardware
---

### Post by danotron on 2008-11-17
Hey all.

I'm having a problem with the current nvidia drivers on an Alienware m15x laptop under Ubuntu 8.04 x64.
CPU is an Intel X9000, video card is an nvidia Geforce 8800M GTX, driver version is 177.82.

When I first installed Ubuntu, a generic display was detected, resolution limited to 800x600.  I halted my shell, shut off X, installed the driver, and it all seemed to work fine... one system reboot later, however, and it no longer appears to be working.  Resolution is capped at 640x480.  I hit ctrl-alt-f1 so I could shut off X and take a looksee, but all it seems to do is black out the screen and lock the system.  Sadly I'm obnoxiously new to the weird world of linux -- I really am not sure where to get started here.  Any words of wisdom from other Ubuntu / m15x / 8800MGTX users out there?

Thanks!

Dan

---

### Post by Milkium on 2008-11-17
Try using EnvyNG to get the proper nvidia driver.

You can get it here: [http://linux.softpedia.com/get/System/Software-Distribution/EnvyNG-36961.shtml](http://linux.softpedia.com/get/System/Software-Distribution/EnvyNG-36961.shtml)

It worked for me.

---

