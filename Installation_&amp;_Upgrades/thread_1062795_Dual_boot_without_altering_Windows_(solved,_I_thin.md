---
title: "Dual boot without altering Windows (solved, I think)"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by mount_evans on 2009-02-07
I have a drive for Windows and a drive for Ubuntu.  My goal was to have a dual boot system without making any changes to the Windows drive--that way, if anything went wrong, I could just make the Windows drive the default boot drive again.  I think I succeeded.  First, I made the Windows drive the "second" hard drive via the motherboard's Setup routine.  Then I installed Ubuntu on what was now considered the "first" hard drive, and made sure that the boot loader was put on that drive as well.  There remained the problem of editing grub so as to have it boot Windows off of the "second" hard drive.  A helpful person in alt.os.linux.ubuntu suggested the following lines for the last entry in /boot/grub/meny.lst:
```
title           Microsoft Windows XP Professional
root            (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader     +1
```
And it seems to be working.  If anyone knows of any potentially nasty side-effects from doing things this way, please let me know.

---

### Post by AlexBellisBrown on 2009-02-07
Thats correct. Its how i did mine and i have no ill effects. :)

---

