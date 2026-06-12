---
title: "reinstalling grub on a dual HDD system"
date: 2008-09-03
forum: General Help
---

### Post by sergentsiler on 2008-09-03
hello! i need explicit instructions on how to wipe out windows while reinstalling or restoring grub. on my system, i have the windows partition on the first HDD with Ubuntu on the second hdd. i want to delete windows, format the entire HDD with ext3 instead of NTFS and still have grub work for me without having to move hdds or any insane stuff.:lolflag:

---

### Post by caljohnsmith on 2008-09-03
> **sergentsiler said:**
> hello! i need explicit instructions on how to wipe out windows while reinstalling or restoring grub. on my system, i have the windows partition on the first HDD with Ubuntu on the second hdd. i want to delete windows, format the entire HDD with ext3 instead of NTFS and still have grub work for me without having to move hdds or any insane stuff.:lolflag:
Probably the best solution for your scenario would be to make sure Grub is installed in the MBR of the Ubuntu HDD, and then set BIOS to boot the Ubuntu HDD first. Then it doesn't matter what you do with the Windows HDD. 

To install Grub to the MBR of the Ubuntu HDD, just do:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][will return your Ubuntu partition in the form of (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how it goes or if you need more details/info.

---

