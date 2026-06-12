---
title: "Partitioning a 4 Terra Disc"
date: 2013-07-31
forum: Hardware
---

### Post by theKuch on 2013-07-31
I've added new disks before, but not getting far this time.

I installed 4 tera drive. It is for data only.

I ran gPartEd but don't seem to be able to get it allocate the drive. I would prefer to have the disk as 1 partition.

I select Primary Partition, ext3, align to MiB

I press add and see the new partition. It says it is an msdos poartition.

When I "apply" I get a message that I have exceed the msdos partition-table-imposed maximum which seems to be about 2 tera.

Is this indeed the limit?

Thanks

---

### Post by theKuch on 2013-07-31
Just tried again with palimpsest an received the following error message:

Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdc, start=0, size=4000787000000, type=0x83
Entering MS-DOS parser (offset=0, size=4000787030016)
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
got it
got disk
new partition
Error: partition length of 7814032002 sectors exceeds the msdos-partition-table-imposed maximum of 4294967295
ped_disk_add_partition() failed

---

### Post by oldfred on 2013-07-31
Gparted defaults to MBR(msdos) partitioning, you have to use gpt. I have not partitioned a large drive, but use gpt on several smaller drives.

  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Are you sure you want one large partition? If for movies or something that may make sense. But otherwise how are you planning on backing up. How long will filechecks either chkdsk for NTFS or e2fsck for ext4 take?

 MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

      
 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

You can use gdisk and even if not partitioning with gdisk you should install it. You cannot use fdisk on gpt partitioned drives.


 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by theKuch on 2013-08-01
Thanks

I set it up as 2 discs of 2 TB each.

---

### Post by Hexxus on 2013-08-01
Was that as a GPT then? Or MBR? If GPT I wonder why 2X instead of 1 big volume... the only reason I ask is because the prices on those 4TB drives are coming down, Newegg had one yesterday for $129.99.

---

