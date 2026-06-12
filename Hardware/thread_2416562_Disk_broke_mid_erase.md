---
title: "Disk broke mid erase"
date: 2019-04-11
forum: Hardware
---

### Post by silveringking on 2019-04-11
So quick and short, a minute after I started an ata secure erase, using partedmagic, my cat set into the pc and by magic shut it off. So now I have a broken disk inside my laptop, now, in case something happened Ive cloned my disk into another disk. (So I don't mind loose all the info).

Ive tried to a few tests even testdisk but it doesnt seem to work. Ive download bootinfoscript and here is the result

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop252                                            squashfs   
/dev/loop253                                            squashfs   
/dev/loop254                                            squashfs   

================================ Mount points: =================================

Device           Mount_Point              Type       Options



======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sda



=============================== StdErr Messages: ===============================

hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
  /dev/sda: read failed after 0 of 4096 at 0: Input/output error
  /dev/sda: read failed after 0 of 4096 at 1000204795904: Input/output error
  /dev/sda: read failed after 0 of 4096 at 1000204877824: Input/output error
  /dev/sda: read failed after 0 of 4096 at 4096: Input/output error
mdadm: No arrays found in config file or automatically


```

Any ideas of what I can do. I would guess I could try to fix it with badblocks but I cannot figure out which block block is broken, my best guess is block 4096, but Ive decided to ask first.

---

### Post by TheFu on 2019-04-11
Did you try recreating a new partition table using gparted? If you select GPT as the type, there will be 2 copies written - one at the beginning and the other at the end of the disk, then create at least 1 partition and format it with LVM or the file system of your choice.

If there aren't huge physical errors, this should do it.

You might want to consider using LUKS encryption on all the partitions. That way if the disk does fail and it is still under warranty, your data won't be available to the vendor.

Also, you can always run **smartctl** against the disk to see what it knows about itself and any failures. Run a test first, then look at the output later, after the test completes.  Something like **sudo smartctl -t short /dev/sda** is the first command. Usually takes 2-3 min to finish.  Then use **sudo smartctl -a /dev/sda** to see the data.  This is non-destructive.  The raw columns are what I look at, since they make the data pretty clear for the stuff we care about.

---

### Post by silveringking on 2019-04-11
Hi here is the trouble, I could easily clone back the disk, but the disk itself is unmountable, it is not detected by mounting partition and gparted stays a long scanning the device, more than it should. However I will run smartctl, right after I wait a while for gparted scan.

---

### Post by silveringking on 2019-04-11
Also as we're speaking the smartmountools tests is running but no line has been given, earlier I tried with fsck and in 12 hours I found no results.

[IMG]https://i.imgur.com/wmYEjm3.png[/IMG]

---

### Post by TheFu on 2019-04-11
If the partition table is gone, no other tools will work until that is replaced, besides parted, fdisk, gparted, other partition management tools or the SMART data tools.

fsck works on file systems, not partitions and not partition tables.

Trying to run fsck against the full HDD is a logic failure.  fsck works against file systems on partitions.

/dev/sda = hole disk
/dev/sda1 = 1st partition on the disk, if it exists and the partition table isn't corrupted.
/dev/sda2 = 2nd partition on the disk, if it exists and the partition table isn't corrupted.
/dev/sda3 = 3rd partition on the disk, if it exists and the partition table isn't corrupted.
....

/dev/sda99 = 99th partition on the disk, if it exists and the partition table isn't corrupted.

With GPT partitioning, over 100 primary partitions can be created, dependent on space.
With MBR partitioning, only 4 "primary" partitions are allowed. Normally, everyone would create 1 of those "primary" partitions as an **extended** partition, which can hold 100+ "logical partitions" ... but all of those logical partitions have to be inside the single "extended partition", contiguous, storage area.  Logical partitions are a hack created to solve a problem while being backwards compatible, mostly.

If you run Linux, using GPT always is a no-brainer choice. Always use GPT.

If you run Windows, there are some specific limitations to be aware with using GPT.  They effectively are gone if the version of Windows is 64-bit, UEFI is used for booting and Win7+ is used.

---

### Post by silveringking on 2019-04-11
Then what do you recommend in this case to recreate the partition table, waiting for gparted to load up?

I was considering this: 

[https://wiki.archlinux.org/index.php/badblocks](https://wiki.archlinux.org/index.php/badblocks)

---

### Post by TheFu on 2019-04-11
badblocks won't fix anything that is physically or logically corrupted too much.  Different sort of problem, most likely.

Use any partition management tool that you like to create a GPT partition.  gparted is 1 of them, but parted, fdisk, and a few others can too.

Any chance the disk controller or cable or power could be failing too?

If you ran the smartctl short test, what were the results?

---

### Post by silveringking on 2019-04-11
So, quick update, it seems the disk gets really slow after a process starts and for me some reason it doesn't kill when a window is closed. Anyway, after a hard reset on the computer, the first I've done is trying to erase the partition again, this time I managed to start erasing the partition, however as you can see this is getting really slow, after the partition is erased, this might take a few days, ill just create a new partition and run some test, it might happen the disk is physically damaged.

[IMG]https://i.imgur.com/Ab0UH7h.png[/IMG]

---

