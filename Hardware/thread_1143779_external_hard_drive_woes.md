---
title: "external hard drive woes"
date: 2009-04-30
forum: Hardware
---

### Post by rose34 on 2009-04-30
Hi Everyone,

I recently brought an 60GB external usb hard drive, with the intention of backing up my photos and music (I don't have that much, so 60 is plenty at the moment!) The drive I brought is here - 

[http://www.amazon.co.uk/60Gb-Portable-Inch-External-Drive/dp/B001PAC67O/ref=sr_1_14?ie=UTF8&s=electronics&qid=1241093455&sr=8-14](http://www.amazon.co.uk/60Gb-Portable-Inch-External-Drive/dp/B001PAC67O/ref=sr_1_14?ie=UTF8&s=electronics&qid=1241093455&sr=8-14)

I have plugged it into the computer, expecting it to show up like my USB memory stick, but nothing. So I restarted the computer thinking that might help, and when Ubuntu was loading it went through a process of scanning something like /dev/sda which it has never done before - this indicates to me that the drive has been detected, but when I go to the folder /dev there is no sda folder?

I have run fdisk -l with these results:

> joe@joe-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb6eeb6ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9566    76838863+  83  Linux
/dev/sda2            9567        9729     1309297+   5  Extended
/dev/sda5            9567        9729     1309266   82  Linux swap / Solaris

None of the above look like it to me but I may be wrong...

Can anyone tell me what I need to do to be able to access this drive, and start copying data please? I am fairly new to linux, but know most of the basics.

Cheers,
Joe

---

### Post by rose34 on 2009-04-30
I got it working - I had plugged it into a USB extension cable, and the LED came on so I assumed it was getting power. However it can't have been enough, as when I plug it direct into the PC it works fine.

Cheers

---

