---
title: "Partition confusion"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by oopsie on 2009-01-17
I installed Ubuntu for the first time ever a few weeks ago. I've played about with it a bit, and it's pretty cool.

But the problem is, because I was just testing it, I gave it about as little space as I could, and now it's all full.

So, I thought I'd uninstall Ubuntu and reinstall it again with a lot more room on a different drive.

Anyway, I used the live CD I downloaded to make the installation the first time, and I got to the partitioning step and noticed that it couldn't resize the drive at all.

My oldest drive is 27GB FAT32 and it seems to see that okay, and I could resize it if I wanted.
My 2nd oldest, and the drive I have Ubuntu on now is 76GB and was NTFS before I gave 10GB of it to Ubuntu the first time I installed.
My newest drive is also NTFS and is 300GB with 160GB of room, and I want to put Ubuntu there with about 50GB of space.

But, the partition part of the install CD can only see the size of the drive and not how much is used. And the only option I think might work is a complete format, which I can't do due to having a lot of stuff I want to keep on it.

So, is there anything I can do to partition this drive? Windows sees it okay, I just deleted a few files and I defragged it ready for partitioning.

Help!:confused:

---

### Post by caljohnsmith on 2009-01-17
Have you tried using the "manual" partitioning choice during the installation? That should allow you to set up partitions for Ubuntu. If for some reason that doesn't work, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted -l
```
And please post the output.

---

### Post by oopsie on 2009-01-17
Yeah, I only ever did manual partioning.

sudo fdisk -lu gave this

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4397e1fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   625142447   312571192+  42  SFS

Disk /dev/sdb: 27.3 GB, 27325218816 bytes
255 heads, 63 sectors/track, 3322 cylinders, total 53369568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb35350d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    53351864    26675901    c  W95 FAT32 (LBA)

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42bc91a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   140536619    70268278+   7  HPFS/NTFS
/dev/sdc2       140536620   160071659     9767520    5  Extended
/dev/sdc5       140536683   151284104     5373711   83  Linux
/dev/sdc6       151284168   155284289     2000061   82  Linux swap / Solaris
/dev/sdc7       155284353   160071659     2393653+  83  Linux

```

sudo sfdisk -d gave this
```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=625142385, Id=42
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size= 53351802, Id= c, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size=140536557, Id= 7
/dev/sdc2 : start=140536620, size= 19535040, Id= 5
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0
/dev/sdc5 : start=140536683, size= 10747422, Id=83
/dev/sdc6 : start=151284168, size=  4000122, Id=82
/dev/sdc7 : start=155284353, size=  4787307, Id=83

```

sudo parted -l gave this
```
Model: ATA WDC WD3200KS-00P (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs              


Model: ATA Maxtor 92732U8 (scsi)
Disk /dev/sdb: 27.3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags    
 1      32.3kB  27.3GB  27.3GB  primary  fat32        boot, lba


Model: ATA Maxtor 6Y080P0 (scsi)
Disk /dev/sdc: 82.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  72.0GB  72.0GB  primary   ntfs              
 2      72.0GB  82.0GB  10.0GB  extended                    
 5      72.0GB  77.5GB  5503MB  logical   ext3              
 6      77.5GB  79.5GB  2048MB  logical   linux-swap        
 7      79.5GB  82.0GB  2451MB  logical   ext3              

```

I hope all that makes more sense to you than it does to me.

---

### Post by caljohnsmith on 2009-01-17
According to the output of those commands, you have a 320 GB drive that has an NTFS partition on it, but the NTFS partition takes up the entire drive. Also, for some reason the NTFS partition appears to be mislabeled as "SFS" instead of NTFS. I would first correct that problem by doing:
```
sudo sfdisk -c /dev/sda 1 7
```
Then how about pulling up the partition editor (System > Admin > Partition Editor), and see if you can resize the NTFS partition on drive sda (your 320 GB drive). If that works, you could also use the partition editor to set up partitions for Ubuntu if you want. Let me know if that works or not.

---

### Post by oopsie on 2009-01-17
Ummmm

I just went back into windows to check everything was working, and it says my E drive isn't formatted =S

I think I've buggered something up ='(

Should I still do your "sudo sfdisk -c /dev/sda 1 7"?

---

### Post by caljohnsmith on 2009-01-17
Yes, I would go ahead and do the sfdisk command, because it can only help to give the NTFS partition the correct label in the partition table. But if Windows doesn't recognize that partition, it may be that the partition is corrupt. Do you have anything important on that partition, or can you maybe reformat it?

---

### Post by oopsie on 2009-01-17
There is some stuff which is semi-important.

That command still hasn't made it so windows can see it and Linux still can't partition it.

I redid "sudo fdisk -lu" and it just seems to have moved things around.

```

Disk /dev/sda: 27.3 GB, 27325218816 bytes
255 heads, 63 sectors/track, 3322 cylinders, total 53369568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb35350d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    53351864    26675901    7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42bc91a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   140536619    70268278+   7  HPFS/NTFS
/dev/sdb2       140536620   160071659     9767520    5  Extended
/dev/sdb5       140536683   151284104     5373711   83  Linux
/dev/sdb6       151284168   155284289     2000061   82  Linux swap / Solaris
/dev/sdb7       155284353   160071659     2393653+  83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4397e1fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   625142447   312571192+  42  SFS

```

It still says SFS =\

I sense a reformat impending :confused:

Or is there something else I can do?

Thank you for your time and effort anyway, even if I am doomed

---

### Post by caljohnsmith on 2009-01-17
OK, that's not good the device letters are moving around, but we'll just work around it. First do again:
```
sudo fdisk -lu
```
Find which is your 27 GB drive (it was sda in your last post, but use the fdisk command output to know for sure) and do:
```
sudo sfdisk -c /dev/[COLOR="Blue"]sdX[/COLOR] 1 c
```
Replace sdX above with your 27 GB drive. Next, replace sdX in the following command with your 320 GB drive (it was sdc in your last post, but be sure to check with the fdisk command above):
```
sudo sfdisk -c /dev/[COLOR="Blue"]sdX[/COLOR] 1 7
```
And then run fdisk again to make sure your 320 GB drive shows an NTFS partition now, and also that your 27 GB drive has a FAT partition on it. IF that works, you could try gparted on the 320 GB drive again, and let me know how that goes.

---

### Post by oopsie on 2009-01-17
Thank you sooooo much!

Windows can read everything again! Although there was a scary 30 seconds when it couldn't even see my 320GB drive *YIKES*

Anyway, the partitioner software can even see it and seems to offer the ability to partition it.

But, I'm tired now, and I don't think it's wise of me to partition while bleary eyed, so I'll attempt to do the rest tomorrow.

Thank you again for being soooooo helpful.

If there's anything I can do in return, feel free to ask

Anyway, thank you!

---

### Post by caljohnsmith on 2009-01-17
I'm really glad to hear that's all it took to fix the problem. Cheers and good luck partitioning it. :)

---

