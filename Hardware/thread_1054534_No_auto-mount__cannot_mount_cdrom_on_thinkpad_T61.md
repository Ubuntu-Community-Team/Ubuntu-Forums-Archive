---
title: "No auto-mount / cannot mount cdrom on thinkpad T61"
date: 2009-01-29
forum: Hardware
---

### Post by Sewerraccoon on 2009-01-29
I just installed Xubuntu on my Thinkpad T61, and so far it's been working very well (all hardware detected and functional). But I've been having problems with my dvd/cd drive. When I insert a cd or dvd, it fails to auto-mount (Note: Automount has worked on Ubuntu on the same system), and I'm unable to manually mount it (I'm pretty sure my syntax it correct: sudo mount -t iso9660 /dev/cdrom /media/cdrom0) and i'm given this message:

mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I have checked my fstab and everything looks correct (i'll attach it to this post). Any input would be much appreciated.

Edit: I forgot to mention that I have had no problem auto-mounting several usb drives (flash and hd), if that's any help

---

