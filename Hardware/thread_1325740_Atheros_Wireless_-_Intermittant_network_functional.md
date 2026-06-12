---
title: "Atheros Wireless - Intermittant network functionality"
date: 2009-11-13
forum: Hardware
---

### Post by natrobius on 2009-11-13
Hello,
I am running a fairly new install of Ubuntu 9.10, and just installed the ATI Proprietary driver for my Mobility Radeon HD 3200. After installing the video driver, my Atheros integrated wireless does seem to want to let me surf the web. I see all available networks, and I am able to connect to them, a few pages load in FireFox here and there, but mostly not. Wireless was functioning 100% prior to ATI installation, and immediately started giving problems. I need help! This is my work computer!

Should be an AR5006 chipset, or compatible.. (AR5007, AR5009)

Thanks is advance!

---

### Post by natrobius on 2009-11-13
Ok. lspci says this is the AR5001 chipset.

---

### Post by dummiebeginner on 2009-11-13
Try this it worked for me and I had exactly those same problems of yours in my Atheros.

[http://ubuntuforums.org/showthread.php?t=1286503&highlight=atheros+karmic](http://ubuntuforums.org/showthread.php?t=1286503&highlight=atheros+karmic)

---

### Post by natrobius on 2009-11-13
Did installing the drivers package solve your problem, or installing the backports?

EDIT: Just installed backport. Connection still unstable. Even seems to drop the AP from time to time.

---

### Post by dummiebeginner on 2009-11-13
I first downloaded the backports by Synaptic. I am a beginner and instead of installing only the one they mention in the post I installed the 3 with similar name:

linux-backports-modules-karmic
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

I did so because in case of doubt I prefer to have something useless than missing something. Plus one of them is called wireless, and they didnt mention it.

Then I followed the steps but make sure that you download the driver exactly for your kernel number. Do you know how to check what your kernel number is?

And are you sure you are doing correct the compilation with the right name of the file (it has lots of numbers and letters)

Try again. It really was a miracle for me I had tried hundreds of things but this worked right away.

---

