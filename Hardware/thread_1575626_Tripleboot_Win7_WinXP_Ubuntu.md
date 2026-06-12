---
title: "Tripleboot Win7 WinXP Ubuntu"
date: 2010-09-16
forum: Hardware
---

### Post by PunkLV on 2010-09-16
Greetings,
so Im trying to set up trippleboot system on my HP G72 120-ew. OEM Win7 + WinXP + ubuntu. Exactly in that order. 

The Problem:
After creating a new partition in Win7 Disk Manager, the only software which can see this partition is Win7 itself. Works fine. Tried not to assign a drive letter, not to format, formatting to ntfs, fat32. 
In winxp installer the new partition is not listed, in ubuntu livecd gParted as well. So, basically, new partition 'does not exist' to anything other then Win7.

Have tried dozens of guides, tips and tricks, and so on. Curently Im thinking of resizing the Win7 partition using gParted and hope that Win7 will survive the move.

Any help would be greatly appriciated.

---

### Post by sikander3786 on 2010-09-16
Are you sure you have created a partition in that space? Might be it is being listed in unallocated space both under XP and Ubuntu?

---

### Post by PunkLV on 2010-09-16
I am tired and sleepy, but not that much. Patrition is fine and well, operates just as any other partition. But only under win7. I really dont know even where to start digging.

---

### Post by sikander3786 on 2010-09-16
> **PunkLV said:**
> I am tired and sleepy, but not that much. 

Never mind. I actually don't know how much computer skill you've got so I asked that question.

Can you please run Ubuntu from a live cd and post the output of the following command.

```

sudo fdisk -l

```

That will help us determine the partition setup of your drive.

---

### Post by PunkLV on 2010-09-16
In a moment. But befo that: could it be becaouse of the dynamic\basic disk types?

Oh, and the new partitions space somehow automatically adds to the the Recovery partition. Which is HP's built-in partition I guess. And it cannot be deleted. Great.

---

### Post by PunkLV on 2010-09-16
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22feface

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204768+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          26       57876   464679936   42  SFS
/dev/sda3           57876       60802    23500824   42  SFS

```

Well this is exactly what gParted and winxp show. Im at loss.

UDT: Either a miracle is going to happen, or a total disaster. By removing the Recovery partition winxp was able to see it as an unallocated space. Winxp installing.

---

### Post by sikander3786 on 2010-09-16
The SFS label under System says that you've got a Windows Dynamic Disk. I have never experienced that myself but did a bit of Googling and found that you might need to convert it to basic disks before you can proceed with installation. The following link might help. Also wait for some other wise replies that might help you too.

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

[COLOR="Red"]**EDIT:**[/COLOR] Good luck for the installation. Now if you've deleted the recovery partition, I think you should backup your data and manually partition the HDD according to your needs. And then installation should go on pretty fine. Hope for the good.

---

### Post by PunkLV on 2010-09-16
Yea, googled a bit. To convert I will need to remove all partitions. So this is not an option for me. 

Thanks for your help and time this far.

Well. Yeah. I fail. Removing the partion caused the rest to fall apart. Maybe there is a way to fix this though. Without doing a clean win7 install

---

### Post by sikander3786 on 2010-09-16
> **PunkLV said:**
> Yea, googled a bit. To convert I will need to remove all partitions. So this is not an option for me. 

Thanks for your help and time this far.
You're Welcome :-)

---

### Post by PunkLV on 2010-09-16
So now ubuntu sees the partition with win7 install, however nor win7 nor xp do not see it. Partition table mixed up bad.

---

### Post by sikander3786 on 2010-09-16
> **PunkLV said:**
> So now ubuntu sees the partition with win7 install, however nor win7 nor xp do not see it. Partition table mixed up bad.
Thats why I suggested manual partitioning. So now you cannot boot Windows 7? Is XP booting fine?

---

### Post by PunkLV on 2010-09-16
Yeah. XP runs OK, on a 10GP partition c:\. But does not see the rest of the 490GB available. People suggest SystemResqueCD. Thats what Im going to try now. Unless you know a way to fix the table from Win7 install cmd.

---

### Post by sikander3786 on 2010-09-16
If you've got Windows 7 disk and have no valuable or non-backed up data on the partition, I suggest that reinstalling Windows 7 will fix most of the problems. If this is not the case, you can try the System Rescue Disk. Not sure if it will help either.

---

### Post by PunkLV on 2010-09-16
I dont have an OEM recovery disk, cheapskates at HP do not provide those. And I do not want to mess around with with a downloaded one. Yet this option is my last resort.

UPDATE
Restored the partittion table. New winxp sees everything. Now I have to restore win7. The fun never ends.

UPDATE
Rstored Win7. Everything boots fine and seems cool, despite the thrilling search for the suitable drivers for XP. Doubt they exist anyway.

---

### Post by sikander3786 on 2010-09-16
Glad to see it was all good at the end. You didn't tell if Ubuntu was installed...? Hope to see you soon at UF.

---

