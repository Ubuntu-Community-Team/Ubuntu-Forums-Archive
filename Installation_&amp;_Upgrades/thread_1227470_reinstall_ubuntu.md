---
title: "reinstall ubuntu"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by rvt20s on 2009-07-30
Im planning on deleting my unbuntu partion which is only 4 Gb then Im going to install the latest ubuntu upgrade. If I do this will my GRUB be messed up or will it be fine once I reinstall ubuntu with a bigger partion? I have a windows NTFS partion which i want to keep also.
thanks

---

### Post by stlsaint on 2009-07-30
well if you delete ubuntu partition you will have a fresh kernel for your grub.

---

### Post by rvt20s on 2009-07-30
sorry, does that mean my ubuntu kernals will be removed from the list ? and the vista longhorn will remain in the list. 
sorry for the newbie quesions :rolleyes:

---

### Post by merlinus on 2009-07-30
How do you plan to create a larger partition for ubuntu?  If you will be shrinking vista, then be sure to delete temp files, defrag several times, and use its disk management tool.

Grub will be part of the new ubuntu install.

---

### Post by rvt20s on 2009-07-30
> **merlinus said:**
> How do you plan to create a larger partition for ubuntu?  If you will be shrinking vista, then be sure to delete temp files, defrag several times, and use its disk management tool.

Grub will be part of the new ubuntu install.


when I first installed ubuntu with the live cd I selected the Dual-booting option then allocated how much space for the partion with a slider bar, so yes vista will be shrinking.

what I would like to know is what happens when I delete my unbuntu partion and just reinstall with my unbuntu CD. can I do that and just select a big partion for ubuntu ?

Or can I just shrink my vista partion and increase the ubuntu one with one program like partion magic or something?

---

### Post by merlinus on 2009-07-30
You run risk of hosing vista if you do not use its disk managment tool to shrink that partition.

---

### Post by rvt20s on 2009-07-30
> **merlinus said:**
> You run risk of hosing vista if you do not use its disk managment tool to shrink that partition.

I think I shall do that first with the disk manager...then I will have unallocted space on my harddisc right?

Then can I go into ubuntu and increase the partion ?

thanks for all the help btw.

---

### Post by merlinus on 2009-07-30
If you are reinstalling, then why not shrink vista and set up new partitions during the installation?  But remember that no matter which way you do it, back up important data,   unless you have a separate /home partition.

But it you do not wish to reinstall, then you can use gparted, either on the live cd or on its own live cd, to grow your linux partition into the freed-up space.

If linux is an extended partition, however, it will require more steps.

---

