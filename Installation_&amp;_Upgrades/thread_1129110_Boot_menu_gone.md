---
title: "Boot menu gone"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by DManX04 on 2009-04-18
I'm not sure this is the right forum for this, but here goes.

My boot menu is gone after trying to re-install windows on another partition. The install failed about halfway through, and now it goes to the windows boot menu (Safe Mode, Safe mode with networking, etc), but there is no Ubuntu option. The manual for Windows says that the boot sequence is changed one time during the install and then changes back, but I assume because of the failed install it was never changed back. 

Any ideas how to fix this? I'm currently running a liveCD and I can access all my files from my Ubuntu install.

---

### Post by ronparent on 2009-04-18
Your failed install of windows appears to have managed overwriting the mbr. Windows WILL do that whever it is installed. You have to boot from the Ubuntu live cd and open a terminal (Applications > Accesssories > Terminal.

Enter the following commands:

sudo grub
Grub> find /boot/grub/stage1

This last command will output the location of Ubuntu ie (hdx,y). Copy that output to the follwing:

grub > root (hdx,y)
grub > setup (hdx)

This will restore grub to the mbr and should load your menu on rebooting!

---

### Post by tarun.winlin on 2009-04-18
> sudo grub
Grub> find /boot/grub/stage1

**ronparent** can you please explain what are the different stages of ubuntu boot & what is the significance, or may be give a pointer for where to read?

---

### Post by ronparent on 2009-04-18
If you are using the grub boot loader, the 1st operation is performed by the mbr written to the very first section of your boot drive. When written by grub it directs loading to the partition in which the main body of grub code is installed. When written by windows further loading operations are directed to the window boot files in the windows partition. Yor main concern here is to restore grub to the mbr. That is done by the code I gave you written to an Ubuntu live cd terminal. You can get a complete education on how grub functions at this site:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Good luck.

---

