---
title: "Kernel update and grub changes ?"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by wimmelis on 2009-01-16
Dear all, 


With a kernel change grub changes its menu list, but I am booting through the windows boot manager and therefore have a file that contains the data of the first 512 byte of the /boot partition containing grub. Now, when I upgrade kernel then this file suddenly seems to not work anymore, if I create a new one, then I can boot again. 
I used to not have this problem, but now when I install a new kernel, I need to repeat that file creation procedure. Has grub changed ?


Thanks, 
WM

---

### Post by Elfy on 2009-01-16
It appears to now use UUID instead of partition numbers, can't think of anything else that's changed.

> title		Ubuntu jaunty (development branch), kernel 2.6.27-7-generic
uuid		67d245ca-d0a5-48d3-88e8-9ffe97f759f3

instead of 
> title		Ubuntu jaunty (development branch), kernel 2.6.27-7-generic
root            (hd0,1)

---

### Post by meierfra. on 2009-01-16
> therefore have a file that contains the data of the first 512 byte of the /boot partition containing grub. 

This file points to the exact physical location of the stage2 file (the number of sectors from the beginning of the hard drive to the stage 2 files). So if the stage2 file gets moved during an  update, you have  to recreate the file.


You can make your life a little bit easier by using [bootpart]("http://www.winimage.com/bootpart.htm").  Bootpart will create a file which points to the boot sector of your Ubuntu partition.
So if you run into problems after updates you just need to reinstall grub via "sudo grub, root (hdX,Y), setup (hdX,Y)", but you will not have to use "dd" to recreate the file in your windows partition.

---

### Post by wimmelis on 2009-01-17
Hi,


Thanks for your replies.

In relation to the bootpart tool, it does not seem to indicate being compatible with Vista, and since the boot-manager has changed substantially between XP and Vista ... Or can anyone confirm it also works with the Vista boot-manager ?


Thanks, 
WM

---

### Post by meierfra. on 2009-01-17
> Or can anyone confirm it also works with the Vista boot-manager ?

It does.  Actually for Vista I recommend using EasyBCD.  EasyBCD uses bootpart internally but has a nicer GUI.

Links:
[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")
[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

---

