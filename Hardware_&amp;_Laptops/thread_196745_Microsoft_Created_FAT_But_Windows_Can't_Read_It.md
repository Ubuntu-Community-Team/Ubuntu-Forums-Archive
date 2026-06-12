---
title: "Microsoft Created FAT But Windows Can't Read It"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by rowanparker on 2006-06-14
Hello,
I went out and bought a new 80gig maxtor hard drive, put it in. I created a DOS partition table and made a 76gig FAT32 partition. Linux can read/write fine but I boot up Windows and it says "My Documents Not Found!" blah blah. I go on Disk Management and it says "Unknown Partition".

Microsoft created FAT32 why can't Windows even recognize it?!?

If there is anyway to make Windows work with it, I can back up data and format disk? I could use another filesystem but as long as there are drivers to make it work in Windows.

Thanks, Rowan.

---

### Post by Stone123 on 2006-06-14
76gig FAT32 partition.
isn't 32 gig max Fat32 for windows.

---

### Post by G Morgan on 2006-06-14
Windows struggles with FAT32 partitions bigger than 30GB IIRC. You should be careful declaring that Micros~1 made FAT, they certainly made FAT16 and FAT32 but didn't create the original filesystem.

---

### Post by BoyOfDestiny on 2006-06-14
[QUOTE=G Morgan]Windows struggles with FAT32 partitions bigger than 30GB IIRC. You should be careful declaring that Micros~1 made FAT, they certainly made FAT16 and FAT32 but didn't create the original filesystem.[/QUOTE]

Not to mention the 4 gig file size limit and fragmentation? Why not just make a small partition fat32, to use as a shared "drive" between windows and linux. Make the rest ext3 or something...

---

### Post by rowanparker on 2006-06-15
> 76gig FAT32 partition.
isn't 32 gig max Fat32 for windows.
32gig is the biggest Windows can create, although they can use larger ones.

> Windows struggles with FAT32 partitions bigger than 30GB IIRC. You should be careful declaring that Micros~1 made FAT, they certainly made FAT16 and FAT32 but didn't create the original filesystem.
I used to have a 40gig FAT32 partition which worked fine in Windows and Linux.

> Why not just make a small partition fat32, to use as a shared "drive" between windows and linux. Make the rest ext3 or something...
I need it all to be used in both.


But i suppose i could create 2 FAT32 partitions. Do you think about 50gig is too big?

Thanks, Rowan.

---

### Post by G Morgan on 2006-06-15
What you have to remember with FAT is that it is a source of interoperability. For that reason MS want it to die a slow horrible death on the desktop hence they make things difficult. For things like MP3 players its fine because MS earn a nice payment for each.

---

### Post by beniwtv on 2006-06-15
I have installed my XP on a 50 GB fat32 partition. No problems here. Ok, maybe it's a bad idea to use fat on Windows XP, but I need to read/write with Ubuntu on it...

Oh, but some things remain: I've got a 2GB SD card for my PDA. Since the PDA isn't the newest one, it can only read 1 GB. So, I created 2 FAT partitions, 1 GB each. Windows XP won't recognize the card anymore! I have to use Ubuntu to copy the files over!

---

### Post by frodon on 2006-06-15
I use a 80Go FAT32 partition without any problem, however even if you created a DOS partition table, if your FAT32 partition is a logical partition then what is important to check is the extented partition declaration.

Could you post there the output of the "sudo fdisk -l" command, thus we'll be able to check your partition table

PS: moved to the hardware section.

---

### Post by rowanparker on 2006-06-15
> Could you post there the output of the "sudo fdisk -l" command, thus we'll be able to check your partition table
```
Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9964    80035798+  83  Linux
```
That seems odd. System = Linux, why? I created a DOS partition table. In GParted, it shows up as FAT32?

What should I do?

Thanks, Rowan.

---

### Post by frodon on 2006-06-15
Well if you are sure that Gparted shows the partition as FAT32 it should be a bug and i advice you to create your partition in command line with fdisk.

Warning: it will format the partition and therefore erase all the datas.

Run a : ```
sudo fdisk /dev/hdb1
```

Here is a quick guide to start but just use the help when using fdisk (character "m"), it's not that difficult just use the help :
[http://www.freeos.com/articles/3935/](http://www.freeos.com/articles/3935/)

Once done do a : ```
sudo mkfs.vfat /dev/hdb1
``` to format the new partition as FAT32.

That's all

---

### Post by rowanparker on 2006-06-18
I solved this issue.

I just backed everything on hdb and used to windows to create a FAT32 partiton, then i made it bigger.

Thanks People, Rowan.

---

