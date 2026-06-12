---
title: "do I have a hard disk failure?"
date: 2011-04-13
forum: Hardware
---

### Post by leptep on 2011-04-13
Can someone help me analyse my problem?
I can no longer access my desktop!!!

I'm running Ubuntu 10.04 on a hp pavillion
If I turn on the computer I get:

[B]no init found: try passing init=bootarg
Busy Box V1.13.13 ......

enter 'help'
(initramfs)_[/B]

I tried running different live cds(ubuntu 9.10, ubuntu 10.04) from cds and usb's as well.
didn't load, i get the following:
[B]stdin: error 0
/init: line 7: can't open /dev/sr0:no medium found
/init: line 7: can't open /dev/sr0:no medium found
unable to open '/dev/sda'
[/B]
eventually live cd ubuntu 10.10 loaded.
following concerning posts i found i tried the following:

1. **e2fsck -C0 -p -f -v /dev/sda1** through terminal or gparted. i get this message:
 [B]filesystem mounted or opened exclusively by another program?
[/B]
note that gparted shows me the partition and knows how much used and unused space i have on sda1

2. i run disk utility, click on the hard disk and choose check filesystem, i immidiatly get the message "file system check completed" "File system is **NOT **clean.
If i click on the volume and press mount it turns forever and nothing happens.

3. i tried installing ubuntu 10.10 thinking i can make it dual boot with ubuntu 10.04, i got to step 3 and the installer freezed


so what's the diagnostic?

---

