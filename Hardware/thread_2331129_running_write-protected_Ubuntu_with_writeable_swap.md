---
title: "running write-protected Ubuntu with writeable swap"
date: 2016-07-18
forum: Hardware
---

### Post by haplorrhine on 2016-07-18
Naturally I chose to boot from my Kanguru FlashTrust pendrive when my hard drive failed.  I realized that the write-protection switch makes my system incorruptible as I surf the Internet from wherever.  The problem is that the swap is write-protected too, so I doubt my laptop can access it.  To do video chats on it, either I need a second pendrive for the swap, or I need to make Ubuntu read-only in some other way.  I appreciate any help.  Perhaps there should be a read-only version with every release.  :)

---

### Post by sudodus on 2016-07-19
There is a read-only version with every release. If you clone the iso file to a USB drive, it is read only. But that is not what you want. You want a switch to have a system that can turn on and off persistence and swap.

I think the safest and simplest method is to have two pendrives (in other words, the way you are already using).

Another method is to have a ***persistent live*** system. When you boot, you can select 'live-only' alias read-only, and 'persistent live' alias read-write. Such systems are normally not using swap, but you can add a swap partition and select 'swapon' or 'swapoff'.

See for example the following links,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by haplorrhine on 2016-07-20
Thank you for the links.  On the first attempt Cheese made my system crash before video could display, but the second time it worked.  That means I could install video chat software and then resume the write-protection, but I'll try Google Plus first.

---

### Post by haplorrhine on 2016-07-21
I might need to make a (persistent) live pendrive from another (basic) live pendrive.  My new and only laptop with a disk drive is having repeated hard drive failures that force me to reinstall the system and re-copy the iso back to the hard drive.

---

### Post by sudodus on 2016-07-21
It should work that way to make a persistent live drive.
I hope you find the cause of the problems with your hard disk drive.

Good luck :-)

---

