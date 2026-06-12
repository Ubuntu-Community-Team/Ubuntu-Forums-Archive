---
title: "Toshiba Satellite A105-S4274 Sound Stopped"
date: 2010-01-16
forum: Hardware
---

### Post by Daedalus.Maelstrom on 2010-01-16
Hi,

I'm new to Linux and wanted to share this bug I've found. I have a Toshiba Satellite A105-S4274 all stock hardware. After installing Linux Ubuntu v9.10 (Karmic Koala)
I clicked: SYSTEM > ADMINISTRATION > HARDWARE DRIVERS and found a software modem that needed to be installed. I clicked 'Activate' and rebooted.
On reloading I had no sound in the RythmBox music player or in any online content such as YouTube. The only exception was audio played with RealPlayer. So I
deactivated the driver, rebooted, and sound is back. I dont really need the software modem for anything I use but wanted to post the bug for a future fix.

Modem Details:

The SmartLink modem daemon is the application part of thedriver for recent modems produced by Smart Link Ltd.

This package replaces (along with hardware access drivers) the olddriver generation (2.7.x) which consisted of kernel modules only.

It needs a kernel driver to access the hardware. This can be eitherrecent ALSA (shipped with a newer kernel (>=2.6.4) with Alsa supportand intel8x0m module) which is sufficient for basic operation anddata/Internet connection, or the SmartLink kernel driver which isprovided by separate packages which you can build using the source fromthe sl-modem-source package.

This driver enables the usage of many software modems, as commonly found in laptops.

---

