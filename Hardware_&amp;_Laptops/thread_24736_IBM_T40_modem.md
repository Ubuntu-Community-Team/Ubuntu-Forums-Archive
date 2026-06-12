---
title: "IBM T40 modem"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by zagor on 2005-04-08
I've recently moved from Fedora FC2 to SimplyMepis and finally to Ubuntu Hoary.

I'm very glad of this choice, Ubuntu is great, though SimplyMpesi was the only one distribution I've tested which could recognize and activate the internal modem of my laptop. Even Knoppix failed.

I'm using an IBM T40 laptop, with an Agere AC'97 winmodem.
Hoary is kept always up-to-date, on a weekly base.

Is there anybody in the community who can give me directions on how to setup my modem?

Thanks

---

### Post by p!=f on 2005-04-08
What kernel are you running? Do you have linux-restricted-modules-2.6.10-5-<your_architecture> package installed? (it's in the restricted section (look at /etc/apt/sources.list or use synaptic to check you apt repositories))
```

[~] > wajig show linux-restricted-modules-2.6.10-5-k7
Package: linux-restricted-modules-2.6.10-5-k7
Priority: optional
Section: restricted/misc
Installed-Size: 12820
Maintainer: Daniel Stone <daniel.stone@ubuntu.com>
Architecture: i386
Source: linux-restricted-modules-2.6.10
Version: 2.6.10.5-1
Provides: nvidia-kernel-1.0.7174
Depends: linux-image-2.6.10-5-k7, module-init-tools, nvidia-kernel-common
Suggests: nvidia-glx, avm-fritz-firmware-2.6.10-5
Filename: pool/restricted/l/linux-restricted-modules-2.6.10/linux-restricted-modules-2.6.10-5-k7_2.6.10.5-1_i386.deb
Size: 4857872
MD5sum: a49b05127d3ae93757d588cd49c5e3ba
Description: Non-free Linux 2.6.10 modules on AMD K7
 This package provides restricted modules for Linux version 2.6.10 on
 AMD Duron/Athlon.
 Currently the following modules are included:
  - madwifi (Atheros)
  - fglrx (ATI)
  - nvidia
  - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusba, fcpci,
    fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
  - **ltmodem (Winmodem)**
 .
 These modules are "restricted" because they are not available under a
 completely Free licence.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by zagor on 2005-04-08
Thanks for the quick  reply.
I'm not in Ubuntu right now, I'll check your suggestion once at home.
I'll post later on, but it seems probably that package is missing, for I'm sure that the ltmodem module is not present in my system.

---

### Post by zagor on 2005-04-09
Hi,

after a great deal of efforts and with the help of the thread [http://www.ubuntuforums.org/showthread.php?t=21940&page=4&pp=10](http://www.ubuntuforums.org/showthread.php?t=21940&page=4&pp=10),
I finally succeded in having the modem recognized.
Still don't know if it works, though I'll test it soon.

Thanks

---

