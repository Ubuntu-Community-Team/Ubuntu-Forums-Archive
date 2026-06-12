---
title: "Add support for E-MU 0204 (USB soundcard)"
date: 2011-03-23
forum: Hardware
---

### Post by snop on 2011-03-23
Hello,
I recently bought an E-MU 0204 DAC. Being such a new device it is not yet supported by default in Ubuntu.
There is, however, a patch to enable this device here:
[http://www.mentby.com/Group/alsa-list/patch-enable-e-mu-0204.html](http://www.mentby.com/Group/alsa-list/patch-enable-e-mu-0204.html)
This patch, however, is already applied to alsa's git.
All in all, what I did to make it work is the following:

Go to this thread to download an automatic alsa update script:
[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

The first step using the script downloads the needed software (including alsa 1.0.24 at the time of writing this).
Once the downloading concludes you can either apply the patch or, as I did, download latest alsa-driver from git and replace the files quirks.c and quirks-table.h. If you use the script with default settings those 2 files will be at:
/opt/Alsa-1.0.24/alsa-driver-1.0.24/alsa-kernel/usb

I already filled a bug report asking for this patch to be backported to Ubuntu 11.04:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/741132](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/741132)

PD: You can download daily git snapshots here [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/)

Edit:
It seems that Ubuntu 11.04 already has this patch applied. Great!

---

### Post by sdlugosz on 2011-04-16
thank you, it works for me on 10.10
:guitar:

---

### Post by ABOBA on 2013-01-10
Hi, do you have system crash problem with E-mu 0204 when turning it off?

---

