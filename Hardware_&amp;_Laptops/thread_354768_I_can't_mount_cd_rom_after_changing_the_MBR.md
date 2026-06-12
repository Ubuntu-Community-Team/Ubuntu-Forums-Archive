---
title: "I can't mount cd rom after changing the MBR"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by apaek on 2007-02-06
So I am new to Ubuntu and the Linux world in general, and I am dealing with a very frustrating problem.  I am working on a laptop, and I installed a fresh copy of Ubuntu on one half of my drive, and then installed Windows XP.  I soon learned what seems to be common knowledge, that Windows overrides the boot record.  I used the live cd and entered the following commands:
sudo grub
find /boot/grub/stage1
root (hd?,?)
setup (hd0)
quit
which I got from:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Anyways the MBR was restored and I could log on to Ubuntu, but now both Windows and Ubuntu can't detect my cd-rom.  Windows could detect it before I changed the MBR, but not after.  Ubuntu gives me the following error:
 mount: special device /dev/scd0 does not exist


I followed all the advice on this forum
[http://ubuntuforums.org/showthread.php?t=339733&page=2&highlight=mount+cd-rom](http://ubuntuforums.org/showthread.php?t=339733&page=2&highlight=mount+cd-rom)
and I seem to have the same problem as this guy as I got the exact same responses they did.  The only difference is that my cd rom does not work in windows at all.My Ubuntu version is Dopper Drake 6.06 I have a sager notebook.  Any help will be greatly appreciated.

---