### Post by haplorrhine on 2016-07-21
Persistence option removed from startup disk creator.  [http://askubuntu.com/questions/772093/where-is-the-persistent-option-for-startup-disk-creator-in-16-04](http://askubuntu.com/questions/772093/where-is-the-persistent-option-for-startup-disk-creator-in-16-04)
Fortunately 12.04 is still available.

For those without a harddrive, you can set the Firefox download folder to another flashdrive in "Preferences".

I made a supposed persistence 16.04 with 2GB from a live 12.04, but it failed to retain the google-talkplugin even though the write-protection switch was off.  That it installed at all makes me wonder whether I needed a persistence version.

---

### Post by haplorrhine on 2016-08-01
Would a persistent live drive be more or less secure than a basic install?  It isn't password protected.

Maybe I regret this post, but perhaps it's extra flashdrives used for storage that aren't secure, as I'm wondering why I could add a new file to a pendrive that was r-w (chmod, non-recursive).

---

### Post by sudodus on 2016-08-01
There are different aspect of security:

- attacks via the internet

- physical access (theft, robbery)

A persistent live drive can be secure against attacks via the internet, but not via physical access.

An installed system with LVM and disk encryption is rather secure against physical access, if you have a good password. It is no more secure than a regular installed system against attacks via the internet connection, and you can use the same methods to make it more secure.

If your problem is the swap, and you have enough RAM to run the application programs you need, you can turn off swap by removing the line about swap in the file **/etc/fstab**. But there are some files, that an installed system wants to access and write to.

If you have enough RAM, maybe it is possible to get what you want with a ram drive. You can try with the boot option **toram**.

I think it would be easier to use persistence. One alternative is a persistent live drive made with ***mkusb***. Another alternative might be 'Simple persistence' - a boot drive, that is cloned from an Ubuntu [flavour] iso file, and a separate pendrive with partitions for persistence.

[Persistent live systems](https://help.ubuntu.com/community/mkusb/#Persistent_live_systems)

If you start by overwriting the whole device to become a boot drive with zeros, and clone from the iso file, then you can be 100% sure that no personal data reside in the boot drive. And you can have separate drives for persistence to run different tasks (banking, chatting, browsing ...). Probably you need no persistence at all for banking, which would make it safer.

---

### Post by CatKiller on 2016-08-01
You can set each partition of a normal install to be read-only at mount time as an option in /etc/fstab. In addition to writeable swap, you'll also likely need a writeable /tmp, and probably /var/log too. You can create these as temporary filesystems that only live in RAM, though, that are destroyed each boot, again with /etc/fstab.

Edit: if you make / read-only by this method, you'll need a way to make it writeable again. I can't remember if you can do so from single-user mode, but the easiest way would be if you could mount the partition on another system to edit /etc/fstab. Since it's a thumb drive, that shouldn't be a problem.

---

### Post by haplorrhine on 2016-08-12
> **CatKiller said:**
> You can set each partition of a normal install to be read-only at mount time as an option in /etc/fstab. In addition to writeable swap, you'll also likely need a writeable /tmp, and probably /var/log too. You can create these as temporary filesystems that only live in RAM, though, that are destroyed each boot, again with /etc/fstab.

Is that how Ubuntu Live stores temporary files, by mounting /tmp in RAM or other volatile memory?
I will try it when I boot a Live session on a system with a harddrive.

In the name of preserving memory, is there something more specific than *apt-get update* that I can use after: *add-apt-repository "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe"* ?

---

### Post by CatKiller on 2016-08-12
> **haplorrhine said:**
> Is that how Ubuntu Live stores temporary files, by mounting /tmp in RAM or other volatile memory?

I don't know.

> 
In the name of preserving memory, is there something more specific than *apt-get update* that I can use after: *add-apt-repository "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe"* ?

I don't know what you mean by preserving memory, or by more specific.

apt-get update refreshes the list of available packages. You will always need to do this after making changes to the list of repositories.

---

### Post by sudodus on 2016-08-12
> **haplorrhine said:**
> Is that how Ubuntu Live stores temporary files, by mounting /tmp in RAM or other volatile memory?
I will try it when I boot a Live session on a system with a harddrive.

Normally /tmp is a directory in the root partition. You have to change the configuration to make it reside in RAM, either /tmp or the whole root partition or some [other] parts of it.
> 
In the name of preserving memory, is there something more specific than *apt-get update* that I can use after: *add-apt-repository "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe"* ?

+1 to CatKiller's reply.

---

### Post by haplorrhine on 2016-10-05
Now I have a related question regarding the physical security of the flashdrive.  At the start I should have taken a checksum of the mounted pendrive via the /dev directory to see whether it was consistent.  Anyway, I'm wondering what they should look like from GParted.  My non-P 16.04 image appears as one fat partition in GParted, but my P 16.04 and non-P 12.04 each appear as two small partitions (one fat and I believe the other swap?) amidst a lot of unallocated space.

---

### Post by sudodus on 2016-10-06
In order to give good replies, we need more details. Please post the output of the following commands (with the flash drives connected)

```
df -h
sudo lsblk -fm
sudo parted -ls
```

---

### Post by haplorrhine on 2016-10-08
Here's the GParted breakdown of P 16.04 and non-P 16.04.  12.04 looks similar to the former.  The were read from Kangurua Flash Trust flashdrives with write protection on.

[TABLE="width: 500"]
[TR]
[TD][SIZE=1]Partition
[/SIZE][/TD]
[TD][SIZE=1]file system
[/SIZE][/TD]
[TD][SIZE=1]mount point
[/SIZE][/TD]
[TD][SIZE=1]size
[/SIZE][/TD]
[TD][SIZE=1]used
[/SIZE][/TD]
[TD][SIZE=1]unused
[/SIZE][/TD]
[TD][SIZE=1]flags
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]/dev/sdc1
[/SIZE][/TD]
[TD][SIZE=1]unknown
[/SIZE][/TD]
[TD][SIZE=1]Ubuntu 16.04 LTS amd64
[/SIZE][/TD]
[TD][SIZE=1]4.00 KiB
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]unallocated
[/SIZE][/TD]
[TD][SIZE=1]unallocated
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]1.38 GiB
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]/dev/sdc2
[/SIZE][/TD]
[TD][SIZE=1]fat16
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]2.31 MiB
[/SIZE][/TD]
[TD][SIZE=1]2.30 MiB
[/SIZE][/TD]
[TD][SIZE=1]8.00 KiB
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]unallocated
[/SIZE][/TD]
[TD][SIZE=1]unallocated
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]27.43 GiB
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]/dev/sdb1 (key)
[/SIZE][/TD]
[TD][SIZE=1]fat32
[/SIZE][/TD]
[TD][SIZE=1]/media/ubuntu/DF50-4156
[/SIZE][/TD]
[TD][SIZE=1]720 GiB
[/SIZE][/TD]
[TD][SIZE=1]1.42 GiB
[/SIZE][/TD]
[TD][SIZE=1]5.78 GiB
[/SIZE][/TD]
[TD][SIZE=1]boot
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[/TR]
[/TABLE]


I prepended a custom column since I did them each separately.  Given that df and lsblk yielded almost the same results each time—some changes in the df "Used" column for some tmpfs entries—I excluded all but the entries for the flashdrives.

