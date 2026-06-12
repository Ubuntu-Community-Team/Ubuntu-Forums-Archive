---
title: "External USB 1 TB HD &quot;unrecognized&quot;"
date: 2011-12-26
forum: Hardware
---

### Post by Lixie on 2011-12-26
I had recently reformatted my laptop with Ubuntu 11.10. As I was loading files back onto my laptop from my external hard drive, it suddenly stops working. I have uploaded most of the files I needed, but I would still like to be able to access my hard drive from my laptop. 

The hard drive mounts properly in Windows still. When I open up disk utility from dash in Ubuntu, the external hard drive is there, but unrecognised. As well, it shows up with the wrong memory: it says it is 2.2 TB hard drive. 

I haven't formatted the drive, or created any partitions on it previously. All I had been doing was transferring files off of it before it suddenly stopped working. I'm fairly new to Ubuntu, so any help would be very much appreciated! 

I've already tried:

Manual mounting. 

This is what terminal returns when I use "sudo fdisk -1"

> fdisk: invalid option -- '1'
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track



I've also tried: 

"sudo mount -t vfat /dev/sdb /media/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137"

it returns:

> mount: /dev/sdb: can't read superblock

And I tried the other:

"sudo mount -t ntfs-3g /dev/sdb /media/external"

it returns: 
> Error reading bootsector: Input/output error
Failed to mount '/dev/sdb': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Please help!

---

### Post by gareththered on 2011-12-26
The command you're looking for is > sudo fdisk -lthe option is the letter 'L' in lower case.  This will list all your drives and their partitions. 
The partition you need will probably have 'HPFS/NTFS/exFAT' in the right had column.

 It is the partition you will need in your second command to manually  mount.  That is, where you have 'dev/sdb' you should have 'dev/sdbx'  where is 'x' is a number as given to you from the previous 'fdisk'  command.  For example, if the 'fdisk' command shows 'dev/sdb2' to be the NTFS partition, you should use 'dev/sdb2' in the mount command.

You could also use > sudo ntfsck /dev/sdb2 (change the partition number for the correct one) to check the filesystem on the NTFS partition.

Good luck!

---

