---
title: "mounting internal drives"
date: 2008-11-24
forum: General Help
---

### Post by DOS Chuck on 2008-11-24
First,here's my system: 3Ghz P4,1Gb RAM,2 internal IDE drives(c:,d: ),1 internal RAID drive(h: ),DVD/RW(e: ),CD/RW(f: ) and external USB drive(g: ).
WinXP is on the c: drive and Ubuntu is on the h: drive. I did it that way just in case. Everything works fine except;

It takes an hour after boot for Ubuntu to recognize and mount the USB drive and the CD/RW and the DVD/RW drives. It never does find the 2 internal drives(c: & d: ). I have reinstalled Ubuntu 8.04 3 times(for various reasons) and have the same problem.

Earlier today, it immediately recognized AND mounted the USB,2 IDE drives and the DVD/RW and CD/RW drives. But, it's only done that once.

I wasn't real sure which forum to put this in to get the most suggestions.

Thanks in advance for any help.

---

### Post by vanadium on 2008-11-24
Since Ubuntu Hardy 8.04, non-system partitons are not anymore mounted automatically on startup. They are mounted "on demand", when you click on their icon in the nautilus file manager.

That is probably a good default choice. However, you can still have a partition automatically mounted at startup by including the partition in /etc/fstab yourself.

---

### Post by blazemore on 2008-11-24
Are you comfortable editing fstab?

The file /etc/fstab tells the system what to mount at startup, and when the mount -a command is run.

First, run the command:
```
sudo fdisk -l
```
to list the devices. Look for the one you want to mount, let's assume it's an ext3 or fat32 filesystem on /dev/sda3

To mount it, we create a mount point, lets mount it as /mnt/Share, but you can call it whatever you want:
```
sudo mount /dev/sda3 /mnt/Share
```

If you want to have it mounted every bootup, you can edit the /etc/fstab file:
```

# Partition shared by Windows and Linux
/dev/sda3       /mnt/Share     vfat        none                                  0 0

```

Mount every fstab entry with
```
sudo mount -a
```

Hope this helps!
Google fstab, or type
```
man fstab
```

To find out more info.
Fstab is definately the way to go with this

---

### Post by AlexBellisBrown on 2008-12-21
I just ran :

sudo fdisk -l

And got this

[sudo] password for alex: 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x236d236d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5111    41054076   83  Linux
/dev/sda2   *        6014        6992     7863817+   7  HPFS/NTFS
/dev/sda3            6993        7296     2441880    5  Extended
/dev/sda4            5112        6013     7245315    7  HPFS/NTFS
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Now, i wish to mount sda4 (it shares my music with iTunes). Am i right in thinking i mus add:

# Partition shared by Windows and Linux
/dev/sda4       /mnt/Share     vfat        none                                  0 0

My fstab file looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=847a1504-bae2-409d-9315-d42716453b19 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=dec5d052-2358-4d35-86ad-11c226b44341 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I see two partitions being automatically mounted, Ubuntu (sda1) and the swap (also linux) and the cdrom of course. But, what do all the rest of the numbers mean? like the UUID? Do you have to add that when you add a partition? I would really like to know how to do this "properly", as to be able to help others in the future. Thanks :)

---

### Post by AlexBellisBrown on 2008-12-21
*shameless bump*

---

### Post by AlexBellisBrown on 2008-12-21
Second shameless bump. Come on, where are the Linux partition experts tonight? Some party nobody told me about?? :popcorn:

---

### Post by fjgaude on 2008-12-23
Since the drive is ntfs then I'd put this in /etc/fstab:

```
# Windows Partition
/dev/sda4    /mnt/Share   ntfs   defaults   0   0
```

You can forget the UUIDs for now. If you have troubles with drives changing names then you will have to find the UUID for sda4 and use that in the fstab instead of its name. The use of "defaults" for ntfs filetype may have to be changed. See **man fstab**.

You have made the mountpoint, /mnt/Share, eh?

If not, do this:

```
sudo mkdir /mnt/Share
```

Let us know how you are doing.

---

