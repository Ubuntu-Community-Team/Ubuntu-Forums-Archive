---
title: "triple booting ubuntu, help required"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by jonndoe45 on 2009-04-30
I have two HD's.

The second (hd1) is set as the boot disk.

xp was loaded first, partition 0, active
win7 was loaded next, partion 1

now when i create a partition for ubuntu and a swap partition all ok

but where do I put the boot loader ? HD1 ?

help please, I am lost

---

### Post by Mark Phelps on 2009-04-30
Since Vista and Seven are so touchy (meaning, easily broken), would recommend you install GRUB to the MBR of the Ubuntu drive.  

You will then have to create a stanza in the menu.lst file for MS Windows, 
but that's pretty easy to do.

Once you get into Ubuntu, open a terminal window and enter "sudo fdisk -lu" (that's a lowercase L, not a one) and post the results here.  That will list your partitions and is needed to figure out the details of the MS Windows boot stanza needed.

---

