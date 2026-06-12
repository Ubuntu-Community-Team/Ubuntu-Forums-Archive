---
title: "Gparted message &quot;The primary GPT table is corrupt&quot; with new 8tb drive installed"
date: 2017-11-10
forum: Hardware
---

### Post by neptune39 on 2017-11-10
Hi

So hardware is HP Microserver n40l (so a little dated). Wanted to add another drive so bought a Seagate ironwolf 8tb and used gparted to partition as GPT and EXT4. Drive works as expected and I can add files without issue. However when I go into gparted now and it scans the drives I get an error saying The primary GPT table is corrupt, but the backup appears OK, so that will be used."

Is this something I should be worried about? Seems like it is. How do I confirm this is related to this specific drive? Have I set this up wrong, this is a new drive and newly formatted so I wouldn't expect this to happen straight away. 

I'm running Ubuntu 16.04.3 LTS xubuntu variant.

Any help much appreciated!

---

### Post by oldfred on 2017-11-10
See what this says:
 sudo gdisk -l /dev/sda 

And you can use gdisk to fix primary partition table based on backup if that is correct.
      
 repair gpt:
[URL="http://www.rodsbooks.com/gdisk/repairing.html"]http://www.rodsbooks.com/gdisk/repairing.html
[/URL]
 sudo gdisk /dev/sda
Command (? for help): 

 Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. T
hat should update primary, backup & protective MBR. 




[URL="http://www.rodsbooks.com/gdisk/repairing.html"]
[/URL]

---

### Post by neptune39 on 2017-11-10
My output

GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 15628053168 sectors, 7.3 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 859759BC-52D6-4037-A37F-613697D05B41
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 15628053134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048     15628052479   7.3 TiB     8300

---

### Post by neptune39 on 2017-11-10
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sda: 15628053168 sectors, 7.3 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 859759BC-52D6-4037-A37F-613697D05B41
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 15628053134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048     15628052479   7.3 TiB     8300  

Command (? for help): v

No problems found. 2669 free sectors (1.3 MiB) available in 2
segments, the largest of which is 2014 (1007.0 KiB) in size.

---

### Post by neptune39 on 2017-11-10
Sorry to keep chucking stuff up but this is the output for /dev/sdc so I think I'm looking at the wrong drive and its this one thats the issue. This is part of a RAID 1 array and from memory was created using mdadm.

GPT fdisk (gdisk) version 1.0.1

Caution! After loading partitions, the CRC doesn't check out!
Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Disk /dev/sdc: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): E6B00A1B-2EBC-481F-AE0E-A0F8EA9148F8
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2157 sectors (1.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      3907028991   1.8 TiB     8300

---

### Post by oldfred on 2017-11-11
The largest drive you can have is 2 TiB, so your 2 TB drive can be MBR(msdos) or gpt(GUID).
But highly recommended not to be both or hybrid. The hybrid configuration was used by older Mac to boot Mac in UEFI/gpt and older Windows in BIOS/MBR on same drive.

 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html) 

But I do not know RAID, nor what difference that may have.
I have seen where sometimes tools see drive incorrectly as RAID or LVM may be across two drives but then tool sees end of (actual)drive in middle of total space.
Only use RAID tools on RAID & LVM tools on LVM.
Parted or gparted do not work on RAID as far as I know.

---

### Post by Yellow Pasque on 2017-11-12
Before doing anything, make a backup of the array if you don't have one (Hopefully, you didn't use all 8TB of that new disk yet).

[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
The quickest way would be to use gdisk to verify (option 'v) the disk to see what it recommends. If it only recommends rebuilding the main GPT using the backup (option 'c'), then that would give me a better feeling about the integrity of the data as opposed to verify finding multiple issues.

The brute force approach:
1. Back up the data on the RAID to the new 8TB disk.
2. Using mdadm, mark the disk in question faulty and remove it from the array.
3. Run smarctl on the disk to verify it's okay physically.
4. Format the disk (recreate the GPT and partitons).
5. Add it back to the array.

---

### Post by neptune39 on 2017-11-14
Ok in the process of recreating the array. Thanks for all the assistance provided and pointing me in the right direction.

Just for completeness I've ended up backing up to another drive and starting from scratch with the RAID which I am going to then test before using again.

---

### Post by Yellow Pasque on 2017-11-14
You're more than welcome. This thread has alerted me to an issue with my own RAID(1) mirror. This is why I keep helping in ubuntuforums.

---

