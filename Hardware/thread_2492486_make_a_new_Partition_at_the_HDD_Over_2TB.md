---
title: "make a new Partition at the HDD? Over 2TB"
date: 2023-11-13
forum: Hardware
---

### Post by Raymond Day on 2023-11-13
Hi I want to make a 8TB partition at the end of the HDD.

I used the Gparted live but it errors because it's 8TB.

Here is some of the command line:

```
root@cardboard:~# parted /dev/sda
GNU Parted 3.4
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: ATA HGST HUH721010AL (scsi)
Disk /dev/sda: 10.0TB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  318GB   318GB   primary   ext4            boot
 2      318GB   320GB   2136MB  extended
 5      318GB   320GB   2136MB  logical   linux-swap(v1)
 3      320GB   2000GB  1680GB  primary   ext4

(parted) mklabel gpt
Warning: Partition(s) on /dev/sda are being used.
Ignore/Cancel? c
(parted) quit
root@cardboard:~# fdisk -l
Disk /dev/loop0: 105.82 MiB, 110960640 bytes, 216720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 9.59 MiB, 10051584 bytes, 19632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 9.1 TiB, 10000831348736 bytes, 19532873728 sectors
Disk model: HGST HUH721010AL
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x0004a747

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sda1  *         2048  620967935  620965888 296.1G 83 Linux
/dev/sda2       620969982  625141759    4171778     2G  5 Extended
/dev/sda3       625141760 3907028991 3281887232   1.5T 83 Linux
/dev/sda5       620969984  625141759    4171776     2G 82 Linux swap / Solaris

Partition 2 does not start on physical sector boundary.
Partition table entries are not in disk order.
root@cardboard:~#
```

What could be the command to add a 8TB at the end I guess it has to be a /dev/sda6 ?

Hope some one can help.

-Raymond Day

---

### Post by yancek on 2023-11-13
> (parted) mklabel gpt
Warning: Partition(s) on /dev/sda are being used.

GParted seems to be trying to change the partition label from msdos to gpt.  I don't know how or why anyone would want an msdos partition table on a 10TB drive or how that happened.   Your install is a Legacy install rather than an EFI install which has commonly used for the last decade.  If you change the partition label from msdos to gpt, you may lose data.  I understand there are ways to do that but I don't know how to.

You have an Extended partition with one logical partition (sda5) within it.  Using the old msdos partitioning, you are only allowed 4 primary partitions and one of those is your Extended partition so you can create another primary at the end of the drive.  I don't actually know if you will have a problem with a partition that size on an msdos drive? 

Your fdisk output shows 19532873728 sectors and you would have to create the partition after the end sector of sda3 which is 3907028991.  
The partition would be a primary partition and would be sda4.  If you were using GPT, you could have up to 128 primary partitions, with 
an msdos partition table you are limited to 4.

You could also unmount the swap and delete it and delete the Extended partition and recreate it at the end of the drive and use 
up the rest of the drive and create logical partitions.  I's suggest the first option.  Would have all been simpler with a gpt partition table.o

---

### Post by TheFu on 2023-11-13
So, partitions over 2TB aren't supported using MSDOS/MBR partition tables.  You'll need to convert or wipe the disk and start over using a GPT partition table.  **gdisk** might be able to convert from MBR-->GPT, but that extended primary parition and logical partition won't map easily to GPT primary partitions.  You'll need to manually fix the /etc/fstab.  

***_[COLOR="#FF0000"]WARNING:[/COLOR]_***
**Before attempting any conversion, ensure you have a backup of any files/data you don't want to lose.  Screwing with partitions has a habit of data destruction.**

I'd use **gparted** myself.

Remember all those times the last 10+ yrs that people said to stop using MBR partitioning?  I guess you weren't really listening. Well, it was important.  That's ok, I don't always listen either. ;)

Additionally, because drive vendors don't count like every other computer person does, your 10TB drive isn't really 10TB.  It is closer to 9.1TB.

