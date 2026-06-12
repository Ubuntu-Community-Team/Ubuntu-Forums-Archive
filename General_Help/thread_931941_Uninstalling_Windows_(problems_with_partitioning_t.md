---
title: "Uninstalling Windows (problems with partitioning to make Ubuntu as the only OS)"
date: 2008-09-27
forum: General Help
---

### Post by raiXer on 2008-09-27
Alright so I have been using Ubuntu for a few weeks now and I have decided to remove Windows. The problem is that I have Ubuntu installed in a logical partition and I am not sure if I will have problems when I format the Windows partition.

Is there any way to format the windows partition without damaging my Ubuntu install?  Like will I be able to boot to Ubuntu without reinstalling it?


Thanks

---

### Post by raiXer on 2008-09-27
need to know this quick

---

### Post by HotCupOfJava on 2008-09-27
Well - if you have it in dual-boot mode, try loading a Live CD of Ubuntu. Go to System->Administration, then select the "Partition Editor" from the list (you only have this program on a Live CD, it does not install on the HD). Use this program to resize the Ubuntu partition to wipe out Windows and take up the entire disk. The Windows partition should be NTFS or FAT32 (to help you recognize it). 

Hope that helps

---

### Post by HotCupOfJava on 2008-09-27
You may have to do a "Delete" with the partition editor to remove the Windows filesystem, then resize the Ubuntu section for the entire disk. Just load the GParted Partition Editor and see what it lets you do.

---

### Post by raiXer on 2008-09-27
yeah I know how to format the disks. The problem is that Ubuntu is on a logical partition and the Windows partition is the only primary partition in my system so I want to know if it is ok to format the windows partition without destroying the Grub.

---

### Post by HotCupOfJava on 2008-09-27
You safest bet may be to reinstall, then. There may be someone here (with more experience than me) who knows how to do it, but I don't.

---

### Post by raiXer on 2008-09-27
well. wouldn't it be the same if I formatted the windows partition and created a new primary partition and let that one have the boot flag?

Btw.  can I set the boot flag on a logical partition and have it boot normally with grub?

---

### Post by TeXtonyx on 2008-09-27
I would make a Super Grub boot disk or cd just in case. After you delete XP and then 
resize the Ubuntu partition, the only danger is if grub installed in the MBR, disappears.
In that case you can just reinstall grub to the MBR.
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

    sudo grub
> root (hd0,0)
> setup (hd0)
> quit

Often there is a step grub> find /boot/grub/stage1 which tells you where stage1 resides 
which tells you how to fill in the root step above (the from) but probably isn't necessary.
You can reinstall grub if needed, from the live CD, opening a terminal, or Super grub. 
The setup step above (the to) reinstalls grub to the MBR just in case grub is missing.

---

