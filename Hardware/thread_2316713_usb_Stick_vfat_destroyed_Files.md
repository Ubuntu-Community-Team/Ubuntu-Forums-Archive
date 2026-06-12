---
title: "usb Stick vfat destroyed Files"
date: 2016-03-10
forum: Hardware
---

### Post by Fahqu1 on 2016-03-10
ich speichere meine Keepassx Datei xxxx.kdbx auf einen USB-Speicher (VFAT).
Nach auswerfen und wieder einstecken ist diese kaputt. Die md5-summe ist verändert.
Wer kann helfen?



 
 
 I save my KeePassX File xxxx.kdbx on a USB memory (VFAT).
 After eject and reinsert is this destroyeds. The md5 sum is changed.
 Who can help?

---

### Post by sudodus on 2016-03-10
Please ask in English :-)

The Ubuntu Forums are international and use English. It will make it possible to give and get help all over the world.

-o-

Generally, it is very important to unmount all partitions on a USB device before unplugging it. Otherwise files and file systems can be corrupted. (Unmounting will flush data buffered in RAM to the target drive.)

It might or might not work to try

1. testdisk
2. photorec

If the file was not completely written, it may not be possible to recover, maybe you can recover part of it.

You can get these programs from [https://www.cgsecurity.org/](https://www.cgsecurity.org/)

---

### Post by C.S.Cameron on 2016-03-10
At least make sure to unplug parent drive with multi partition flash drives.
Do not try to format a multi partition flash drive with Windows.

---