I wouldn't use any HDD over 2TB for an OS.  2TB and larger are for data.  For the OS, use an SSD.  I write this after learning the hard way that 4TB HDDs have the same issue and putting the OS onto them seems to be hard on the drive to make the lifespan reduces to just above the warranty period.  I lost (3) 4TB HDDs that way - they had 3 yr warranties and all of them with the OS installed too, died before their 4th year in service.  I switched the OS to be a smaller storage device and things have been better AND my 4TB and larger HDDs are lasting longer now.

---

### Post by Raymond Day on 2023-11-14
I started to install for the 3rd time now Ubuntu server 22.04.3 LTS and each time it says insert boot devise. So it just will not boot it's on the 10TB drive on a **Intel® Desktop Board D945GCLF2** it takes a log time because it's only got USB 2.0 not 3.0 it's that old. But 2 SATA ports.

Was installing as LVM and this last time turn that off and still no boot and I seen it said installing GRUB.

How can I fix this? I wanted to then copy the files from the 2TB drive it was running on.

-Raymond Day

---

### Post by Yellow Pasque on 2023-11-14
> Warning: Partition(s) on /dev/sda are being used.
You may need to run "sudo swapoff" so you can convert the drive to GPT (Note: as others have said, all data will be erased off the drive). 
IIRC, a LiveUSB will make use of a swap partition if it detects one.

---

### Post by TheFu on 2023-11-14
> **Yellow Pasque said:**
> You may need to run "sudo swapoff" so you can convert the drive to GPT (Note: as others have said, all data will be erased off the drive). 
IIRC, a LiveUSB will make use of a swap partition if it detects one.

Actually, the gdisk conversion may not wipe any data, just swap the partition table, but that isn't guaranteed, so planning for the worst is smart.  The worst case would be total data loss.

---

### Post by yancek on 2023-11-14
> So it just will not boot it's on the 10TB drive  

What is the "it" you are referring to that is on the 10TB drive?  How are you trying to install the Ubuntu Server?  Did you download the iso file and write it to a USB with software designed for that purpose?  If so, what software?  Did you verify the download was good before putting it on the USB/DVD?  What are you trying to install?  You already have GParted on a disk right?  You already have a Linux install on the drive, correct?  Problems creating an 8TB partitions were explained above.  You need a GPT partition table not msdos so that is what you would need to do.  You might be able to change it without data loss, I don't know but I would certainly backup any important data before doing anything.

---

### Post by Raymond Day on 2023-11-22
I got it to boot from a 2TB SSD and running very good.

Then I used Webmin to make the 2TB and the 10TB look like one big LVM drive.

It worked real good and copied about 5TB of Data to it.

Power went out for a little and it will not boot now. It's goes to **grubrescue**.

I got a grml live Linux booted on a USB stick. Because it supports LVM.

Here are some commands I did but just don't know how to fix this:

```
root@grml ~ # ls
root@grml ~ # pwd
/root
root@grml ~ # cd /
root@grml / # ls
bin   dev  grml-live  initrd.img      lib    lib64   media  opt   root  sbin  sys  usr  vmlinuz
boot  etc  home       initrd.img.old  lib32  libx32  mnt    proc  run   srv   tmp  var  vmlinuz.old
root@grml / # vgscan
  Found volume group "vgcardboard" using metadata type lvm2
root@grml / # vgchange -ay
  2 logical volume(s) in volume group "vgcardboard" now active
root@grml / # df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            961M     0  961M   0% /dev
tmpfs           198M  892K  197M   1% /run
/dev/sdc1       855M  855M     0 100% /run/live/medium
/dev/loop0      781M  781M     0 100% /run/live/rootfs/grml64-full.squashfs
tmpfs           986M   13M  974M   2% /run/live/overlay
overlay         986M   13M  974M   2% /
tmpfs           986M     0  986M   0% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           986M     0  986M   0% /tmp
tmpfs           198M     0  198M   0% /run/user/0
root@grml / # mkdir /media/RESCUE
root@grml / # mount /dev/vgcardboard/root /media/RESCUE
root@grml / # mount /dev/sda1 /media/RESCUE/boot
mount: /media/RESCUE/boot: unknown filesystem type 'LVM2_member'.
       dmesg(1) may have more information after failed mount system call.
32 root@grml /
```

