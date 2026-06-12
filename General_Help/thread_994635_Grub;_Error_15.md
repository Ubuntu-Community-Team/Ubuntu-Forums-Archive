---
title: "Grub; Error 15"
date: 2008-11-26
forum: General Help
---

### Post by superarmy on 2008-11-26
When I restarted my computer, grub came up with error 15:file not found something like that. I am now unable to boot into Ubuntu and am currently running of the live CD. When I try
find /boot/grub/stage1


I get "find: `/boot/grub/stage1': No such file or directory"

Help please.

---

### Post by superarmy on 2008-11-26
Actually I just opened menu.lst of Grub and it is completely empty. So I think it need rebuilding, how do I do this?

---

### Post by caljohnsmith on 2008-11-27
How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by roshanjose on 2008-11-27
the error indicates that your grub is not installed properly and the grub installation has failed.... put in the cd again and then jump to the step wer u reinstall the grub...everything will be fine then

---

### Post by superarmy on 2008-11-30
Turns out it had to do with that Cruft remover thing, it removed the old Kernel versions too. Therefore Grub could not find them. So I went into the Grub boot menu list and updated the Kernel number and it worked fine.

---

