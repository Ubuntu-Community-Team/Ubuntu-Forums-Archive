---
title: "Dell Inspiron 1501, ATI Mobility 1150, and FGLRX"
date: 2010-05-09
forum: Hardware
---

### Post by CyberXZT on 2010-05-09
Hello everyone. I have been using Ubuntu for quite a long time. At the moment I am using Ubuntu 10.04 x64. I am trying to get into gaming however my GFX card (ATI Mobility 1150) does not work with the latest FGLRX drivers offered and the opensource ones dont work well. I remember the drivers working a long time ago back in Ubuntu 8.04 and lower. My question is how would I go about installing the FGLRX drivers from 8.04 (FGLRX 8.3 if I recall) onto my 10.04 system?

---

### Post by AlexZaim on 2010-05-09
Try
```
sudo sh ./driver.run --listpkg

```
... or something like that.
And you'll see the list of supported distributions for the particular driver.
I done it myself recently and there is no support (from my driver) for 9.10 nor 10.04. I haven't tried creating the source package though...
So i'm stuck on 10.04 with no driver

By the way.. what opensource drivers did you use? I'm not sure i understood what you meant.

---

### Post by CyberXZT on 2010-05-09
Im using the opensource ati drivers that automatically come with ubuntu. And I cant run that command because I dont have any drivers to use to install from. ATI no longer supports my card so I would like to know if its possible to install the FGLRX 8.3 drivers from Ubuntu 8.04 somehow or if anyone has a way to install them otherwise.

EDIT:

I found 8.3 drivers for x64 Linux ([http://support.amd.com/us/gpudownload/linux/8-3/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/8-3/Pages/radeon_linux.aspx)) and did the --listpkg command and found that it will compile up to Ubuntu 8.04.

---