So how can I fix this on a LVM to boot? What commands can I give with this live grml ?

Here is a LS on the mounted part that worked at lest.

```
32 root@grml / # cd /media/RESCUE
root@grml /media/RESCUE # ls
303GB_Partition1  boot  dev  home  lib32  libx32      media  opt   root~on-2TB-SSD  run   snap  sys  usr
bin               core  etc  lib   lib64  lost+found  mnt    proc  root             sbin  srv   tmp  var

I was copying the files from the old boot drive to this new SSD

root@grml /media/RESCUE #
```

hope some one can help.

-Raymond Day

---

### Post by TheFu on 2023-11-22
Who told you to use LVM?  Sure, I'm a fan, but not unless you don't already know it from running a simple setup for a few years first.

Looks like you are just running random commands without understand what they each do. It is easy to miss the important parts that way, especially if you don't understand what LVM does/is.

I cannot help with details in the next few days, so I don't want to start. Best if someone else does it and I suspect you'll have better luck getting help without LVM in the middle.  Or you could work through an LVM tutorial. Any tutorial on Linux regardless of OS is fine. LVM is LVM is LVM across all Linuxen.  BTW, nearly all, if not all, Ubuntu Live Boot ISOs include LVM too.

I will leave you with 1 command that should show how storage objects are contained inside other storage objects:
```
$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```

Trying to mount things in the LVM-way that aren't LVM will always fail.

---

### Post by Raymond Day on 2023-11-22
Wow thanks for getting back so fast.

Here is that command:

```
root@grml / # lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME                   TYPE FSTYPE       SIZE FSAVAIL FSUSE% LABEL               MOUNTPOINT
sda                    disk              9.1T
&#9492;&#9472;sda1                 part LVM2_member  9.1T
  &#9492;&#9472;vgcardboard-root   lvm  ext4        10.9T    8.7T    14%                     /media/RESCUE
sdb                    disk              1.8T
&#9500;&#9472;sdb1                 part vfat         512M
&#9500;&#9472;sdb2                 part                1K
&#9492;&#9472;sdb5                 part LVM2_member  1.8T
  &#9500;&#9472;vgcardboard-root   lvm  ext4        10.9T    8.7T    14%                     /media/RESCUE
  &#9492;&#9472;vgcardboard-swap_1 lvm  swap         976M
sdc                    disk iso9660     29.1G                grml64-full 2022.11
&#9500;&#9472;sdc1                 part iso9660      855M       0   100% grml64-full 2022.11 /usr/lib/live/mount/medium
&#9492;&#9472;sdc2                 part vfat           4M                GRML
root@grml / #
```

Hope that helps for the next thing to do.

Thank you.

-Raymond Day

---

### Post by Raymond Day on 2023-11-22
I used LVM because wanted a 10TB on it and just could not get it to boot from it. But it does boot on a 2TB so installed on it and set it all up and was working good till had to reboot.

With LVM I could add the 10TB drive.

-Raymond Day

---

### Post by Raymond Day on 2023-11-23
[Went to this webpage]("https://phoenixnap.com/kb/grub-rescue") and I got to the part were it says to do "sudo grub-install -root-directory=/mnt/ /dev/sda" but I put at the end /dev/sdb because that is were the boot 2TB SSD is.

Here is what I did on a live Ubuntu Desktop 22.04.3 LTS one.