[TABLE="width: 500"]
[TR]
[TD][SIZE=1]custom
[/SIZE][/TD]
[TD][SIZE=1]Filesystem
[/SIZE][/TD]
[TD][SIZE=1]Size
[/SIZE][/TD]
[TD][SIZE=1]Used
[/SIZE][/TD]
[TD][SIZE=1]Avail
[/SIZE][/TD]
[TD][SIZE=1]Use%
[/SIZE][/TD]
[TD][SIZE=1]Mounted on
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]P 16
[/SIZE][/TD]
[TD][SIZE=1]/dev/sdc1
[/SIZE][/TD]
[TD][SIZE=1]1.4G
[/SIZE][/TD]
[TD][SIZE=1]1.4G
[/SIZE][/TD]
[TD][SIZE=1]0
[/SIZE][/TD]
[TD][SIZE=1]100%
[/SIZE][/TD]
[TD][SIZE=1]/media/ubuntu/Ubuntu 16.04 LTS amd64
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]nP 12
[/SIZE][/TD]
[TD][SIZE=1]/dev/sdc1
[/SIZE][/TD]
[TD][SIZE=1]758M
[/SIZE][/TD]
[TD][SIZE=1]758M
[/SIZE][/TD]
[TD][SIZE=1]0
[/SIZE][/TD]
[TD][SIZE=1]100%
[/SIZE][/TD]
[TD][SIZE=1]/[SIZE=1]media/ubuntu/Ubuntu 12.04.5 LTS amd64[/SIZE][/SIZE]
[/TD]
[/TR]
[TR]
[TD][SIZE=1]nP 16
[/SIZE][/TD]
[TD][SIZE=1]/dev/sdb1
[/SIZE][/TD]
[TD][SIZE=1]7.2G
[/SIZE][/TD]
[TD][SIZE=1]1.5G
[/SIZE][/TD]
[TD][SIZE=1]5.8G
[/SIZE][/TD]
[TD][SIZE=1]20%
[/SIZE][/TD]
[TD][SIZE=1]/[SIZE=1]media/ubuntu/DF50-4156[/SIZE][/SIZE]
[/TD]
[/TR]
[/TABLE]

[SIZE=1][/SIZE][TABLE="width: 500"]
[TR]
[TD][SIZE=1]custom
[/SIZE][/TD]
[TD][SIZE=1]NAME
[/SIZE][/TD]
[TD][SIZE=1]FSTYPE
[/SIZE][/TD]
[TD][SIZE=1]LABEL
[/SIZE][/TD]
[TD][SIZE=1]UUID
[/SIZE][/TD]
[TD][SIZE=1]MOUNT POINT
[/SIZE][/TD]
[TD][SIZE=1]SIZE
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]P 16
[/SIZE][/TD]
[TD][SIZE=1]sdc
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]Ubuntu 16.04 LTS amd64
[/SIZE][/TD]
[TD][SIZE=1]2016-04-20-22-29-52-00
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]7.2G
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]sdc1
[/SIZE][/TD]
[TD][SIZE=1]iso9660
[/SIZE][/TD]
[TD][SIZE=1][SIZE=1]Ubuntu 16.04 LTS amd64[/SIZE][/SIZE]
[/TD]
[TD][SIZE=1][SIZE=1]2016-04-20-22-29-52-00[/SIZE][/SIZE]
[/TD]
[TD][SIZE=1]/media/ubu
[/SIZE][/TD]
[TD][SIZE=1]1.4G
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]sdc2
[/SIZE][/TD]
[TD][SIZE=1]vfat
[/SIZE][/TD]
[TD][SIZE=1][SIZE=1]Ubuntu 16.04 LTS amd64[/SIZE][/SIZE]
[/TD]
[TD][SIZE=1]B1F5-0A13
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]2.3M
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]nP 12
[/SIZE][/TD]
[TD][SIZE=1]sdc
[/SIZE][/TD]
[TD][SIZE=1]iso9660
[/SIZE][/TD]
[TD][SIZE=1]Ubuntu 12.04.5 LTS amd64
[/SIZE][/TD]
[TD][SIZE=1]2014-08-07-21-07-49-00
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]7.2G
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]sdc1
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1][SIZE=1]Ubuntu 12.04.5 LTS amd64[/SIZE][/SIZE]
[/TD]
[TD][SIZE=1][SIZE=1]2014-08-07-21-07-49-00[/SIZE][/SIZE]
[/TD]
[TD][SIZE=1]/media/ubu
[/SIZE][/TD]
[TD][SIZE=1]758M
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]sdc2
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1][SIZE=1]Ubuntu 12.04.5 LTS amd64[/SIZE][/SIZE]
[/TD]
[TD][SIZE=1][SIZE=1]2014-08-07-21-07-49-00[/SIZE][/SIZE]
[/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]2.1M
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]nP 16
[/SIZE][/TD]
[TD][SIZE=1]sdb
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]7.2G
[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]sdb1
[/SIZE][/TD]
[TD][SIZE=1]vfat
[/SIZE][/TD]
[TD][SIZE=1]
[/SIZE][/TD]
[TD][SIZE=1]DF50-4156
[/SIZE][/TD]
[TD][SIZE=1]/media/ubuntu/DF5
[/SIZE][/TD]
[TD][SIZE=1]7.2G
[/SIZE][/TD]
[/TR]
[/TABLE]
[SIZE=1][/SIZE]
parted output, all:
Warning: Unable to open /dev/sd* read-write (Read-only file system).  /dev/sd* has been opened read-only.

