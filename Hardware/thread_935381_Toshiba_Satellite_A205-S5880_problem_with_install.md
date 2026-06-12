---
title: "Toshiba Satellite A205-S5880 problem with install"
date: 2008-10-01
forum: Hardware
---

### Post by JimGvo on 2008-10-01
This is probably more for reference than anything.  I recently purchased one of these beasts and had anticipated dual booting it Linux/Vista.  Not going to happen.  Partition Magic doesn't recognize the partition table, gpartd, the latest cdrom doesn't recognize the partition table and Ubuntu doesn't think there is a partition table.  Fdisk -l shows a vaild partition table however.  

I don't have a clue as how to resize the NTFS file system on partition 2 of this system.  

So anyone looking at this for a Linux dual boot system, might want to skip it.  I unfortunately have to have a Windows OS on this system so it'll remain a Windows system only I fear.  I can't wipe it and put Linux on it.  I'm sure not going to give M$ bucks for a full version of XP either, even if there are drivers for it, which from what I've read on the net is a real possibility.

Later,
Jim.

---

### Post by empty_spaces on 2008-10-01
What are your specs? 
I recently bought a Satellite A205 S5855, and everything works OOTB with Hardy. I was even able to use my Ubuntu live CD to move Vista to one side of the HDD and create 3 more partitions, one of which I use for Hardy. 
Here is my thread,
[http://ubuntuforums.org/showthread.php?t=859422](http://ubuntuforums.org/showthread.php?t=859422)

---

### Post by JimGvo on 2008-10-02
> **empty_spaces said:**
> What are your specs? 
I recently bought a Satellite A205 S5855, and everything works OOTB with Hardy. I was even able to use my Ubuntu live CD to move Vista to one side of the HDD and create 3 more partitions, one of which I use for Hardy. 
Here is my thread,
[http://ubuntuforums.org/showthread.php?t=859422](http://ubuntuforums.org/showthread.php?t=859422)
Specs?  It's a 3 Gb mem, 200 Gb HD, Intel dual core processor, 1.8 Mhz.  

I booted the Hardy live cd and wasn't able to do squat with the partitions.  The only utility that could even read the partition table was fdisk.  What utility did you use to resize the drive?  

I did the first steps of an install, hoping that the partition manager would let me do something, but it didn't know what to do with the drive other than create a new partition table.  Gparted got an error #105 trying to read the partition table.

Thanks,
Jim.

---

### Post by empty_spaces on 2008-10-02
If I remember correctly, I first used the guided install on the Ubuntu LiveCD to move Vista to one side with a partition of 50GB, and used the remaining 100GB to install Ubuntu Hardy + 4GB Swap. I did not touch the Vista Recovery partition.
Then I used the Gparted CD to further split the 100GB Ubuntu partition into 3 parts of 40GB + 30GB + 30GB, keeping the Ubuntu install on the 40GB partition.

---

### Post by ahmadaktaa on 2008-11-24
thanx

---

