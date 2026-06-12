---
title: "Acer AspireOne 751h won't boot USB UNR"
date: 2009-09-05
forum: Hardware
---

### Post by taenus on 2009-09-05
I've just picked up a 751h after reading positive reviews of both the hardware and other's experience with Linux on it.  While I've found posts about tweaking, my problem is more basic.

UNR on the flash drive won't boot to install.

I've got a JetFlash Transcend 8GB stick that I previously had a Knoppix/VFAT setup on that I'm attempting to install from.  I started off by wiping it and loading the image by:

```
dd if=/dev/zero of=/dev/sdi
dd if=ubuntu-9.04-netbook-remix-i386.img of=/dev/sdi
```

When I pick the USB stick from the boot menu (seems to be correctly noticed), I just get: *Operating System not found*

Any ideas on how to get this to boot the installer?  The wired NIC also does PXE, but I'm trying to keep things simple.

---

### Post by taenus on 2009-09-05
DOH!  The BIOS was 2 versions behind.  Once I flashed it (and unfortunately had to do it from Winders), the USB booted fine.

---