parted output, P 16 and nP 12:
Warning: the driver description says the physical block size is 2048 bytes, but Linux says it is 512 bytes.

parted output, all:

Model: Kanguru Flash Trust (scsi)
Disk /dev/sdc: 7734 MB
Sector size (logical/physical): 512B/512B
Partition Table: unknown (or msdos for non-persistent 16.04)
Disk Flags:

parted output, nP 16:

[TABLE="width: 500"]
[TR]
[TD]Number
[/TD]
[TD]Start
[/TD]
[TD]End
[/TD]
[TD]Size
[/TD]
[TD]Type
[/TD]
[TD]File system
[/TD]
[TD]Flags
[/TD]
[/TR]
[TR]
[TD]1
[/TD]
[TD]1049kB
[/TD]
[TD]7734MB
[/TD]
[TD]7733MB
[/TD]
[TD]primary
[/TD]
[TD]fat32
[/TD]
[TD]boot
[/TD]
[/TR]
[/TABLE]

---

### Post by haplorrhine on 2016-10-08
I almost forgot the footnote I added while copying the lsblk output.

all MODE is brw-rw----.
all GROUP is disk.
all OWNER is root.

---

### Post by sudodus on 2016-10-08
The content in the iso9660 partitions '/dev/sdc1' are read-only. I am rather sure they are images of the iso file(s).

The content in the FAT partitions '/dev/sdc2' can be written to, but they are very small, and typically only used for booting.

nP16 has a different partition table, was made with another tool. 'Everything' is contained in the FAT partition, and it can be written to, at least when booted with persistence.

I am not sure that I understand what and why you ask. Are you concerned about the ***security***? Do you want to be sure that your system can not be written to? In that case you should have a ***live-only*** system (not a persistent live system, not an installed system).

-o-

You chose a difficult way with tables. It is even likely, that you have introduced some error when creating the tables. It would have been much easier to simply copy and paste from the terminal window to the editing box (here). If you wish, you can remove lines or words afterwards (to make it clean). Finally, put it within CODE tags. If you press the button 'Reply with quote' you will see how I did it.

1. live drive cloned by mkusb from Ubuntu Xenial amd64 mini.iso (live-only)
```

$ sudo lsblk -fm /dev/sdd
NAME   FSTYPE  LABEL    UUID                                 MOUNTPOINT NAME    SIZE OWNER GROUP MODE
sdd    iso9660 CDROM    2016-07-19-17-20-59-00                          sdd    29,8G root  disk  brw-rw----
&#9500;&#9472;sdd1 iso9660 CDROM    2016-07-19-17-20-59-00                          &#9500;&#9472;sdd1   49M root  disk  brw-rw----
&#9492;&#9472;sdd2 vfat    Firmware 17BE-88B6                                       &#9492;&#9472;sdd2    6M root  disk  brw-rw----

```
2. live drive cloned by mkusb from Ubuntu Xenial amd64 iso file, ubuntu-16.04.1-desktop-amd64.iso (live-only)
```

$ sudo lsblk -fm /dev/sdd
NAME   FSTYPE  LABEL                    UUID                                 MOUNTPOINT NAME    SIZE OWNER GROUP MODE
sdd    iso9660 Ubuntu 16.04.1 LTS amd64 2016-07-19-21-27-51-00                          sdd    29,8G root  disk  brw-rw----
&#9500;&#9472;sdd1 iso9660 Ubuntu 16.04.1 LTS amd64 2016-07-19-21-27-51-00                          &#9500;&#9472;sdd1  1,4G root  disk  brw-rw----
&#9492;&#9472;sdd2 vfat    Ubuntu 16.04.1 LTS amd64 0F7B-9366                                       &#9492;&#9472;sdd2  2,3M root  disk  brw-rw----

```
3. persistent live drive created by mkusb from Ubuntu Xenial amd64 iso file, ubuntu-16.04.1-desktop-amd64.iso (selected 67% for persistence)
```

$ sudo lsblk -fm /dev/sdd
NAME   FSTYPE  LABEL                    UUID                                 MOUNTPOINT NAME    SIZE OWNER GROUP MODE
sdd                                                                                     sdd    29,8G root  disk  brw-rw----
&#9500;&#9472;sdd1 ntfs    usbdata                  2D87375C3158C661                                &#9500;&#9472;sdd1  9,3G root  disk  brw-rw----
&#9500;&#9472;sdd2                                                                                  &#9500;&#9472;sdd2    1M root  disk  brw-rw----
&#9500;&#9472;sdd3 vfat    ubu1604164               C372-B196                                       &#9500;&#9472;sdd3  122M root  disk  brw-rw----
&#9500;&#9472;sdd4 iso9660 Ubuntu 16.04.1 LTS amd64 2016-07-19-21-27-51-00                          &#9500;&#9472;sdd4  1,4G root  disk  brw-rw----
&#9492;&#9472;sdd5 ext4    casper-rw                0e2b6666-21d0-4e33-9baa-48a5e0d07e66            &#9492;&#9472;sdd5   19G root  disk  brw-rw----


```

