---
title: "Fglrx problem on 12.10"
date: 2012-10-28
forum: Hardware
---

### Post by Jeroen De Dauw on 2012-10-28
I have a radeon HD 7800 card to which I have 3 monitors hooked up. I'm having problems getting the fglrx driver to work on Ubuntu 12.10 though. Got version 12.10 of the driver [here ]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx"), created distribution specific packages and installed those. This worked but after I rebooted my box a second time it no longer does. If I open my display manager it only shows one monitor (the output is actually going to two of my three monitors, cloned) named "default" rather then the expected "DVI-D-0", "DVI-D-1", "DP-0" (or something like that). When I try to open the catalist control center it gives the following error:

> There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.

I removed the driver and reinstalled it the same way I did yesterday and am not getting it to work again. I also tried installing the thing from the repos (ie with apt-get), using the installer without creating distribution specific packages and using the previous version of the driver. All failed. No idea how to get it to work again in a way it stays working.

Any pointers would be very much appreciated.
[]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")

---

### Post by RLDr on 2012-10-28
Please Read Carefully:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

I have successfully activated the dual graphics (Intel HD + AMD ATI) of my Dell Vostro 3550 Laptop running Ubuntu 12.04 LTS after a long time effort.:guitar:

---

