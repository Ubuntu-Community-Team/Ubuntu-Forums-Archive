---
title: "3TB disk appears as two separate devices"
date: 2013-08-16
forum: Hardware
---

### Post by halfbeing on 2013-08-16
I have just bought a 3TB Seagate hard drive which I have put in a USB enclosure. The problem is that Linux can only see it as two drives rather than one. There is a 2TB /dev/sdb and a 747GB /dev/sdc. Windows 7 can see the drive as a single device, but only with the help of Seagate's Disk Wizard software. I have formatted both of the "virtual" drives with GPT. I am using Linux installed on two machines, a Thinkpad R61i and a Dell Optiplex 330, both with up to date BIOS, to access the disk. Is there any way I can get Linux to see the disk in its entirety so I can install a single partition across it?

---

### Post by oldfred on 2013-08-16
Install gdisk and post this:
sudo apt-get install gdisk

       sudo gdisk -l /dev/sda


 sudo parted /dev/sda unit s print

Sometimes it is the external enclosure that is really the problem.


 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by halfbeing on 2013-08-17
Thanks for replying!

Here are the outputs of the two commands you asked for, applied to both of the disks (/dev/hdb and /dev/hdc) that Linux sees for my one physical disk. As you can see I created a GPT for each as well as an ext4 volume to check that I did at least have a working disk of some sort. But I worry whether I can rely on another machine being able to read those partitions, for instance if I put the disk in another case. In any case what I really need is still to have a single volume stretching over the entire disk.

robert@ermintrude:~$ sudo gdisk -l /dev/sdb
[sudo] password for robert: 
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 4294967295 sectors, 2.0 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 37F6ACE2-1AC4-44DF-B291-07D382B2A094
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 4294967261
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      4294967261   2.0 TiB     0700  Linux filesystem
robert@ermintrude:~$ sudo parted /dev/sdb unit s print
Model: ST3000DM 001-1CH166 (scsi)
Disk /dev/sdb: 4294967295s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End          Size         File system  Name              Flags
 1      2048s  4294967261s  4294965214s  ext4         Linux filesystem

robert@ermintrude:~$ sudo gdisk -l /dev/sdc
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdc: 1565565872 sectors, 746.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): EF69A6E0-0209-444C-9513-769B58DE6B0A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1565565838
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      1565565838   746.5 GiB   0700  Linux filesystem
robert@ermintrude:~$ sudo parted /dev/sdc unit s print
Model: ST3000DM 001-1CH166 LUN1 (scsi)
Disk /dev/sdc: 1565565872s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End          Size         File system  Name              Flags
 1      2048s  1565565838s  1565563791s  ext4         Linux filesystem

---

### Post by oldfred on 2013-08-17
I thought it might show something, but does not really.

But I thought new drives were 4K drives and would show as 512/4K, so did vendor reconfigure drive to make it be two drives? Or it may be the 
       [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)
Alignment 2048 sectors Advanced Format drives
[http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted](http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted)

A few others with similar issues have found the USB hard drive caddy had a 2TB limit or really only worked with MBR drives.

---

### Post by halfbeing on 2013-08-17
You're being very helpful! I tested the crippled enclosure hypothesis by plugging the drive in where the internal DVD drive normally goes and gparted recognised the disk for its proper size, created a correct GPT and a 2.7TB ext4 volume. I put the disk back in the enclosure and plugged it in and gparted threw up errors again. Is it safe to say that the enclosure definitely is the culprit? If so, do you think that when I buy a replacement I will need to restrict myself strictly to enclosures for which the blurb explicitly claims Linux compatibility?

[This]("http://www.pixmania.be/be/fr/12989678/art/maxinpower/boitier-externe-de-stocka.html") is the enclosure that I bought, if it makes any difference. I wonder if there was a big red flag that I didn't notice when I was shopping?

Anyway, thanks once again!

---

### Post by oldfred on 2013-08-17
High school French from fifty years ago is not helping me read ad. :)

Not sure what the exact issue is or why some do not work correctly.

---

### Post by halfbeing on 2013-08-18
Sorry! I really just meant a big red flag in terms of something like "brand I've never heard of" or it not saying "Linux" in the right-hand column of the specifications :)

Anyway, I've printed the retailer's return voucher, but it looks like I'd have to pay almost as much in postage as I would get as refund, so this one goes down to experience!

Thanks once again for your help!

(I'll leave this thread not marked solved until I've got a replacement enclosure and seen it working properly.)

---

### Post by halfbeing on 2013-08-22
This is just to confirm that the problem was the disk enclosure. If you are shopping for a disk enclosure for a large disk you need to google the word "capacity" to confirm that the one you are thinking of buying is up to the job.

---

### Post by oldfred on 2013-08-22
Thanks for update.

---