---

### Post by haplorrhine on 2016-10-17
Than you very much sudodus.  I take it that even the boot partition is unwriteable because of the way it is mounted on a live-only system?

It's good to know that there was nothing obviously abnormal about their partitioning.  I have rewritten the iso files to the pendrives, and I did checksums this time.  You need sudo privileges, but it is consistent, at least if you hash the entire pendrive (sd* without the appended digits).  I was struck that the md5 hash value of my non-persistent 16.04 pendrive changed after I rewrote the image to it.  I rewrote it again two more times without seeing the hash value change, but that could be because I didn't write to it enough times to kill enough flash memory cells to change the partition size and thus the hash value.  However I wrote the same image to another ~8GB Kanguru FlashTrust and received a unique hash value for that pendrive.
I have a secondary, unconnected, physically isolated laptop that I'm using to write these images to the flashdrives.  Everything was done exactly the same and so the end product should have been the same unless enough flash memory cells had died.

---

### Post by sudodus on 2016-10-17
When you clone the iso file to a USB pendrive each byte will cloned exactly as it is. So if you extract it (exactly the cloned number of bytes) into another file, and run md5sum on that file, you will get the same result as on the original iso file. But if you extract also the unallocated data 'behind' the cloned iso file, you will get a bigger file, and of course another md5sum.

When you know how cloned iso files work, and that the file system is read-only by its nature (ISO 9660), you can rely on such USB drives, that they are not changed by any malware.

---

### Post by haplorrhine on 2016-11-09
How would I clone a bootable pendrive onto a DVD-R?  Problems might arise if it tries to use swap stored on a read-only DVD.  I'm trying anyway.  12.04, but not 16.04, comes with growisofs (code below).  Unfortunately it consistently gives an error message at 99% (below that) whether I use /dev/sr0, dvd, or dvdrw.

growisofs -Z /dev/sr0=/dev/sdx

