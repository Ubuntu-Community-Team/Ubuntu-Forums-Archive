---
title: "[SOLVED] Resizing partitions"
date: 2008-11-04
forum: General Help
---

### Post by pjalegria on 2008-11-04
Hi 

I try to decrease my swap partition and use the unallocated space to primary ext2 partition but i cant do it...

Decrease swap its easy but when a try to use the the unallocated space to increase primary ext2 i cant do it, the only option is to create a new partition with the unallocated space... can someone help me?

---

### Post by taurus on 2008-11-04
Did you remember to unmount that ext2 partition first before you wanted to expend it?  The best way to resize partitions is with gparted from the LiveCD.

---

### Post by drs305 on 2008-11-04
Is the swap also in a primary partition or is it located in a logical partition? It might help if you post a pic.

---

### Post by pjalegria on 2008-11-04
Yes i use Ubuntu live cd and i only have ext2 primary partition and swap

---

### Post by drs305 on 2008-11-04
From gparted in the live cd. Tell us at what point you get an error or which step you can't complete.

1. Select the existing partition - it should be highlighted. 
2. Click on the menu's 'Partition'. See if 'Umount' is greyed out. If it isn't, unmount the partition.
3. Partition, Resize. Increase the value in 'New Size', then click on Free Space Preceeding or Free Space Following to set, then Resize/Move to activate.
4. Click Apply.

---

### Post by pjalegria on 2008-11-04
I cant increase ext2 partition, i have unallocated space but ext2 dont let me increase...

---

### Post by taurus on 2008-11-04
Can you post a screenshot of gparted with your partitions table?

You can take a screenshot from Applications -> Accessories -> Take Screenshot.

---

### Post by louieb on 2008-11-04
Only know of two reasons you can't grow the partition.
More than likely your unallocated space is inside an extended partition. In that case you will need to shrink the extended partition too.

Or it is not right next to the partition you want to enlarge. In order to add space to a partition the unused space must be next to the partition you are trying to grow.

if you have more questions please post the partition table  by coping the output of ```
sudo fdisk -l
``` lowercase L at the end
Another way to take a screen-shot of the active window is to press Alt+PrtScr

[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by pjalegria on 2008-11-05
Were it is my partitions...

[[IMG]http://img231.imageshack.us/img231/3158/capturaecradevsdagparteqw5.png[/IMG]](http://imageshack.us)

I want to deacrese swap to 512mb and increase ext2...

---

### Post by shortcut144 on 2008-11-05
If you are not already, go use gparted.

apt-get install gparted

Shows up and Partition Editor in your menus.

---

### Post by pjalegria on 2008-11-08
Cant someone help me please....

---

### Post by louieb on 2008-11-08
Your screen shot shows both partitions locked. 
You need to use a live CD such as a Ubuntu live CD or the   [SystemRescueCd.]("http://www.sysresccd.org/Main_Page")

Your screen shot also shows you don't have any unallocated space. You need to shrink the swap partition 1st.

taurus and drs305 pretty much described what you need to do.

A couple of good links for using Gparted.
 [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")
[Linux.com :: Dual-booting Windows and Linux the easy way (Linux.com videos)]("http://www.linux.com/feature/114157")  Don't worry about the title these videos show how to use the Gparted partition editor.

---

### Post by pjalegria on 2008-11-08
yes, but already have done that... after i shrink the swap i have the unallocated space but when i try to increase the ext2 partition, I CANT...:confused:

---

### Post by louieb on 2008-11-08
Did you shrink swap from the left? The unallocated space needs to be in between the two partitions.

---

### Post by pjalegria on 2008-11-08
yes, and then...

---

### Post by louieb on 2008-11-08
then what?

---

### Post by pjalegria on 2008-11-08
Solved...:lolflag: is the "LEFT SIDE", i was shrink swap from the right side... Thanks guys

---

