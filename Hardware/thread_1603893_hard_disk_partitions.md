---
title: "hard disk partitions"
date: 2010-10-23
forum: Hardware
---

### Post by RastaManPower on 2010-10-23
hello guys i jsut removed my windows 7 partition and now i want to use the hd only for linux. is this how it should look?
[IMG]http://uppix.net/7/6/c/88b71616522837d3bedba0e576a5b.png[/IMG]
how do i merge the unallocated space with the primary ubuntu partition? it wont let me

---

### Post by srs5694 on 2010-10-23
Given your existing partition sizes, I recommend you create a new partition in the free space and use it as /home. This will be far safer than trying to move and resize your Linux system. You will, however, have to engage in some file juggling. [Here's one guide](http://www.ibm.com/developerworks/library/l-partplan.html) to doing so, albeit an old one. I'm pretty sure there's a newer Ubuntu-specific guide to this task somewhere, but I don't have a URL handy.

In the long run, having a separate /home partition is superior because it separates user data from system data. This enables you to completely wipe the OS and re-install fresh without touching your user data. This can be handy if your Ubuntu installation becomes badly damaged, if you want to upgrade while eliminating cruft from previous versions, or if you want to switch from Ubuntu to another distribution entirely.

---

### Post by RastaManPower on 2010-10-23
allright thanck you.. i am getting a mounting media error at syatyup now. how come?

---

### Post by srs5694 on 2010-10-23
You'll have to be more precise. What (if anything) have you done, and what's the precise error message? Also, if you've changed anything, please post the output of the following commands, ideally between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility:

```

df -h
sudo fdisk -lu
sudo blkid
cat /etc/fstab

```

---

### Post by RastaManPower on 2010-10-23
i dont know what i did.. this is the output
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              24G   13G  9.7G  57% /
none                  2.0G  256K  2.0G   1% /dev
none                  2.0G  1.3M  2.0G   1% /dev/shm
none                  2.0G  216K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x353d494b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   566724607   283361280   83  Linux
/dev/sda3       566724608   616949759    25112576   83  Linux
/dev/sda4       616949760   625141759     4096000   82  Linux swap / Solaris


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x353d494b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   566724607   283361280   83  Linux
/dev/sda3       566724608   616949759    25112576   83  Linux
/dev/sda4       616949760   625141759     4096000   82  Linux swap / Solaris
nico@nico-ubuntu:~$ sudo blkid
/dev/sda1: UUID="6310c575-55a8-4f20-b6ae-9925a0bacd4f" TYPE="ext4" 
/dev/sda3: UUID="1f294fee-15c0-4f02-b95d-baf4a436bac8" TYPE="ext4" 
/dev/sda4: UUID="37b1dce7-7020-49f7-86d8-e62e8d542c90" TYPE="swap" 


/dev/sda1: UUID="6310c575-55a8-4f20-b6ae-9925a0bacd4f" TYPE="ext4" 
/dev/sda3: UUID="1f294fee-15c0-4f02-b95d-baf4a436bac8" TYPE="ext4" 
/dev/sda4: UUID="37b1dce7-7020-49f7-86d8-e62e8d542c90" TYPE="swap" 
nico@nico-ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda3	/	ext4	errors=remount-ro	0	1
/dev/sda1	/media/8C846BA9846B948C	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
/dev/sda2	/media/A62C72A62C727163	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
/dev/sdb1	/media/DOCUMENTI\0402	ntfs	defaults,nls=utf8,umask=0222,nosuid,nodev	0	0
/dev/sda4	none	swap	sw	0	0



the error i am getting is unable to mount media and it tells me to press s to continue or another letter to recover


this is what i get if i click on my new partition from Computer menu
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda1 on /media/8C846BA9846B948C

---

### Post by RastaManPower on 2010-10-23
double post sorry

---

### Post by srs5694 on 2010-10-23
I believe the error is caused by old entries for your (now deleted) Windows partitions in /etc/fstab. You should remove them. The entries in question are:

```

/dev/sda1 /media/8C846BA9846B948C ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8 0 0
/dev/sda2 /media/A62C72A62C727163 ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8 0 0

```

Back up /etc/fstab and remove those two lines and the error message should go away.

You'll then be able to temporarily mount your new /dev/sda1 to some temporary location (say, /mnt), copy your /home directory to /mnt (or wherever you mount /dev/sda1), rename /home to something else (say, /home-backup), create a new (empty) /home directory, create a new /etc/fstab entry to mount /dev/sda1 to /home, and reboot. Once you're satisfied it's working, you can delete the old /home-backup directory.

---

### Post by RastaManPower on 2010-10-24
it says the fstab is read only. i dont understand what you wrote sorry

---

### Post by srs5694 on 2010-10-24
You need to be root to edit /etc/fstab, so use sudo or gksudo to launch your editor on it.

As to the rest of what I wrote, consult a Web guide about moving /home, such as the one I referenced earlier, in post #2 in this thread.

---

### Post by cascade9 on 2010-10-24
Umm....this might not be what you want to do, but have you considered just reinstalling? 

Having /root that 'deep' into the drive is a lot slower than having it at the beginning of the drive, and it does make a difference (booting in particular should be faster).  

> **srs5694 said:**
> Given your existing partition sizes, I recommend you create a new partition in the free space and use it as /home. This will be far safer than trying to move and resize your Linux system. You will, however, have to engage in some file juggling. [Here's one guide]("http://www.ibm.com/developerworks/library/l-partplan.html") to doing so, albeit an old one. I'm pretty sure there's a newer Ubuntu-specific guide to this task somewhere, but I don't have a URL handy.

In the long run, having a separate /home partition is superior because it separates user data from system data. This enables you to completely wipe the OS and re-install fresh without touching your user data. This can be handy if your Ubuntu installation becomes badly damaged, if you want to upgrade while eliminating cruft from previous versions, or if you want to switch from Ubuntu to another distribution entirely.

+lots and lots. 

Having a seperate /home makes life a lot easier.

---

### Post by RastaManPower on 2010-10-25
ok so i repartitioned the whole drive and reinstalled ubuntu. this is how my hd looks now. is this correct?
[IMG]http://uppix.net/7/6/3/f543bebfcf2e6d70eff1c79938476.png[/IMG]

---

### Post by srs5694 on 2010-10-25
Yes, that looks good to me. I do have some suggestions, but none of them are critical:


[list]
[*]The separate /boot probably isn't required, but it won't hurt. You could eliminate it entirely.
[*]I'd make /boot ext2 rather than ext4, and make it about half the size it is now; for such a small partition, the journal and other extra features of ext3 and ext4 aren't important, and can actually cause problems. I seldom use more tha 100 MiB on my /boot partitions.
[*]I'd make /dev/sda3 a logical partition rather than a primary partition, just to clear up one primary partition for future use, should it be necessary in the future (say, if you want to install FreeBSD or Windows).
[*]If you're sure this disk will be used for Linux only, you might consider using the newer GUID Partition Table (GPT) format rather than the older Master Boot Record (MBR) format for partitions. GPT has a number of minor advantages over MBR, such as CRCs to help identify data corruption in the partition table, backups of the important partition table data, labels for partitions, and elimination of the primary/extended/logical partition distinction. OTOH, a few buggy BIOSes have problems with GPT disks. These problems can [usually be overcome,](http://www.rodsbooks.com/gdisk/bios.html) but you may need to jump through some hoops to do so. If you've got existing data on the disk, you can use [GPT fdisk](http://www.rodsbooks.com) to convert it. If not, you can use GParted to create a new partition table -- select Device -> Create Partition Table, click the Advanced button, and select "gpt" as the type. If you go with GPT, though, be sure to create a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) of 1 MiB (*MiB*, not GiB; in fact, it can be as small as about 35 KiB) for GRUB 2.
[/list]

---

### Post by RastaManPower on 2010-10-26
if i delete the boot partition i will be able to boot in ubuntu?

---

### Post by srs5694 on 2010-10-26
Sorry; I missed the fact that you'd already re-installed. If Ubuntu is already installed, then you should keep the /boot partition as it is, since the system relies upon it.

---

### Post by RastaManPower on 2010-10-26
i have been reinstallign ubuntu the the past 5 days and i am sick of it. i think i will keep it the way it is.. sick of spending hours installing stuff

---

