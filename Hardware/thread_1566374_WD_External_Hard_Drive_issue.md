---
title: "WD External Hard Drive issue"
date: 2010-09-02
forum: Hardware
---

### Post by p&#333;shko on 2010-09-02
Hello,

I'm totally new to Ubuntu (I'm sure you've heard that one before), but I really like what I'm seeing so far.  The inclusion of OpenShot in version 10.04 is what finally sealed my conversion.

Anyway, I'm having a few issues with some of my laptop hardware, but I'll begin with the most pressing.  I can't get my 2TB Western Digital firewire/USB external hard drive to mount.  I can see it under Places, but when I try to access it, I get the following error message:

----

Unable to mount 2.0 TB Filesystem

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

----

Has anyone else encountered this issue or are there any pros out there who can give me a plan of attack?  Sorry if I've neglected to provide any other necessary information.

Thanks in advance for your assistance.

---

### Post by sharathcshekhar on 2010-09-02
1. Which File System format is your HDD?
2. Please post the output of $ sudo fdisk -l
3. Is it accessible in Windows and other Systems?
Looks like there there is a bad super block in the HDD. Time to back up and format is again!

---

### Post by p&#333;shko on 2010-09-02
Hi!

Thanks for the quick reply.

The drive is formatted in NTFS.  I also have a storage partition formatted in NTFS that opens fine in Ubuntu.

Here's the output I got from the prompt:

----

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x55a255a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6528    52428800    7  HPFS/NTFS
/dev/sda2            6528       22792   130641920    7  HPFS/NTFS
/dev/sda3           22792       22913      975873    5  Extended
/dev/sda4           22913       24322    11311104   83  Linux
/dev/sda5           22792       22913      975872   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000392994816 bytes
255 heads, 63 sectors/track, 243200 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0e50eca0

---

To answer your third question, the external does seem to operate more or less normally in Windows.  The only weird thing is when I try to modify it in Windows partition manager, it lists about 16GB of space as unallocated, but whenever I try to extend the main part of the drive to absorb that space (or even a small part of it), I get an error message that their isn't sufficient space to complete the action.  I can't even access it in a couple of the third party partition apps I've tried.  Could just be one final kick in the rear end from Windows as I exit stage left.  :P

Can I reformat the drive in NTFS or is there a better file system that's compatible with both Windows and Ubuntu?  I'm planning on installing Windows in Virtualbox just so I can have access to iTunes.

---

### Post by srs5694 on 2010-09-02
Your fdisk output reports that a GUID Partition Table (GPT) was found on /dev/sdb, but the output doesn't show the usual protective MBR partition table structure. It could be that this is the root of the problem -- or it could be that you've accidentally truncated the output. The complete output on a GPT disk should look like this:

```

$ sudo fdisk -l /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488386583+  ee  GPT

```

Note the last line, which defines /dev/sda1 as type 0xEE ("GPT"). Check again to be sure you don't see something similar on your disk. If it's not present, it's easily enough restored:


[list=1]
[*]Install GPT fdisk (gdisk). You can install an old version via apt-get, by typing "sudo apt-get install gdisk"; however, the last I checked, this would install version 0.5.1, which is elderly and has known bugs. (The current version is 0.6.10.) I recommend you go to the [Sourceforge download page,](https://sourceforge.net/projects/gptfdisk/files/) obtain the .deb file for your architecture, and install it. (Double-click it in a file manager and it should install.)
[*]At a shell prompt, type "sudo gdisk /dev/sdb" to launch the program. It's possible that the program will complain that it found both MBR and GPT data. Tell it to use the GPT data (option 2).
[*]Type "p" to list your partitions and verify that they look sensible. Based on the other output you mentioned, you should see at least one partition (/dev/sda2), and probably /dev/sda1, too. At least one should be of type 0700. If you do *not* see this, quit by typing "q" and post the output of gdisk's "p" command.
[*]Type "x" to enter the experts' menu.
[*]Type "n" to create a new protective MBR.
[*]Type "w" to save the changes and exit. You'll have to verify this action.
[/list]


At this point, typing "sudo fdisk -l /dev/sdb" should produce output similar to what I posted above. Try unplugging the drive and plugging it back in. With any luck, it will work more sensibly. If it doesn't, something else is going on -- perhaps some NTFS corruption that would require fixing with Windows' FDISK.

---

### Post by p&#333;shko on 2010-09-02
Thanks so much for your help.  I did not see either item you mentioned.  Here is what the 'p' command revealed:

----

Disk /dev/sdb: 3907017568 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 5A556095-7C5D-4178-BF36-383D3C8C9A64
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907017534
Partitions will be aligned on 8-sector boundaries
Total free space is 34406717 sectors (16.4 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640      3866056703   1.8 TiB     4200  LDM data partitionn
   3      3866056704      3872348679   3.0 GiB     8200  Basic data partition
   4      3906755391      3906757438   1024.0 KiB  4201  LDM metadata partition
   5      3906757439      3907017534   127.0 MiB   0C01  Microsoft reserved part

----

This all only makes a sliver of sense to me to be quite honest...

---

### Post by srs5694 on 2010-09-02
Your output looks sensible, so you can go ahead and fix the MBR as described in steps 4-6 of my earlier post; however, you've got a Windows Logical Disk Manager (LDM; aka "dynamic disks") configuration. Linux seems to have LDM support, but I know very little about it. My limited knowledge suggests that Linux will see the partitions like it would see a Linux software RAID or LVM setup. If you're very lucky, Ubuntu will detect all this automatically; however, you may need to do some additional configuration before this will work.

---

