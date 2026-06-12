---
title: "Unusual problem - Windows Xp clashing with Ubuntu"
date: 2008-11-04
forum: General Help
---

### Post by akshar_patel_47 on 2008-11-04
I've been using ubuntu and windows xp dual boot since 7.10 was released. 

My windows crashed recently and I had to reinstall it. During the Windows xp installation during the drive selection screen, no matter whichever drive I select, windows installer told me that the file system of that drive was not windows xp compatible (Even though every drive was NTFS) and that I would have to select another drive. Even though I would delete a partition and make that partition again.. it would give me the same error. I tried formatting the partition to NTFS using Ubuntu Live CD as well. (*,)](*,)](*,)

Also during the recent installation of Ubuntu 8.10, I found that each and every partitions of my hard disk were of a file system name fusion ( or something related to it). Is that why windows xp does not let me install itself?? :confused::confused::confused:

Actually, I would have been more than happy to be relieved of windows but my college assignments and projects are to be done unfortunately in windows so I need it on an as and when needed basis. 

So, my question is this... Is there a way to completely change the partition's file system to NTFS or any other way the windows would let me install it?

I have two hard disks one of 80 GB ( Having Ubuntu on which I boot ) and other 250 GB ( Which used to have Windows till recently :lolflag: ) with 6 partitions.

---

### Post by Peter09 on 2008-11-04
Have you thought about running windows as a virtual machine in Ubuntu - its an easy and neat solution and does away with all the partitioning problems?

---

### Post by akshar_patel_47 on 2008-11-04
Yup.. I already have it running as a virtual machine using virtual box. But it has issues like it doesn't recognize my motherboard and graphic card as well. So can't do anything in it.

---

### Post by Peter09 on 2008-11-04
VirtualBox does not show the virtual machine your real graphics card and motherboard. So yes if you need 3d graphics it will not work. If you just need simple apps it will.

---

### Post by akshar_patel_47 on 2008-11-04
Not only that, it glitches too much as I can't install my graphic card drivers. And too slow.

So any way of formatting the drives to NTFS completely using Ubuntu facilities or some other way???

---

### Post by Vl@d on 2008-11-04
> windows installer told me that the file system of that drive was not windows xp compatible (Even though every drive was NTFS) and that I would have to select another drive. Even though I would delete a partition and make that partition again.. it would give me the same error.

SATA drives?  Try to set the AHCI to Compatibility on the BIOS (Another option would be load the correct SATA drivers into a floppy) .

---

### Post by akshar_patel_47 on 2008-11-04
Thanks for the reply Vl@d. I'll try it out. But the thing is why now... I've done ubuntu and windows dual boot installation some 10 times and nothing has happened. This time I don't know what's up with windows...

---

### Post by logos34 on 2008-11-04
> **Vl@d said:**
> SATA drives?  Try to set the AHCI to Compatibility on the BIOS

Either that or the fact that ubuntu on the other (80 GB) disk is the boot drive...Try switching the Bios hard disk boot priority so the 250 GB is first, then try to install XP.

---

### Post by akshar_patel_47 on 2008-11-04
Yes ubuntu's 80 GB is the boot drive. But by changing hard disk priority and installing windows will I have to change my GRUB settings?

---

### Post by logos34 on 2008-11-04
> **akshar_patel_47 said:**
> Yes ubuntu's 80 GB is the boot drive. But by changing hard disk priority and installing windows will I have to change my GRUB settings?

Not necessary.  After installing windows (assuming it lets you) just set it back like it was and continue booting from the other drive.  [Add a XP entry to grub menu.lst like this.]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")

---

### Post by akshar_patel_47 on 2008-11-04
> **logos34 said:**
> Not necessary.  After installing windows (assuming it lets you) just set it back like it was and continue booting from the other drive.  [Add a XP entry to grub menu.lst like this.]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")

Thanks for the links... I'll try to install windows the way to told me and get back to you asap.

---

### Post by akshar_patel_47 on 2008-11-04
Still having the same problem guys...help me out. 

I tried making my windows drive as the main boot drive and there's nothing like AHCI compatibility in my BIOS ( I checked each and every option ).

](*,)](*,)](*,)](*,)](*,)

Windows says it can't recognize the partition and when I delete the partition and make a new one... it says it's not a windows xp compatible partition.

Maybe my boot sector is messed up????

---

### Post by logos34 on 2008-11-05
you say there's 6 partitions on the 250 gb drive...make sure you're trying to install XP on a PRIMARY partition, rather than a logical partition inside the extended partition.

Other than that not sure what the problem could be.  You might want to post the output of

sudo fdisk -l

---

### Post by akshar_patel_47 on 2008-11-05
Here is the output

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22052204

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9faf9fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6080    48837568+  83  Linux
/dev/sdb2            6081       30401   195358432+   f  W95 Ext'd (LBA)
/dev/sdb5            6081       12160    48837568+   7  HPFS/NTFS
/dev/sdb6           12161       15200    24418768+   e  W95 FAT16 (LBA)
/dev/sdb7           15201       21280    48837568+   7  HPFS/NTFS
/dev/sdb8           21281       27359    48829536    7  HPFS/NTFS
/dev/sdb9           27360       30401    24434833+   7  HPFS/NTFS

```

---

### Post by alwayshere on 2008-11-05
I went through all that when i use windows all i did was had a hard drive for each and always turn the one i was not using off in bois .
may seem  extreme but if you get sick of reinstalling windows try it it works .

OR you could just install ubuntu then use virtualbox to install windows in virtualbox .i tried it on my macbook and it worked ok but i didnt put it through it paces ,heres the sight [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

OR you could use your windows cd for a coaster lol


Good luck

---

### Post by caljohnsmith on 2008-11-05
Akshar_patel_47, I think you should follow Logos34's advice; the only NTFS partitions you have on your sdb drive are all logical partitions, and you should install Windows to a primary partition. If I were you, I would repartition your sdb drive to have a primary NTFS partition to install Windows to. You can only install Windows to a logical partition if there is a primary NTFS/FAT32 partition available where Windows can put its boot files. But if you just simply create a large primary NTFS partition for Windows, I think you will have no problem installing Windows; that's what I would do if I were in your shoes.

---

### Post by akshar_patel_47 on 2008-11-05
Thanks logos34, caljohnsmith and alwayshere... I'll try each and everything you've said and get back with the results.

---

### Post by KeyserSoze93 on 2008-11-05
When you say "fusion", do you mean "fuse", because if it is an ntfs drive, it will be mounted with ntfs-3g, which uses the fuse (userspace filesystem support) infrastructure, so it's still ntfs...

---

### Post by sdowney717 on 2008-11-05
you could always simply brute force this issue by

backing up your home files in ubuntu

install XP by wiping the drive clean, start over
reinstall ubuntu
restore home directory.

---

