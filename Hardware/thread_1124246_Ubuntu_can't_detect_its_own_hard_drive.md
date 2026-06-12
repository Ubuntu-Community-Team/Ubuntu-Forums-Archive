---
title: "Ubuntu can't detect its own hard drive"
date: 2009-04-13
forum: Hardware
---

### Post by RandomMatt on 2009-04-13
I just did an update of my system to the latest Jaunty packages (I suppose this serves me right, then =(), and now all of a sudden when I try to boot into Ubuntu it stalls for a while while trying to detect the root hard drive, then fails and drops to a BusyBox session.

I tried to replace the UUIDs with hd(0,1) and /dev/sda2 in the grub prompt, but no avail. The kernel seems to have literally lost its ability to interface with hard drives! (grub is on the same drive)

I tried a different kernel, the realtime kernel, but that crashed during hardware detection. So it looks like I'll have to do a reinstall... or is there any way I can recover from this?

Thanks in advance,

Matt

---

### Post by RandomMatt on 2009-04-13
Fixed the problem!

I had a working Debian system already installed, so I went into that, used chroot to change root to that of the Ubuntu system, and used apt to reinstall the kernel image. There were a few errors reported because of the incompatibility between the two systems, but it seems to have booted fine.

---

