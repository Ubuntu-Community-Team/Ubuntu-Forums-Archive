---
title: "/home not ready yet or not present after Windows partition flag change"
date: 2016-07-09
forum: Hardware
---

### Post by ObsequiousNewt on 2016-07-09
I have a dual-boot system, Windows 7 alongside Kubuntu 14.04, and using GRUB to boot. Additionally, I have three ext4 partitions: /, /home, and /data (the last of which was intended to be accessible from either system, but I rather foolishly forgot that Windows can't read ext4.)

I recently, while trying to diagnose a problem with Windows, had to run msconfig.exe, and in order to do so it was necessary to set the flag for the Windows partition to be Active.

When I restarted, I booted from GRUB as normal, but while starting, Linux presented me with a black screen and the message "The disk drive for /home is not ready yet or not present." and gives me the options to boot anyway or drop to a root shell.

I looked up this problem and got several potential solutions, but I'm hesitant to try anything just yet, as nobody seems to have gotten into this situation the same way I did.

Here is the output from fdisk -l and blkid (printed from a live CD):
```

kubuntu@kubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eeecf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   204802047   102400000    7  HPFS/NTFS/exFAT
/dev/sda2       204802048   243863551    19530752   83  Linux
/dev/sda3       243865598   416114687    86124545    5  Extended
/dev/sda4       416115630   625137344   104510857+  83  Linux
/dev/sda5       400115712   416114687     7999488   82  Linux swap / Solaris
kubuntu@kubuntu:~$ sudo blkid /dev/sda*
/dev/sda1: LABEL="zzyxy" UUID="EEC8AB91C8AB571D" TYPE="ntfs" 
/dev/sda2: UUID="5681db66-e8af-49af-a4bf-9ccba720b399" TYPE="ext4" 
/dev/sda4: UUID="21abf3cb-028f-4781-b07a-cb01ee814caf" TYPE="ext4" 
/dev/sda5: UUID="74e129b3-b0ce-4fd8-bcd2-5b2d02ceb743" TYPE="swap"

```

I recognize I got into this situation through my own stupidity... but I'd appreciate any help to get out of it.

EDIT: here is /dev/fstab, printed from the root shell I am given upon booting (commented lines cropped out):
```

# / was on /dev/sda2 during installation
UUID=5681db66-e8af-49af-a4bf-9ccba720b399 /               ext4    errors=remount-ro 0       1
# /data was on /dev/sda4 during installation
UUID=21abf3cb-028f-4781-b07a-cb01ee814caf /data          ext4   defaults        0       2
# /home was on /dev/sda6 during installation
UUID=78e492ba-3e54-418d-a621-49dc0ef4ff91 /home          ext4   defaults        0       2
# swap was on /dev/sda5 during installation
UUID=74e129b3-b0ce-4fd8-bcd2-5b2d02ceb743 none          swap  sw              0       2

```

Note that /home was on /dev/sda6 during installation, but according to fdisk -l appears to be on /dev/sda3.

---

### Post by weatherman2 on 2016-07-09
sda3 is an extended partition - a "container" for other partitions (logical partitions).  This is a kludge for the ancient MSDOS-style partition table that can handle only four primary partitions.  Inside an extended partition, you can have as many partitions as you want (up to some pretty high limit).

Anyway - sda6 is clearly not there anymore, nor is any partition with UUID 78e492ba-3e54-418d-a621-49dc0ef4ff91, obviously.

It looks like you have free space at the beginning of the extended partition sda3 where sda6 may have been.  You can visualize this with Gparted more easily.

Something else must have happened in Windows besides just changing the type of the Windows partition to active.  Could be the fact that sda6 is earlier in the partition table but numbered later wasn't liked by Windows and it "fixed" it.

If you had important data in your /home, you might try data recovery (try testdisk).  If the old /home is still there but the partition table simply got mucked, maybe it's as easy as fixing the partition table.

Gparted has some data recovery abilities as well but I've not used them.

---

### Post by oldfred on 2016-07-09
Since Windows 7, major reinstalls and new upgrades from Windows 7 to Windows 10 have major partition errors.
Windows on these major updates, forgets to write all the logical partitions. 

You can restore with testdisk, or parted rescue since you have a good idea of start (sector or 2 after start of Extended) & end (sectors before sda5) of missing partition.

Back up current partitions. Some with testdisk have made it worse by not including all existing partitions and then could not get back to starting point.
       backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT.txt
So you know sectors, your fdisk post above looks like it should be the same:
sudo parted /dev/sda unit s print 

    
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by ObsequiousNewt on 2016-07-09
By following the instructions in the link, I was able to rescue with parted. Thank you both very much for your help!

---

