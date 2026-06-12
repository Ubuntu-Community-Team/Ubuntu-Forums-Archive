---
title: "GPT partition is visible in Windows but not in Ubuntu"
date: 2013-03-06
forum: Hardware
---

### Post by markius on 2013-03-06
I have a PC that I need to dual boot between Windows and Ubuntu 12.04.
When I need to boot into Ubuntu I'm using a live USB stick.

I'm having a lot of difficulty mounting one of my NTFS drives while I'm booted into Ubuntu.

The drive in question is a 3TB SATA disk that's attached to one of the onboard SATA ports on my motherboard (MSI-7411).
It doesn't seem like Ubuntu is able to see the GPT:
```
root@ubuntu:~# gdisk -l /dev/sdc
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sdc: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): A728EE87-A788-40A9-AE2F-A70257884B33
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 5860533101 sectors (2.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
root@ubuntu:~#
```

gdisk under Windows sees the GPT and partitions...
```
C:\Users\Administrator\Downloads\gdisk-windows-0.8.6-2>gdisk
GPT fdisk (gdisk) version 0.8.6.1

Type device filename, or press <Enter> to exit: 1:
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk 1:: 2930266584 sectors, 2.7 TiB
Logical sector size: 1024 bytes
Disk identifier (GUID): F611D7F1-45A5-44F3-AC46-A7CE031D0D04
Partition table holds up to 128 entries
First usable sector is 18, last usable sector is 2930266566
Partitions will be aligned on 8-sector boundaries
Total free space is 1461 sectors (1.4 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              18          131089   128.0 MiB   0C01  Microsoft reserved part
   2          132096      2930266111   2.7 TiB     0700  Basic data partition

Command (? for help):
```
...and the drive mounts without any difficulty.
I've noticed that the reported geometry is different under Windows.

