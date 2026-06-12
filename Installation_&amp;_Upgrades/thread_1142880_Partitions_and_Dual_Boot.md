---
title: "Partitions and Dual Boot"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by twooften on 2009-04-29
I am about to install windows(i know, but...) on a partition, I have done this before and f**ked my computer all up.
So I think that I am ready to do it again but I want to run the procedure past some of you guys to make sure I am not going to screw it all up again.

so I have

/dev/sda1 = Ubuntu i386x32 Boot
/dev/sda2 = Ubuntu i386x64 
/dev/sdb1 = Storage
/dev/sdb2 = Future Windows

Ok, so because I installed x64 last it is loading that grub every time the computer boots, which is no big deal.
I am running x32 for all my regular uses. There was an ubuntu install on sdb1 that I was using before I did a bunch of upgrades, I had a couple of big directories on there so I deleted everything else and resized it to get some free space for a windows install. 
So this is where I am at, I haven't even rebooted yet after the resize.
These are the steps I am about to take.

1. Boot to x64, get grub to re-evaluate what is installed and what is not.
    This is because, it was seeing my old 7.10 install on sdb1
2. Restart just to make sure things are still fine.
3. Hide sda1 and sda2 so the windows install wont see them.
   **Q. Will grub still load from sda2?
4. Install windows.
5. If windows is the only thing booting and being seen, then boot to live
   cd.
6. If grub is still loading, boot to sda2 and edit grub to hide the ubuntu
   installs when loading windows, and make sure sda1 is still the default
   boot.

so any insight would be a great help.
Thnx in advance.

---

### Post by ronparent on 2009-04-29
Just a short comment. If you change the boot order in bios to boot on what is now sdb and install window to that drive like you indicate, then windows will write that mbr and leave the one on what is now sda alone. So when you want to boot back to ubuntu you can change the boot order again to boot on the grub mbr. You would have to add your new windows install to the /boot/grub/menu.lst but at least you would have access to both systems in the meanwhile by changing the boot order.

---

### Post by twooften on 2009-04-29
Ah, thats perfect!
Should I hide sda anyway? Just in case. 

Plenty Thnx
I will reply with the outcome.

---

### Post by ronparent on 2009-04-30
Glad to hear it. It's not necessary to hide sda. Not desireable to hide it if you want to share files with windows.

---

