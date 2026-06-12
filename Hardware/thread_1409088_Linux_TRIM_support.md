---
title: "Linux TRIM support"
date: 2010-02-17
forum: Hardware
---

### Post by potestas on 2010-02-17
I've been scouring the forumaspheres and can't find any conclusive evidence that Linux does or will support TRIM for Solid State Drives (SSD) - frustrating.  I know the SSD firmware must also support TRIM and many SSD drives now do.  Can anyone confirm TRIM support at the Linux OS level now or in development?  Thanks - RC

---

### Post by eti.que on 2010-02-19
I second this question!

From what I read now and there:
- there's a script existing that somehow "trim" the SSD - called [wiper]("http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper-sh-discussion-thread-(Linux-TRIM-tool)")
- Kernel 2.6.32 [should]("http://forum.notebookreview.com/showthread.php?t=452657") support it

But I don't have much details.

More generally I am as well looking for best practices about SSD, like:
- which FS & options are recommended
- what partitionning & options (swap for hibernation but low swap usage settings)
- tmpfs layout
- application specific tricks (where to store Chromium/Thunderbird's cache, etc.)

Thanks in advance!

---

### Post by portets on 2010-02-19
well i can't halp much, but i know that the new linux file system that probably won't be out for a while and is very experimental has a mode specifically for SSD's.

it's called BTRFS and is supposed to be revolutionary for linux filesystems.

don't expect it for a while though.

---

