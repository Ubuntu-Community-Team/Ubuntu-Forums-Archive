---
title: "External USB Drive"
date: 2012-12-25
forum: Hardware
---

### Post by fillemazendacus on 2012-12-25
Hey!

I have new problem.
I can't get contact between ubuntu and external USB drive. It is empty drive and it will be enough when I can format it some way..

*lsusb* gave me this, but I can't see this drive anywhere else..
```
Bus 003 Device 006: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB

```

---

### Post by 2F4U on 2012-12-25
It probably has no filesystem on it and is not mounted, so you won't see it in, for example, the file manager. Are you able to see it in the partition manager?

---

### Post by fillemazendacus on 2012-12-25
Mm.. I don't see it in System Monitoring.
I installed something KDE partition manager, but this not works correctly, showing nothing at all.. And sure I don't see it in any file manager too.. :(

---

### Post by pardalet on 2012-12-25
Looks like your USB drive might not be formatted. Try the Gnome Disk Utility:

```
$ sudo apt-get install gnome-disk-utility
```


With this utility you should be able to view the USB drive and format it.

---

### Post by zlatankos on 2012-12-25
hello im new here... i dont know if there is any reason to make a new thread so i continue this one...

i use Ubuntu 12.04 
```
Notebook-PC:~$ uname -r
3.2.0-35-generic-pae
```I used an external disk yesterday , in the beggining evething was ok. But when i do safely remove or unmount or restart,shut down etc  and i try to reconnect it  i get the following message :

```

         unable to mount

Error mounting: mount exited with exit code 13:  ntfs_mst_post_read_fixup_warn: magic: 0x43425355  size: 4096   usa_ofs:  1014  usa_count: 65535: Invalid argument
Actual VCN (0x800009f01000000) of index buffer is different from expected VCN (0x0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```except from this some times i get no message and the nautilus doesnt show something.

when i used the hd to windows seems like it is corrupted and needs a format, after format (to ntfs) everything is ok in windows whatever i do write eject etc

but when i write and remove the disk in ubuntu then it get corrapted and needs format to ntfs. Also this format is ok only in windows when i tried it with gparted i get the following :
 (i tried format to ntfs , fat32 , ext3 ext4 with gparted and the result is the same....)

[IMG]http://img703.imageshack.us/img703/3605/snapshot2rk.png[/IMG]



before the format the problem seems like this in gparted

[IMG]http://img560.imageshack.us/img560/1653/snapshot1cs.png[/IMG]


summarizing it seems that there is problem when i write in disk and remove it and using ubuntu, then the data or the file system is getting corrupted...(in windows everything is fine)

thanks in advance 
and sorry if my english is too bad

---

### Post by fillemazendacus on 2012-12-26
> **pardalet said:**
> Looks like your USB drive might not be formatted. Try the Gnome Disk Utility:

```
$ sudo apt-get install gnome-disk-utility
```


With this utility you should be able to view the USB drive and format it.

It gave me errors.. :(

Trying to use overwrite format (NTFS):
```
Error erasing device: Error writing 1048576 bytes to /dev/sdb: Input/output error (udisks-error-quark, 0)
```

Trying to use not-overwrite format (NTFS):
```
Error creating file system: Command-line `mkntfs -f -F -L "Volume" "/dev/sdb"' exited with non-zero exit status 1:
stdout: `Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
'
stderr: `/dev/sdb is entire device, not just one partition.
mkntfs forced anyway.
Error writing to /dev/sdb: Input/output error
Error writing non-resident attribute value.
add_attr_sd failed: Input/output error
Couldn't create root directory: Input/output error
Failed to fsync device /dev/sdb: Input/output error
Warning: Could not close /dev/sdb: Input/output error
' (udisks-error-quark, 0)
```

What the Input/Output errors? I tried different USB-ports..

---

### Post by gordintoronto on 2012-12-26
That seems to indicate that the hard drive has failed.

---

### Post by pardalet on 2012-12-26
I'm afraid **gordintoronto** might be right...

But before throwing the drive away, have you tried to plug it to another machine running another OS?

---

### Post by fdrake on 2012-12-26
what is fdisk or parted saying?
```

sudo fdisk -l
sudo parted -l

```

---

### Post by fillemazendacus on 2012-12-27
First place was Windows where happened nothing too.

sudo fdisk -l:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

```

sudo parted -l, drive started to make sound, and after little time:
```
Model: ATA ST3000DM001-1CH1 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  99.6MB  98.6MB  fat32                 boot
 2      99.6MB  2983GB  2983GB  ext4
 3      2983GB  3001GB  17.1GB  linux-swap(v1)


Error: /dev/sdb: unrecognised disk label 
```


but lsusb still found this:
```
Bus 005 Device 004: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB

```


Just for one more test i tried ext4-format and got huge message:
```
Error creating file system: Command-line `mkfs.ext4 -F -L "New Volume" "/dev/sdb"' exited with non-zero exit status 37:
stdout: `Filesystem label=New Volume
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
134217728 inodes, 536870400 blocks
26843520 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
16384 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848, 512000000

Allocating group tables:     0/16384    1/16384    2/16384    3/16384    4/16384    5/16384    6/16384    7/16384    8/16384    

***hell many numbers***

/1638416383/16384           done                            
Writing inode tables:     0/16384    1/16384    2/16384    3/16384    4/16384    5/16384    6/16384    7/16384    8/16384    

***hell many numbers***

/1638416383/16384           done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information:     0/16384    1/16384'
stderr: `mke2fs 1.42.5 (29-Jul-2012)
Warning: could not erase sector 2: Attempt to write block to filesystem resulted in short write
Warning: could not read block 0: Attempt to read block from filesystem resulted in short read
Warning: could not erase sector 0: Attempt to write block to filesystem resulted in short write

Warning, had trouble writing out superblocks.' (udisks-error-quark, 0)
```


Is it possible that something is wrong somewhere in my ubuntu with this "/dev/sdb"?
Will it be not safe unplug from Windows and if yes, is that somehow possible to fix then?

---

### Post by fdrake on 2012-12-27
```

sudo dd if=/dev/sdb count=$((2*16384)) | hexdump -C | > ~/Desktop/bin

```
post here the content please

---

### Post by fillemazendacus on 2012-12-27
> **fdrake said:**
> ```

sudo dd if=/dev/sdb count=$((2*16384)) | hexdump -C | > ~/Desktop/bin

```
post here the content please



```
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00236693 s, 0.0 kB/s
```

---