: - [ WRITE@LBA=231020h failed with SK=5h/END OF USER AREA ENCOUNTERED ON THIS TRACK]: Input/output error
: - ( write failed: Input/output error
/dev/sr0: flushing cache
/dev/sr0: updating RMA
/dev/sr0: closing session
/dev/sr0: reloading tray

I will try using genisoimage to generate an iso image from the pendrive, then writing that iso to the disk.  I might even try cat /dev/sdx > /dev/sd0.

---

### Post by sudodus on 2016-11-09
You can 'burn an image' like you do with an iso file to make a boot DVD. But if you try to have a swap partition or file on a read-only device, you will find that it cannot be used.

-o-

I do not understand what you are trying to do. Are you trying to add some program package and create a 're-spin' or custom linux boot system? Why?

If you want a read-only system, you can make a cloned copy of a standard Ubuntu iso file. You can burn an image to a DVD disk, or clone it to a USB pendrive. In both cases you will get a *read-only ISO 9660 file system*, and nothing will be stored after you shut down or reboot the computer (unless you make an effort and store a file in *another* drive).

---

### Post by C.S.Cameron on 2016-11-09
One persistence method not mentioned above, is to make a Live, non Persistent drive, copy blank casper-rw persistence file over to it.
When booting, press F6 and type "<space>persistent".
That session of Ubuntu will be persistent everything will be saved.
Of course the drive will only boot Live, (without changes), until the next time you boot with " persistent".

I recall once trying to figure out how to make the casper-rw file read only but did not have much luck, have not seen it done since.

---

### Post by haplorrhine on 2016-11-09
> **sudodus said:**
> You can 'burn an image' like you do with an iso file to make a boot DVD. But if you try to have a swap partition or file on a read-only device, you will find that it cannot be used.

Where is this option?  There is no "write to disc" option in the right-click menu when I right-click on the /dev/sd* file.

> **sudodus said:**
> I do not understand what you are trying to do. Are you trying to add  some program package and create a 're-spin' or custom linux boot system?  Why?

If you want a read-only system, you can make a cloned copy of a standard  Ubuntu iso file. You can burn an image to a DVD disk, or clone it to a  USB pendrive. In both cases you will get a *read-only ISO 9660 file system*, and nothing will be stored after you shut down or reboot the computer (unless you make an effort and store a file in *another* drive). 

I'm using un-updated 12.04, so I'll download growisofs for 16.04 and try that next.

There are two things I want to try, but there's a more basic problem. The flashdrive contents will not write to the optical disk regardless, regardless of whether it is basic Ubuntu Live (partition resized to 2000 to 4000 megabytes) or a Ubuntu Live partition alongside an ext partition.  I'm considering two options:

I could make a persistence live system, then add files or install packages on it, then write the flashdrive contents to an optical disk (DVD-R).  I might have to make it mount as read-only (/etc/fstab) or else errors could occur while running it from a read-only optical disk, which is why I'm trying a different approach first.
I used Startup Disk Creator to write the iso to the flashdrive, then I resized the resulting fat32 partition down to 2000 megabytes.  Next, I added an ext2 partition of 2000 megabytes and added files to that partition.  It boots fine and I'm able to view the ext2 partition.

---

### Post by sudodus on 2016-11-09
There are several tools. I use ***k3b*** to write CDs and DVDs.

-o-

I think a persistent live system is made such that it needs write permissions to the casper-rw file or partition. It is much more complicated to create a custom iso file with your tweaks and extra program packages. But it is possible, if you really want to spend the time to learn how to do it. See for example these links:

[9w/Manual](https://help.ubuntu.com/community/9w/Manual)

[willhaley.com/blog/create-a-custom-debian-live-environment](http://willhaley.com/blog/create-a-custom-debian-live-environment/)

---

### Post by C.S.Cameron on 2016-11-09
There are tools such as Remastersys, (Pinguy Builder and Respin are live forks), that allow you to modify Ubuntu, update the filesystem.squashfs and rebuild the iso.
you can then run a Live customized O/S with or without using persistence.

My experience is that running off a CD or DVD is much slower that off of USB, but this might no longer be true with lots of RAM.

or one could keep a copy of casper-rw in the Home folder update it as required and use it to overwrite the casper-rw file in the root.

---

### Post by haplorrhine on 2016-11-19
It looks like Remastersys is a more well-known program, and 9w is mostly for writing iso images, not editing them.  Is this the official remastersys website and repository?

deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) precise main
from askubuntu [http://askubuntu.com/questions/133272/how-do-i-install-remastersys](http://askubuntu.com/questions/133272/how-do-i-install-remastersys)

---

### Post by sudodus on 2016-11-19
Yes Remastersys is well known, but it is no longer maintained. You need to find one of the forks, if you want to use the tool on new versions of Ubuntu.

Yes, 9w itself is cloning iso files and other images and extracting tarballs, but my references show how 9w was *made* according to Will Haley's blog post, and it is a method that you could use for your purpose.

---

### Post by haplorrhine on 2017-01-28
I was working on encryption for a while, but I'm back to this again.  Indeed remastersys was abandoned long ago and therefore won't run on recent releases of Ubuntu without significant accomodation.  LinuxRespin works on 16.04 with only minor accomodations.  [https://github.com/ch1x0r/LinuxRespin/issues/2](https://github.com/ch1x0r/LinuxRespin/issues/2)

I got it installed on Ubuntu Live, but now I am curious as to whether a simple backup would work for a post-install setup of Ubuntu.  Won't a simple backup only run on the machine it was installed on, or are all the necessary drivers still there so that the backup could be booted on any machine?  I tried making a backup while running Ubuntu Live, and it gave some errors regarding the kernel and cryptsetup.

---

### Post by sudodus on 2017-01-29
What do you mean by 'a simple backup'? There are many backup methods and tools.

-o-

In general, an installed Ubuntu system is portable between computers, particularly if you avoid proprietary drivers. But a live or persistent live system is more portable (because the the driver issue, that you mentioned).

---

### Post by haplorrhine on 2017-01-29
Is there a section of the debian-handbook I should read for background knowledge on backups?  Since the drivers exist as kernel modules, perhaps I should read [Compiling (8.10)]("https://www.debian.org/doc/manuals/debian-handbook/sect.kernel-compilation.en.html") and [Installing a Kernel (8.11)]("https://www.debian.org/doc/manuals/debian-handbook/sect.kernel-installation.en.html")?  

Here is the error message I get in Ubuntu Live 16.04.
ubuntu@ubuntu:~$ sudo respin backup custom.iso
[...]
Creating a new initial ramdisk for the live system
cryptsetup: WARNING: failed to detect canonical device of overlay
cryptsetup: WARNING: could not determine root device from /etc/fstab
Copying your kernel and initrd for the livecd
cp: cannot stat '/boot/vmlinuz-4.4.0-21-generic': No such file or directory
Missing valid kernel. Exiting

---

### Post by sudodus on 2017-01-29
It seems to me that your tool cannot manage the encryption.

One method is to clone the whole drive with ***Clonezilla***. See [http://clonezilla.org](http://clonezilla.org)

You can store the backup as a compressed image (a directory with a number of files). But to be sure, you should restore from the compressed image to a target drive (another drive, that you have for this particular purpose). The target drive must be of exactly the same size as the source drive or bigger for Clonezilla to work.

---

### Post by haplorrhine on 2017-01-29
I'm also trying uck (Ubuntu Customization Kit), run fro the terminal as uck-gui, but it won't read the iso file from my flashdrive.  The file gives the correct sha256sum, so it is not corrupted.
The file "does not exist" with the version of uck available in the [http://archive.ubuntu.com/ubuntu/pool/multiverse/](http://archive.ubuntu.com/ubuntu/pool/multiverse/) archive.
uck_2.0.0-beta1 gives the same error message whereas beta3 says it "does not seem to be a valid ISO9660 image".

I would prefer something that I can boot from a DVD-R, so I don't find myself resizing the current system to temporarily fit a second system alongside it.

---

### Post by sudodus on 2017-01-30
Let us hope someone who knows uck will see this and can help you.

---

### Post by haplorrhine on 2017-01-30
I'm back to respin (remastersys) and I would like immediate hep.

It doesn't encounter the same error on an installed system, but the default options (sudo respin backup) do not create a sizeable iso file.  It looks like what I want to do is "sudo respin dist iso xxx.iso", which must be preceded by "sudo respin dist cdfs", which apparently gets rid of all user files.  [http://askubuntu.com/questions/832425/how-to-make-iso-of-current-installation-using-respin](http://askubuntu.com/questions/832425/how-to-make-iso-of-current-installation-using-respin)
Now I'm worried about losing the user files since that could include a lot of necessary packages that were carelessly installed from the home directory.  Unfortuantely dpkg seems to lack an easy "deisntall" option that would allow me to reinstall these packages with the --root option.  I really don't want to shutdown what I've done so far, for this laptop will not retain an uncorrupted install of Ubuntu and forces me to reinstall repeatedly.  I'm going to try upgrading grub after this.

One laptop has no harddrive to install to, and on the other no install persists.  :P  :D

It appears that remove is actually what I needed even though what I read had distinguished deinstall from remove.  I used dpkg -r <package-name>, and I was able to move the config files and reinstall, but I want to be sure they're installed as root.  When I enter "sudo dpkg -i <respin-deb-file>", the output ends in "/usr/bin/mandb: fopen /var/cache/man/20321: Permission denied" even though respin and its man page seem to work afterward.

/edited to replace a query with the solution/  If the final output says your iso "is 36K in size" or "properties" says your iso is 34.8kB in size, then you need to install syslinux-utils and isolinux.
[URL="http://askubuntu.com/questions/732953/remastersys-creating-36k-iso-files-14-10-15-04-15-10?rq=1"]http://askubuntu.com/questions/732953/remastersys-creating-36k-iso-files-14-10-15-04-15-10?rq=1

[/URL]It looks like the burned DVDs are not booting, so there's still something wrong.  Incidentally, it's confusing testing the DVDs since I am booting into identical systems regardless.

/another append/

new goal

Is there any way to partition a DVD-R?  I've successfully booted from a bootable pendrive with a second partition containing iso files, but using dd or genisoimage to copy the pendrive to a DVD did not result in a bootable DVD.  Furthermore, I'm unaware of how to burn a DVD with multiple partitions, and I have no way to resize the bootable partition after it has been burned to the DVD-R.
My goal was to create a self-replicating DVD from which I could create bootable flashdrives from which I could burn more of said boot disk.  Now I'm uncertain that remastersys/respin can do this, for I would need to create a backup that contains a backup of itself rather than a mere backup with a standard iso file on it.  I will settle for a bootable DVD from which I can create more Live USB sticks with the standard iso image.

---

### Post by haplorrhine on 2017-03-05
Now I want to hash the flashdrives from a Windows system, and I have little Windows experience.  In Ubuntu, since I cannot hash a directory, I hash as root the /dev/sd* file to get a hash of the flashdrive that is consistent as long as the flashdrive contents aren't changed.  I don't know whether I could do this from Windows or whether I would get the same hash value across platforms.  It looks like Windows 7+ has a directory called "Disk Management" or "diskmgmt.msc", but I don't know how to hash in Windows nor do I know whether it has to be a file to be hashed.

---

### Post by sudodus on 2017-03-06
What do you mean by hash - do you mean to create a checksum, for example with md5sum?

In that case, yes, you can do that on the device level. If you want to know that things are really read, you can use ***pv***.

```
sudo add-apt-repository universe   # only in standard Ubuntu

sudo apt-get install pv    # install pv

sudo bash -c 'pv /dev/sdx | md5sum'
```

-o-

Example: I run a persistent live system with Lubuntu in a 16 GB USB3 pendrive.

```
lubuntu@lubuntu:~$ sudo lsblk -fm
NAME   FSTYPE   LABEL                    UUID                                 MOUNTPOINT               NAME     SIZE OWNER GROUP MODE
zram3                                                                         [SWAP]                   zram3  489.9M root  disk  brw-rw----
zram1                                                                         [SWAP]                   zram1  489.9M root  disk  brw-rw----
sr0                                                                                                    sr0     1024M root  cdrom brw-rw----
loop0  squashfs                                                               /rofs                    loop0  842.3M root  disk  brw-rw----
sda                                                                                                    sda     14.9G root  disk  brw-rw----
&#9500;&#9472;sda4 iso9660  Lubuntu 16.04.2 LTS i386 2017-02-16-00-49-38-00               /cdrom                   &#9500;&#9472;sda4   900M root  disk  brw-rw----
&#9500;&#9472;sda2                                                                                                 &#9500;&#9472;sda2     1K root  disk  brw-rw----
&#9500;&#9472;sda5 ext4     casper-rw                6e4b9038-a4d9-4c29-97e9-0073567488e9 /media/lubuntu/casper-rw &#9500;&#9472;sda5     5G root  disk  brw-rw----
&#9500;&#9472;sda3 vfat     usbboot                  66D2-5E85                            /media/lubuntu/usbboot   &#9500;&#9472;sda3   122M root  disk  brw-rw----
&#9492;&#9472;sda1 ntfs     usbdata                  08493C5647C047D7                     /media/lubuntu/usbdata   &#9492;&#9472;sda1   1.3G root  disk  brw-rw----
zram2                                                                         [SWAP]                   zram2  489.9M root  disk  brw-rw----
zram0                                                                         [SWAP]                   zram0  489.9M root  disk  brw-rw----
[COLOR="#0000FF"]lubuntu@lubuntu:~$ sudo md5sum /dev/sda4
d0e847a20181145fdc1206d9f9048e99  /dev/sda4

lubuntu@lubuntu:~$ sudo bash -c 'pv /dev/sda4 | md5sum'
 900MiB 0:00:04 [ 206MiB/s] [========================================================================================================================>] 100%            
d0e847a20181145fdc1206d9f9048e99  -[/COLOR]

[COLOR="#FF0000"]lubuntu@lubuntu:~$ sudo md5sum /dev/sda
7b6f72469ed208845048544ea63185a7  /dev/sda

lubuntu@lubuntu:~$ sudo bash -c 'pv /dev/sda | md5sum'
14.9GiB 0:01:14 [ 206MiB/s] [========================================================================================================================>] 100%            
96cb5c64fb65265006f7b00a639acaf5  -[/COLOR]
lubuntu@lubuntu:~$ 
```

Notice that the checksums match for **/dev/sda4** but not for **/dev/sda**. This is because /dev/sda4 has a read-only file system and is not changed, even though it is mounted. But /dev/sda is the whole active drive, and there are read/write file systems, that are mounted and used. For example the file ~/.bash_history is modified after each command in a terminal window.

***So if you want a reliable checksum, you should boot from another drive, and unmount all partitions on the drive before you create the checksum.***

---

