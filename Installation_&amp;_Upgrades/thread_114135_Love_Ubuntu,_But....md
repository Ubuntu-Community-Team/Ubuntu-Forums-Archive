---
title: "Love Ubuntu, But..."
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by powdercarrot on 2006-01-07
I've installed Ubuntu on a 300GB drive (with XP on another 60GB drive) and when I went through the partioning , I left about 200GB unformatted.  Now I can't seem to format it/partition it through XP or Breezy.  I'd like to get some advice on how to access this unused space which Breezy labels unavailable and XP labels unallocated.  When I try to create a new partition in XP with a right click, the option is not available.

Alternatively, since this is a new install, I could reinstall Breezy on this big drive.  If this is the case, I need to use the drive for Breezy and use about 200GB as a Fat32 partition that can be accessed from XP and Ubuntu.

Thanks in advance!

---

### Post by lrmall01 on 2006-01-07
Does qtparted not see it?

---

### Post by powdercarrot on 2006-01-07
Sees it, but can't change it.

---

### Post by pizzach on 2006-01-08
[QUOTE=powdercarrot]Sees it, but can't change it.[/QUOTE]

Try going through the install process using custome format or whatever it is, making sure to NOT reformat the previous volumes and not actually getting to actually installing (though I don't think it will let you if you format right.)   In my exprerience it will reformat even if it complain a little.  Then reboot.

Let me repeat, make sure to set the program so it doesn't reformat your special partitions.

And please, PLEASE, try to make a more informitive subject title.  That way if other people experience your problem, when they search for it, they will get the right discussion.

---

### Post by powdercarrot on 2006-01-08
I changed the Title.  Thanks for the advice.

---

### Post by powdercarrot on 2006-01-08
Could you give a little more explanation of what you mean by 'custome format' and how to not let it install?

---

### Post by az on 2006-01-08
[QUOTE=powdercarrot]I've installed Ubuntu on a 300GB drive (with XP on another 60GB drive) and when I went through the partioning , I left about 200GB unformatted.  Now I can't seem to format it/partition it through XP or Breezy.  I'd like to get some advice on how to access this unused space which Breezy labels unavailable and XP labels unallocated.  When I try to create a new partition in XP with a right click, the option is not available.

Alternatively, since this is a new install, I could reinstall Breezy on this big drive.  If this is the case, I need to use the drive for Breezy and use about 200GB as a Fat32 partition that can be accessed from XP and Ubuntu.

Thanks in advance![/QUOTE]

You need to use a live cd with a partitioner.  You cannot partition a drive with a mounted partition on it.  Using the live cd will mount the swap, so if you use that, run
sudo swapoff -a

and then run gparted

You can also just boot the install cd and use the command line

CTRL-ALT-F2 after the hardware detection is done and it has loaded the tools. 

The parted command line interface is quite straightforward.

Windows partition tools are no good for drives with linux file systems.

---

### Post by zappa86 on 2006-01-08
When you say you left 200gb unformatted, do you mean unformatted or unpartitioned. Type su and enter your pass. then do a:
```
fdisk /dev/hdX
```
where X is your drive (dont worry about the number after X). (Also if you have a sata drive its /dev/sdX)
then under the fdisk prompt press 'p' and it will list out your partitions. Also you could try
```
sudo gparted
```
this is another program to edit partitions
(if you dont have it then apt-get install gparted)
Also if your drive is mounted you may have trouble editing the partitions. If you have another boot disk you should try that. Finally in windows. The drive will not appear as d:, e:, f:, etc... yet. You need to go to: start->control panel->administration->computer management and from there go to the disk management. Then you can create that partition in windows.

---

### Post by powdercarrot on 2006-01-08
[QUOTE=zappa86]When you say you left 200gb unformatted, do you mean unformatted or unpartitioned. Type su and enter your pass. then do a:
```
fdisk /dev/hdX
```
where X is your drive (dont worry about the number after X). (Also if you have a sata drive its /dev/sdX)
then under the fdisk prompt press 'p' and it will list out your partitions. Also you could try
```
sudo gparted
```
this is another program to edit partitions
(if you dont have it then apt-get install gparted)
Also if your drive is mounted you may have trouble editing the partitions. If you have another boot disk you should try that. Finally in windows. The drive will not appear as d:, e:, f:, etc... yet. You need to go to: start->control panel->administration->computer management and from there go to the disk management. Then you can create that partition in windows.[/QUOTE]

With Manage in XP, I can't change that unallocated space.

---

### Post by powdercarrot on 2006-01-08
[QUOTE=azz]You need to use a live cd with a partitioner.  You cannot partition a drive with a mounted partition on it.  Using the live cd will mount the swap, so if you use that, run
sudo swapoff -a

and then run gparted

You can also just boot the install cd and use the command line

CTRL-ALT-F2 after the hardware detection is done and it has loaded the tools. 

The parted command line interface is quite straightforward.

Windows partition tools are no good for drives with linux file systems.[/QUOTE]

Will I lose all data on the disk that way?

---

### Post by az on 2006-01-08
[QUOTE=powdercarrot]Will I lose all data on the disk that way?[/QUOTE]
Only if you do it wrong.


Parted is very safe.  Whether you are using a graphical frontend to it (Gparted or Qtparted) or just the command line.  It is pretty simple.


dora@dora:~$ sudo parted /dev/hda
Password:
GNU Parted 1.6.21 with HFS shrink patch 16
Copyright (C) 1998 - 2004 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.  See the GNU General Public License for more details.

Using /dev/hda
(parted) print
Disk geometry for /dev/hda: 0.000-19881.914 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031  19147.785  primary   ext3        boot
2      19147.786  19877.299  extended
5      19147.816  19877.299  logical   linux-swap
(parted) ?
  check MINOR                   do a simple check on the filesystem
  cp [FROM-DEVICE] FROM-MINOR TO-MINOR      copy filesystem to another partition  help [COMMAND]                prints general help, or help on COMMAND
  mklabel LABEL-TYPE            create a new disklabel (partition table)
  mkfs MINOR FS-TYPE            make a filesystem FS-TYPE on partititon MINOR
  mkpart PART-TYPE [FS-TYPE] START END      make a partition
  mkpartfs PART-TYPE FS-TYPE START END      make a partition with a filesystem
  move MINOR START END          move partition MINOR
  name MINOR NAME               name partition MINOR NAME
  print [MINOR]                 display the partition table, or a partition
  quit                          exit program
  rescue START END              rescue a lost partition near START and END
  resize MINOR START END        resize filesystem on partition MINOR
  rm MINOR                      delete partition MINOR
  select DEVICE                 choose the device to edit
  set MINOR FLAG STATE          change a flag on partition MINOR

(parted) mkpartfs
Partition type?  primary/logical? logical
File system type?  [ext2]?



You do not need to use sudo from the installer shell.

"print" will show you the free space

"mkpartfs" will ask you what where and what kind of partition to use.  It will default to the free space, I think.  Pretty easy.

Creating a partition out of free space will not touch your current partitions.

However, if you create a partition in the middle of your drive and it renumbers your existing partitoin, you need to edit your /etc/fstab and /boot.grub.menu.list

If you free space is at the end of your drive, never mind.  No problem.

---

