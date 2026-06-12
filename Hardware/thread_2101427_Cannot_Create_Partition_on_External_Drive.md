---
title: "Cannot Create Partition on External Drive"
date: 2013-01-04
forum: Hardware
---

### Post by suddentwigs on 2013-01-04
Hello there. I'm using Ubuntu Studio 10.04. I've just plugged in my brand new hard drive and reformatted the volume to Ext4. I then wondered if I should format the drive too, which has proven to be a mistake as the computer will not read it and also refuses to create a partition. This is the message, and it does not vary across different filesystems: 

Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdc, start=0, size=3000592977920, type=0x83
Entering MS-DOS parser (offset=0, size=3000592977920)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
Warning: Device /dev/sdc has a logical sector size of 4096.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

got it
got disk
Error: Can't have a partition outside the disk!
ped_partition_new() failed


Any thoughts?

---

### Post by sudodus on 2013-01-04
Check very carefully that you get the correct drive before doing anything, because if you do this to another drive, there is no way to restore (except if you have a good backup somewhere else). Will the following command recognize the drive (is it [FONT=Courier New]**/dev/sdc**[/FONT] also at this moment, or maybe something else)?

```
sudo fdisk -lu
```***dd*** is nicknamed disk destroyer, so be careful! Double check and triple check that everything is correct! The following code will overwrite the first 1 MB of the drive with zeros.

```
sudo if=/dev/zero of=/dev/sdx bs=1024 count=1024
```You need to replace x with the appropriate letter for the drive to be overwritten, it used to be /dev/sdc, but maybe not now.

After that you should be able to use ***gparted*** again, start with

Device (or maybe Unit) -- Create Partition Table (MSDOS is the standard one with MBR)

and after that you should be able to create a partition again.

---

### Post by suddentwigs on 2013-01-04
Thanks. However, I think I've got it sorted in the meantime. I had it set to format the drive as master boot record, once I set it to GUID or No Partition, it seems to work. No real idea what it means, but I think it's okay now.

---

### Post by sudodus on 2013-01-04
You can find out from this wiki page

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

