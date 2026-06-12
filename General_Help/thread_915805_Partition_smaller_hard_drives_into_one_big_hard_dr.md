---
title: "Partition smaller hard drives into one big hard drive."
date: 2008-09-10
forum: General Help
---

### Post by G-Dub on 2008-09-10
Is there a way to partition smaller hard drives into one big hard drive? I am sick of having a bunch of hard drives.

---

### Post by iaculallad on 2008-09-10
> **G-Dub said:**
> Is there a way to partition smaller hard drives into one big hard drive? I am sick of having a bunch of hard drives.

Meaning, multiple physical hard drives to just one virtual hard drive? Or are you talking of partitions?

---

### Post by stumac on 2008-09-10
Logical volumes should answer your problem. I have used extensively in commercial UNIX systems but never in Linux but they should be about the same.  Google lvm for helpfull links

---

### Post by triphazard on 2008-09-10
You might want to look into a RAID 0 setup or even better (if you have more than 2 physical disks), RAID 5.

I could be mistaken (and it's highly likely) but I think there's a way of achieving similar functionality with symbolic links too.

---

### Post by Bucky Ball on 2008-09-10
Backup your data, run partition editor (gparted - in System->Administration). If you haven't got it, open a terminal and type:

**sudo apt-get install gparted**

Or you can find it in Synaptics. Either option should install it to System->Administration drop down menu as Partition Editor or in the terminal you can open with:

**sudo gparted**

Unmount the partitions you want to delete (right click - unmount) then you can delete the partitions in there and make one big one.

---

### Post by G-Dub on 2008-09-10
> **iaculallad said:**
> Meaning, multiple physical hard drives to just one virtual hard drive? Or are you talking of partitions?
Yes, this is my goal.

> **triphazard said:**
> You might want to look into a RAID 0 setup or even better (if you have more than 2 physical disks), RAID 5.

I could be mistaken (and it's highly likely) but I think there's a way of achieving similar functionality with symbolic links too.

I have 3 Physical hard drives that i want into 1 logical hard drive. Is this the best was to do it? RAID 5...? I have no idea what that is, do you have any tutorials?

> **Bucky Ball said:**
> Backup your data, run partition editor (gparted - in System->Administration). If you haven't got it, open a terminal and type:

**sudo apt-get install gparted**

Or you can find it in Synaptics. Either option should install it to System->Administration drop down menu as Partition Editor or in the terminal you can open with:

**sudo gparted**

Unmount the partitions you want to delete (right click - unmount) then you can delete the partitions in there and make one big one.

This sounds like the best way, any other opinions?

---

### Post by Bucky Ball on 2008-09-10
[QUOTE=G-Dub]I have 3 Physical hard drives that i want into 1 logical hard drive.[/QUOTE]

Hmm. I was assuming you were talking partitions. Not sure if what you want to do is possible.

---

### Post by triphazard on 2008-09-10
> **G-Dub said:**
> Yes, this is my goal.



I have 3 Physical hard drives that i want into 1 logical hard drive. Is this the best was to do it? RAID 5...? I have no idea what that is, do you have any tutorials?



This sounds like the best way, any other opinions?

Sounds like a RAID array is what you'll want then.  Basically, a RAID 0 array will give you the total capacity of all three disks in one 'virtual drive' so if you have have, for example, 3 250GB drives, you could make one 750GB volume.  But if any of the drives fail you'll experience some data loss.

RAID 5 is like RAID 0 but it uses parity to protect you against disk failures.  You'd get the total capacity of all disks available to you minus one disk.  So if you have three disks you'd only get the capacity of 2 disks BUT if any of the disks fails, the data is safe thanks to the use of parity.  In, say, a 7 disk array you'd get the total capacity of 6 disks (7-1) so the more disks, the more efficient/beneficial it becomes.

If you go down the RAID array route you should do some proper research into which of the above solutions would be best for you.

There's a detailed tutorial on setting this up [**[COLOR="Blue"]here[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=408461") too which is worth looking at.

---

### Post by stumac on 2008-09-10
G-Dub
I repeat.  Logical volume is what you need.  Raid is great but only works well if your disk are of identical capacity and realy requires a Raid controller.
Logical volumes allow you to partition disks as you wish then string all the partitions together as one logical partition. It is easy,very flexible and will suit your existing hardware.
 
Have a look at     [http://www.linux.com/feature/142673](http://www.linux.com/feature/142673)

Regards,

Stumac

---

### Post by bingoUV on 2008-09-10
> **G-Dub said:**
> 
" gparted suggestion snipped "
This sounds like the best way, any other opinions?

Except that it does not work. stumac is right. The raid options will either risk your data (raid-0), or give you less storage than the full amount possible from 3 drives (raid-5).

lvm is your best bet. Google lvm.

---

### Post by jerome1232 on 2008-09-10
> **stumac said:**
> G-Dub
I repeat.  Logical volume is what you need.  Raid is great but only works well if your disk are of identical capacity and realy requires a Raid controller.
Logical volumes allow you to partition disks as you wish then string all the partitions together as one logical partition. It is easy,very flexible and will suit your existing hardware.
 
Have a look at     [http://www.linux.com/feature/142673](http://www.linux.com/feature/142673)

Regards,

Stumac

+1 lvm will do it, easiest way (for me at least) is to just reinstall using the alternate cd, it allows you to create a locical volume that spans multiple physical discs.

---

### Post by krsmit0 on 2008-09-10
the downside to lvm...

The current implementation does not support write barriers. This means that the guarantee against filesystem corruption offered by journaled file systems like ext3 and XFS is negated under some circumstances.

---

### Post by Bucky Ball on 2008-09-10
[quote=bingoUV]Quote:
                                                                      Originally Posted by **G-Dub**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5762028#post5762028")                 
                 [I]" gparted suggestion snipped "
This sounds like the best way, any other opinions?[/I]
                                 
Except that it does not work.[/quote]Doesn't work? Not sure I am with you. Doesn't work for what G-Dub wants to do, no, but I assumed (and I guess we never should) they were talking about partitions on a single drive. For that it would work. :)

---

