---
title: "Problem with 9.04 boot."
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by mngsailing on 2009-05-17
I upgraded to 9.04, keeping my old menu.list.

Now I cannot boot.  When I "ESC" during grub, it shows only a list of 8.10 kernels.  How do I connect to the 9.10 kernel? 

If I let it go on, it states " PCI  Unsupported PM cap regs version (7) "
and sometimes  "over-current change on port 2".

Anyone got ideas for moving forward?

---

### Post by martinkoo on 2009-05-18
Hi, I think we all have the same problem (I saw another guy with the same problem as you just few pages from here). I think the problem is that you stayed using Grub instead of Lilo. Maybe I did something a bit different, but I think we are in the same state right now. (See my post: [http://ubuntuforums.org/showthread.php?t=1162524](http://ubuntuforums.org/showthread.php?t=1162524)).

Well anyway I still didn't find any right answer for the problem ;). Keep on searching.

---

### Post by Mark Phelps on 2009-05-18
I'm not at my 9.04 machine right now, so I don't have the specific kernel info, but the general procedure is that you would have to edit your menu.lst file to add lines for the 9.04 kernel entries. You would do that by opening a terminal and entering "gksudo gedit /boot/grub/menu.lst"

Basically, you could copy the lines in your menu.lst for your current kernel and change the title, root, kernel, and initrd lines to match what is needed for 9.04.

If you have 9.04 installed on your machine, use "sudo blkid" to get a list of UUIDs.  One of them will be your 9.04 installation.

Update:

Here's some sample menu.lst code from my box (you will have to edit for yours:

> 
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b1aaa347-fa2c-4873-85ca-eec189d3d8e3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b1aaa347-fa2c-4873-85ca-eec189d3d8e3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet


---

