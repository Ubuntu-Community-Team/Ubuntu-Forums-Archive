---
title: "External Usb Hard Drive wont mount anymore"
date: 2011-10-04
forum: Hardware
---

### Post by mrjoeyman on 2011-10-04
I have a laptop which is connected to my usb hard drive. I backed up some files to it and upon a regular reboot it is now inaccessible. I have Ubuntu and LMDE (Mint 11) installed on my laptop and both were able to access it. The following is information I am including to help someone to help me. Thank you.

when I click on it I get this message:

    > Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 1).
    Failed to mount '/dev/sdb1': Input/output error
    NTFS is either inconsistent, or there is a hardware fault, or it's a
    SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
    then reboot into Windows twice. The usage of the /f parameter is very
    important! If the device is a SoftRAID/FakeRAID then first activate
    it and mount a different device under the /dev/mapper/ directory, (e.g.
    /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
    for more details.



I checked it in the Disk Utiity program in Mint and it passed all tests except the one that checks the filesystem. It give me the message:

    > File system NOT clean



I used Testdisk to analyze it and here is what the log file says afterward:

    > Mon Oct 3 19:22:48 2011
    Command line: TestDisk

    TestDisk 6.11, Data Recovery Utility, April 2009
    Christophe GRENIER <grenier@cgsecurity.org>
    [http://www.cgsecurity.org](http://www.cgsecurity.org)
    OS: Linux, kernel 3.0.0-1-486 (#1 Sun Jul 24 13:43:13 UTC 2011)
    Compiler: GCC 4.4 - Sep 15 2010 23:07:43
    ext2fs lib: 1.42-WIP, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
    /dev/sda: LBA, HPA, LBA48, DCO support
    /dev/sda: size 117210240 sectors
    /dev/sda: user_max 117210240 sectors
    /dev/sda: native_max 117210240 sectors
    /dev/sda: dco 117210240 sectors
    Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
    Hard disk list
    Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63, sector size=512 - ATA IC25N060ATMR04-0
    Disk /dev/sdb - 320 GB / 298 GiB - CHS 38913 255 63, sector size=512 - WD 3200AAJ External

    Partition table type (auto): Intel
    Disk /dev/sdb - 320 GB / 298 GiB - WD 3200AAJ External
    Partition table type: Intel

    Analyse Disk /dev/sdb - 320 GB / 298 GiB - CHS 38913 255 63
    Geometry from i386 MBR: head=255 sector=63
    NTFS at 0/1/1
    get_geometry_from_list_part_aux head=255 nbr=2
    get_geometry_from_list_part_aux head=8 nbr=1
    get_geometry_from_list_part_aux head=16 nbr=1
    get_geometry_from_list_part_aux head=32 nbr=1
    get_geometry_from_list_part_aux head=64 nbr=1
    get_geometry_from_list_part_aux head=128 nbr=1
    get_geometry_from_list_part_aux head=240 nbr=1
    get_geometry_from_list_part_aux head=255 nbr=2
    Current partition structure:
    1 P HPFS - NTFS 0 1 1 38912 254 63 625137282 [My External Drive]
    No partition is bootable
    Ask the user for vista mode
    Computes LBA from CHS for Disk /dev/sdb - 320 GB / 298 GiB - CHS 38914 255 63
    Allow partial last cylinder : Yes
    search_vista_part: 1

    search_part()
    Disk /dev/sdb - 320 GB / 298 GiB - CHS 38914 255 63
    NTFS at 0/1/1
    filesystem size 625137282
    sectors_per_cluster 8
    mft_lcn 786432
    mftmirr_lcn 39071080
    clusters_per_mft_record -10
    clusters_per_index_record 1
    HPFS - NTFS 0 1 1 38912 254 63 625137282 [My External Drive]
    NTFS, 320 GB / 298 GiB
    get_geometry_from_list_part_aux head=255 nbr=2
    get_geometry_from_list_part_aux head=8 nbr=1
    get_geometry_from_list_part_aux head=16 nbr=1
    get_geometry_from_list_part_aux head=32 nbr=1
    get_geometry_from_list_part_aux head=64 nbr=1
    get_geometry_from_list_part_aux head=128 nbr=1
    get_geometry_from_list_part_aux head=240 nbr=1
    get_geometry_from_list_part_aux head=255 nbr=2

    Results
    * HPFS - NTFS 0 1 1 38912 254 63 625137282 [My External Drive]
    NTFS, 320 GB / 298 GiB

    interface_write()
    1 * HPFS - NTFS 0 1 1 38912 254 63 625137282 [My External Drive]
    write!

    write_mbr_i386: starting...
    write_all_log_i386: starting...
    No extended partition
    You will have to reboot for the change to take effect.

    TestDisk exited normally.




As you can see Testdisk wrote the mbr to it, but after reboot, still same error messages.




This is what I get after typing "fdisk -l" into the terminal:

    > Disk /dev/sda: 60.0 GB, 60011642880 bytes
    255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x000081ab

    Device Boot Start End Blocks Id System
    /dev/sda1 2048 47102579 23550266 83 Linux
    /dev/sda2 47102580 108551204 30724312+ 83 Linux
    /dev/sda3 108551205 117210239 4329517+ 82 Linux swap / Solaris

    Disk /dev/sdb: 320.1 GB, 320072933376 bytes
    255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000

    Device Boot Start End Blocks Id System
    /dev/sdb1 * 63 625137344 312568641 7 HPFS/NTFS/exFAT


I hope someone can help me, thanks.

---

### Post by coffeecat on 2011-10-04
This is the important bit:

> Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sdb1': Input/output error
[COLOR="Red"]NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. [/COLOR]In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

You probably have a corrupted filesystem in sdb1. A hardware fault is a possibility but filesystem corruption is more likely. Testdisk won't be able to help. You need to connect the drive to a Windows system and run chkdsk. NTFS is a Microsoft filesystem and although the Linux command line utility ntfsfix can repair some NTFS inconsistencies, this almost certainly needs chkdsk.

---

### Post by WasMeHere on 2011-10-04
This first option should be rather safe, but it is always good to backup the private files, before your tamper with the partition.

I suggest you try the 'automatic advice' of your first quote. _Attach your usb hard drive to a windows computer_ and run 
```
chkdsk /f
``` on the partition with errors on your usb hard drive. 'Then reboot into Windows twice' probably means that some actions occur during boot on the boot partition. This may be relevant only if you boot from the [usb] drive. Anyway reboot and try to find your usb drive again after the chkdsk session!

[I]Edit: during writing you already received a similar reply,
so I summarize: '+1'[/I]

---

### Post by mrjoeyman on 2011-10-04
Ok I have it plugged into my Windows machine and I can see my files on the hard disk. They look to be fine. How do I run a checkdisk? Thanks.

Update: I googled it and right clicked the icon in my computer, and clicked properties and am running the chkdsk now. I will report the findings.........

---

### Post by mrjoeyman on 2011-10-04
Ok after running the chkdsk, and the test that goes with it (checks for and tries to recover bad sectors), all was good. I then formatted it and put it back on my linux machine and it works like new. I don't understand it, but I love it. Its a really big drive. Can you tell me how I can make it into 2 partitions? I would like to have just one small partition to work with..and leave the rest unallocated? Is that possible with a drive like this? Thanks. I am marking this solved but will post this question I just asked as a new post if I can get it accomplished with your help. Love this community! I get such quick responses!!  ):P

Update: Here is the new post and the information leading the the solution to the previously new question in this post;

[http://ubuntuforums.org/showthread.php?t=1854719](http://ubuntuforums.org/showthread.php?t=1854719)  (Solved)

---

### Post by WasMeHere on 2011-10-05
After a good backup, try gparted (from a live cd or usb system)!

Have fun
Olle

---

### Post by mrjoeyman on 2011-10-05
I sure did have fun! Thanks :p

Here is a link to the rest of this solution:

[http://ubuntuforums.org/showthread.php?t=1854719](http://ubuntuforums.org/showthread.php?t=1854719)  (SOLVED)

---

