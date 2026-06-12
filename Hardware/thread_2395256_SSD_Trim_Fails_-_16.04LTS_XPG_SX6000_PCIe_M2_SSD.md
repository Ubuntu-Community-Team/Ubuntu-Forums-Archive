---
title: "SSD Trim Fails - 16.04LTS XPG SX6000 PCIe M2 SSD"
date: 2018-06-29
forum: Hardware
---

### Post by dusenberg2 on 2018-06-29
Gigabyte BRIX GB-BKI5A-7200 i5-7200U, M2 PCIe, Intel HD620 graphics.
SSD: ADATA ASX6000NP-128GT-C 128GB XPG SX6000 PCIe M.2 
BIOS: American Megatrends v2.18.1263 (2017), EFI boot, secure boot OFF
OS: Linux Mint 18.2-MATE Sonya  4.10.0-35-generic #39~16.04.1-Ubuntu

I got a new Brix recently with XPG SX6000 SSD, and installed Mint 18.2 Mate on it.  Fstrim fails with message 'fstrim: /: FITRIM ioctl failed: Operation not supported'. 

I have the same OS and kernel on a relatively new Lenovo E570 which has same i5-7200U as the Brix but an OEM SSD, and fstrim works without problem

I've searched for solutions and found several old posts about kernel bugs/issues with some SSDs (eg Samsung) but nothing that points to fixing my problem.  Don't know what to do next - can anyone help, please?

---

### Post by oldfred on 2018-06-29
Same error:

fred@bionic-z97:~$ fstrim -v / 
fstrim: /: FITRIM ioctl failed: Operation not permitted

Note: this specific command has never ever worked for me.  :)
       [http://xkcd.com/149/](http://xkcd.com/149/)

fred@bionic-z97:~$ sudo fstrim -v /
[sudo] password for fred: 
/: 21.3 GiB (22849024000 bytes) trimmed

---

### Post by QIII on 2018-06-29
Odd.  I wonder if, despite them being m.2, they might go through a USB bus.  That's what that message looks like.

---

### Post by QIII on 2018-06-29
Just looked around.  It is a bona fide PCIe controller.  Weird.

---