```
root@ubuntu:~# mount /dev/sdb1 /mnt
root@ubuntu:~# mount --bind /dev /mnt/dev &&
>
> mount --bind /dev/pts /mnt/dev/pts &&
> mount --bind /proc /mnt/proc &&
> mount --bind /sys /mnt/sys
root@ubuntu:~# grub-install -root-directory=/mnt/ /dev/sdb
grub-install: invalid option -- 'r'
Try 'grub-install --help' or 'grub-install --usage' for more information.
root@ubuntu:~# sudo grub-install -root-directory=/mnt/ /dev/sdb
grub-install: invalid option -- 'r'
Try 'grub-install --help' or 'grub-install --usage' for more information.
root@ubuntu:~# sudo grub-install -root-directory=/mnt/ /dev/sdb -r
grub-install: invalid option -- 'r'
Try 'grub-install --help' or 'grub-install --usage' for more information.
root@ubuntu:~# cd /mnt
root@ubuntu:/mnt# ls -l
total 852
drwxr-xr-x   2 root root   4096 Nov 23 08:11 bin
drwxr-xr-x  21 root root   4580 Nov 23 10:08 dev
dr-xr-xr-x 325 root root      0 Nov 23 10:05 proc
dr-xr-xr-x  13 root root      0 Nov 23 10:05 sys
-rwxr-xr-x   1 root root 865768 Nov 23 08:12 zsh
root@ubuntu:/mnt#
```

Took this screen shot too it's wants me to install UEFI firmware but this don't have the BIOS for that it's to old. I did install a Ubuntu old one and then updated it to 22.04 and it worked on the 2TB. But like I said after I added the 10TB to the LVM and rebooted that when it goes to the grub rescue here is the screen shot of it saying that.

[https://photos.app.goo.gl/L7fKGWczBPANfrEKA]("https://photos.app.goo.gl/L7fKGWczBPANfrEKA")

Not sure if that image will work but it's a link to my Google drive.

In the grub rescue I can do a LS on all the things it list and then do a LS on all the names and none came up says file system unknow.

Like this:

"ls (lvm/vgcardboard-root)"

It will come back with "not found"

How do I fix this?

-Raymond Day

---

### Post by oldfred on 2023-11-23
I do not use LVM, but it is my understanding that you do not want to span across drives. If one drive fails, you lose all data on both drives.
Either way you need another large drive for backups.

With gpt you have to have either an ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot.
Both should be near beginning of large drives. I typically added both as first two partitions when first converting from BIOS to UEFI, so all I had to do was reinstall grub, not totally redo drive.
The bios_grub is unformatted partition of 1GB with bios_grub flag if using gparted. If using gdisk, it it code ef01. The actual GUID is some very long string that identifies partition type.

---

### Post by Raymond Day on 2023-11-24
I went in the BIOS and can only switch the drive to **Legacy** and **Native** no UEFI to pick.

Guess that is what is wrong.

A boot-repair will just come back saying "The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware" I did put it to **Native** and still does not boot.

This BIOS don't see the right size of the 10TB drive it sees it as a 1204.7 GB drive. Not 10 TB.

So I think it's 2 problem's. Updated the BIOS too. Not sure if they are any more updates for it.

This motherboard only has USB 2.0 but does have 2 SATA ports I guess they just came out when this board did.

-Raymond Day

---

### Post by oldfred on 2023-11-24
Did you change to gpt?
And add a bios_grub partition at beginning of drive for BIOS boot or an ESP for UEFI boot?
Does UEFI/BIOS see drive correctly in settings?

---

### Post by Raymond Day on 2023-11-25
I got it working now. I put a 2TB SSD on it and installed Ubuntu and then did a symbolic link to the 10 TB HDD and it's still booting from the 2TB now and can use the 10TB from a link to it. Junk can not install it on a 10TB drive.

I had to format the 10TB drive with **pvremove /dev/sdb1 --force --force** command.

So don't need help any more. It's a old BIOS and can only work with a boot drive not much bigger then 2TB.

I made my own case for it long ago just the same size as the mini-itx and cut out the back ports just for that motherboard. So be to hard to get a new motherboard for it that would support booting from a 10TB HDD.

Thanks for your help one this.

-Raymond Day

---

### Post by TheFu on 2023-11-27
Please mark the thread as SOLVED using the thread tools button.

---