Here's some other information that might be useful:
dmesg: [http://paste.ubuntu.com/5591501/](http://paste.ubuntu.com/5591501/)
line 810 is interesting [    2.897166]  sdc: unknown partition table

lspci: [http://paste.ubuntu.com/5591997/](http://paste.ubuntu.com/5591997/)
The ATI southbridge is in fakeRAID mode, with /dev/sda1 and /dev/sda2 being mirrored.  This appears to be picked up correctly by dmraid.
The 3TB drive is configured as "single disk" in the RAID option ROM. I did try switcing to AHCI mode but it didn't solve the problem.

parted -l: [http://paste.ubuntu.com/5592000/](http://paste.ubuntu.com/5592000/)
line 20 is interesting Error: /dev/sdc: unrecognised disk label



Can anyone offer any advice as to what I should do to get this drive working under Ubuntu?

Cheers

---

### Post by markius on 2013-03-08
Would I be better of posting this in the beginners forum?

---

### Post by markius on 2013-03-09
I've taken everything off the drive and created a new GPT from inside Ubuntu.  I then created a single NTFS partition and put some data on it.
Rebooted into Windows and... "Uninitialized disk", no GPT and no data. :confused:

Anybody?  Surely I haven't discovered some new and unsolvable problem?

---

### Post by oldfred on 2013-03-09
I have seen issues with Windows gpt and disk utility created gpt drives. Most created with with gdisk or gparted seem to be ok.

But I find it strange that Linux gdisk sees 512 sector and Windows sees 1024? I thought most new drives were 4K?
       [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)

I do see a minor version difference in gdisk. I would make sure I have the newest version in both systems from rodbooks site.
       GPT fdisk Tutorial 
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

---

### Post by markius on 2013-03-09
Hi oldfred

Thanks for taking the time to respond.

The linux kernel seems to be aware that the underlying hardware is using 4096-byte physical blocks:
```
root@ubuntu:~# dmesg | grep sdc
[    6.089624] sd 3:0:0:0: >[sdc] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    6.089780] sd 3:0:0:0: >[sdc] 4096-byte physical blocks
[    6.089937] sd 3:0:0:0: >[sdc] Write Protect is off
[    6.090006] sd 3:0:0:0: >[sdc] Mode Sense: 00 3a 00 00
[    6.090040] sd 3:0:0:0: >[sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.098531]  sdc: unknown partition table
[    6.098795] sd 3:0:0:0: >[sdc] Attached SCSI disk

```

After doing a little bit of research, it's clear that the problem is the disagreement of the LBA size between Windows and linux.

[This Wikipedia article]("http://en.wikipedia.org/wiki/GUID_Partition_Table") says that the MBR partition table is stored at LBA0 with the GPT stored at LBA1.

Because the LBA size in Windows is 1024 bytes, linux doesn't see the "Windows" GPT at LBA1, instead finding it 512-bytes later at at LBA2...

```
root@ubuntu:~# dd if=/dev/sdc skip=2 bs=512 count=1 2>/dev/null | od -x
0000000 4645 2049 4150 5452 0000 0001 005c 0000
0000020 9ded 437f 0000 0000 0001 0000 0000 0000
0000040 51d7 aea8 0000 0000 0012 0000 0000 0000
0000060 51c6 aea8 0000 0000 e25d d5ad 83e2 43be
0000100 b882 98af 55af 9586 0002 0000 0000 0000
0000120 0080 0000 0080 0000 a02d 0b0e 0000 0000
0000140 0000 0000 0000 0000 0000 0000 0000 0000
*
0001000

```
(4645 2049 4150 5452 is big-endian for "EFI PART", the signature string of a GPT)

Conversely, if I write my GPT using linux, Windows doesn't see it at LBA1 either, because from the Windows perspective the "linux" GPT is at LBA0.5 :/

At this point I think I can discount gdisk as being the cause of the problem as this error being introduced at a lower level of the OS.

I think the key questions are...
What is the correct LBA size for my 3TB disk?
Why is linux reporting a different LBA size to Windows?
How do I fix the broken system?

---

### Post by oldfred on 2013-03-09
While I use gpt on several smaller drives, I do not have any large TB drives. So I do not know much to help.

But I am curious on how you formatted originally. Was it Windows, Windows 3rd party tools, or did drive have gpt from vendor?

I have seen 512/512 or 512/4K logical/physical drives but not any with your 1K blocks.

It used to be in BIOS we set CHS and then with larger drives over 8GB it changed to LBA which was always 512. So is there some sort of UEFI/BIOS setting?

Another link with some technical details.
[http://thestarman.pcministry.com/asm/mbr/GPT.htm](http://thestarman.pcministry.com/asm/mbr/GPT.htm)

Do you have RAID setting on in Windows?
[http://www.rodsbooks.com/gdisk/advice.html](http://www.rodsbooks.com/gdisk/advice.html)

---

### Post by markius on 2013-03-09
The disk was originally partitioned and formatted in Windows so the GPT was at an offset of 1024 bytes which worked for Windows but was no good for linux.
In the course of my troubleshooting I ended up flattening the drive and recreating the GPT using gdisk in linux which put the GPT at an offset of 512 bytes - great for linux, no good for Windows.


After a bit more investigation I discovered that I'm not the first person to experience this problem.  There is [a thread from 2011]("http://ubuntuforums.org/showthread.php?t=1768724") where someone is having a similar problem.  That thread refers to a RAID set on an AMD chipset and although I'm only using a single disk, it is attached to an AMD chipset that's running in RAID mode.

It appears that either AMD's AHCI RAID drivers for Windows or the AMD chipset itself don't properly report the logical sector size to Windows.  Despite the fact that the AMD RAIDXpert tool clearly says "512-byte sectors" Windows is being told to use 1024-byte sectors.

So to answer my own questions....
What is the correct logical sector size?  512 bytes.  Or [4096 bytes ]("http://msdn.microsoft.com/en-gb/library/windows/desktop/hh182553(v=vs.85).aspx").  Definitely not 1024 bytes!
Why is linux reporting a different LBA size to Windows?  Either because linux is hard coded to use 512 bytes or because it isn't burdened with duff AMD drivers.
How do I fix the broken system? Technically it's neither Windows or linux that's broken.  Whichever way you look at it this is a problem that AMD should address either in their hardware/firmware or in their Windows drivers.


For me the workaround has been to take the motherboard out of AHCI RAID mode and revert to plain AHCI.  For whatever reason AHCI mode reports 512-byte sectors to Windows and I'm able to create a GPT that can be read by both Windows and Ubuntu.
I was running in AHCI RAID mode because I also have 2 1TB disks that form a RAID1 mirror and I've been forced to switch to Windows dynamic mirroring for these.  My next challenge is to get linux dmraid to see and mount that RAID set - CAN.OF.WORMS!


Thanks for your help.  Confirming that the geometry mismatch was unusual put me on the right track to understanding the issue and coming up with the workaround.  It's been an educational afternoon!

Cheers

---

### Post by oldfred on 2013-03-09
Thanks for the update. 

Do not know much about RAID as I do not use it for desktops. And there are different kinds of RAID which I barely know the difference or  hardware, "fakeraid", and Linux' own version.

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

---

