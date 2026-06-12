---
title: "Question about mounting WD My Book drive in a linux box using Disks"
date: 2013-06-17
forum: Hardware
---

### Post by roylefamily on 2013-06-17
Hi,

I am trying to mount the hard drive out of my Western Digital My Book  World Edition. I have removed it from the case and installed it in a  Ubuntu system(XBMCBuntu on a N40L machine). 

The drive has four  partitions. I wish to mount the 997G partion 4. Using the lower left  gear wheels the Edit Mount Options are greyed out. The Edit Partition  Type pull down shows Linux RAID auto (0xfd). Is this partition type  stopping the Edit Mount Option being active. Can I safely change the partition type?

I am nervous about using  the top right gear-> Format Disc Don’t overwrite existing data  (Quick). Is this the only way forward? The drive has data I don't want to lose.

Thanks

---

### Post by user_of_gnomes on 2013-06-17
Does the WD My Book have a RAID set-up? If that is the case and you change the partition type, you might very well destroy all the data.

---

### Post by roylefamily on 2013-06-17
It was a single drive unit. I thought RAID implied more than one drive. But it does declare itself as Linux RAID auto (0xfd).

---

### Post by user_of_gnomes on 2013-06-17
What's the exact type of WD My Book?

---

### Post by roylefamily on 2013-06-17
Its the 1T white light version.

---

### Post by steeldriver on 2013-06-17
No, don't attempt to change the partition type / table 

It's possible that it really is a RAID disk - try installing the mdadm package and seeing if it will recognize / assemble it

See here

[http://askubuntu.com/questions/21987/not-enough-components-to-start-the-raid-array](http://askubuntu.com/questions/21987/not-enough-components-to-start-the-raid-array)

[http://mybookworld.wikidot.com/forum/t-90514/how-to-recover-data-from-wd-my-book-world-edition-nas-device](http://mybookworld.wikidot.com/forum/t-90514/how-to-recover-data-from-wd-my-book-world-edition-nas-device)

---

### Post by roylefamily on 2013-06-17
Well!

That was a big success!!! Thank you very much. I installed mdadm and postfix via synaptic. I then ran


sudo mdadm --assemble --scan

and the partitions appeared in the file manager:p I have one last inquiry. The drive was starting to fail.
I will be moving stuff of it in stages. All the data is in /Public, owner Root, Group Steven. If I enter that folder and try to move
a sub-folder on to another drive I am denied permission. For example /AVCHD Comp1, Owner 99, Group Steven.

It will let me move /Data in one operation but that may be unwise. I am uncomfortable messing with permissions when I don't know what
I am doing.

---

### Post by roylefamily on 2013-06-17
> **roylefamily said:**
> Well!

That was a big success!!! Thank you very much. I installed mdadm and postfix via synaptic. I then ran


sudo mdadm --assemble --scan

and the partitions appeared in the file manager:p I have one last inquiry. The drive was starting to fail.
I will be moving stuff of it in stages. All the data is in /Public, owner Root, Group Steven. If I enter that folder and try to move
a sub-folder on to another drive I am denied permission. For example /AVCHD Comp1, Owner 99, Group Steven.

It will let me move /Data in one operation but that may be unwise. I am uncomfortable messing with permissions when I don't know what
I am doing.

I should add my new drive (where I am to move the stuff off the old drive) is shown as Owner root, Group root, change contents-only owner. So that's probably the issue.

---

### Post by steeldriver on 2013-06-17
Well if you have any concerns about the health of the drive, then you should prioritize getting the data off it - you can worry about ownerships / permissions later

How are you accessing the drive now? if you are using the GUI filemanager (not command line) then probably all you need to do is run it with administrative privileges - I'm not sure which file manager is used in XBMCbuntu, possibly PCmanFM? in which case you should be able to do from a terminal

```
gksu pcmanfm &
```

which should let you copy anything anywhere (so be careful!)

---

### Post by roylefamily on 2013-06-18
Yes, that worked. Interstingly the directories that were falling apart in the WD enclosure are still corrupt. The drive is failing. All of it that I wanted copied without complaint, however now I will find a file compare function to check them.

---

### Post by roylefamily on 2013-06-18
Checked every thing with Meld and it's good. I was hoping to file check and repair the drive to see if I could wring a bit more life out of it. Unfortunately it looks like as it's raid gparted won't file check it. I assume a reformat is needed?

---

### Post by steeldriver on 2013-06-18
There should be an actual filesystem (ext2/ext4/xfs) on top of the RAID volume - you could try probing the RAID block device with the 'file' command e.g.

```
sudo file -sL /dev/md0
```

which should give you some info - if it's xfs that might explain why gparted won't check it, in that case you may need a disk check utility from the xfsprogs package

---

### Post by roylefamily on 2013-06-22
Hi,

The file system is xfs. The drive continues to degrade and wont mount. That's ok, I got my data. 

My new drive has mounted at /media/Steven/f53ea550..........

It is owned by root but I need to own it. sudo chown -R steven:steven /dev/sdc1

does not change any thing. Any ideas?

---

### Post by coffeecat on 2013-06-22
> **roylefamily said:**
> 
My new drive has mounted at /media/Steven/f53ea550..........

It is owned by root but I need to own it. sudo chown -R steven:steven /dev/sdc1

does not change any thing. Any ideas?

If you want to own a Linux filesystem, you need to mount it and then own the mountpoint, not the device descriptor. That sounds weird, I know, but that's the way it works. Owning the mountpoint while the filesystem is mounted actually owns the filesystem rather than the mountpoint, which can be proven by re-checking the mountpoint ownership with the filesystem mounted and unmounted after you have owned it. Also, if you have not yet written any files to the filesystem, you do not need the -R option. So...

```
sudo chown steven:steven /media/Steven/f53ea550..........
```

Obviously, complete the full UUID of the mountpoint.

Two additional tips: if you label the sdc1 partition and then mount it via the filemanager, the mounpoint will be /media/steven/partition_label. Much more convenient than that long UUID string. Also, in the chown command - if you type steven: then your default steven usergroup name will be assumed. Thus:

```
sudo chown steven: /media/Steven/f53ea550..........
```

It saves a few keystrokes. It seems to be a little-known shortcut.

---

### Post by roylefamily on 2013-06-27
Hi Guys,

Things have moved on a bit. After scanning the faulty  drive it looks good. Perhaps years of untidy power downs and no disc  maintenance unravelled it. So I have the two 1T drives formatted as xfs and  assembled as /dev/md127 a raid1 device. The mdadm create process went  without hitch, taking 150 minutes or so to synchronise. I am wondering  what form the mount command takes for a raid device. Is xfs the file type?

I will put it  at /mnt/raid1/. The directory raid1 is created. Strangely it is not  visible in the terminal that created it. When I tried to create it a  second time sudo mkdir reported it as existing?

---

### Post by steeldriver on 2013-06-27
What do you mean by "not visible in the terminal that created it"? what does

```
ls /mnt
```

say? If the directory was created OK, you should be able to mount it as

```
sudo mount -t xfs /dev/md127 /mnt/raid1
```

If you are permanently mounting the array as part of your system, then you will probably want to put an entry for it in your /etc/fstab using either the array UUID or the device mapper name (/dev/mapper/xxx) - and also run 'update-initramfs -u' to write the RAID config into your initial RAM image.

---

### Post by roylefamily on 2013-06-27
OK,

Should have done 

mkdir raid1

 not 

mkdir /raid1 

so that's sorted.

The mount command complains of wrong fs type, bad option, bad superblock.
 
I think that formatting the drives as xfs before creating the  raid1 may have been meaningless. Perhaps now is the time for a format?

---

### Post by roylefamily on 2013-06-27
It gets worse!

I have looked in gparted. My md127 hasn't even got a partition. Its member drives sdb1, sdc1 have formatted xfs partitions. I suppose that's not all that's required.

---

### Post by steeldriver on 2013-06-27
Let's take a step back here - what are you trying to do exactly? you mention 'creating' the RAID and xfs but do you remember exactly what commands you used? What do

```
sudo parted /dev/sdb
```

```
sudo parted /dev/sdc
```

say? 

Do you actually need a RAID device? are you trying to get the original  WD external back up and running with a replacement disk or is the  intention just to use the new disk as is?

---

### Post by roylefamily on 2013-06-28
Hi,

I rescued the data of my western digital 1T drive and upon doing a disk check it came up ok. Having bought another 1T I decided to make a raid1 out of the pair. I did this by creating 1 linux raid auto partition on each drive and formatting to xfs. the drives are sdb and sdc

The mdadm create command worked and created /dev/md127 out of sdb and sdc. Now I thought that at this point md127 should be mountable. However in gparted md127 is shown as having no partition. Not surprising as I never created one but I didn't think that I needed to.

sudo parted /dev/sdb

 and

sudo parted /dev/sdc

start parted with no errors and it waits for me to do issue a command. I did nothing and quit. 


sudo mount -t xfs /dev/md127 /mnt/raid1

exits with errors wrong fs type, bad option, bad superblock. 

It looks to me that I need to create a partition on md127.

---

### Post by steeldriver on 2013-06-28
Sorry that was a brainfart on my part - I meant 

```
sudo parted /dev/sdb [COLOR=#0000ff]**print**[/COLOR]
```

You should see something like

```

Model: ATA WDC WD20EARX-00P (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  68.7GB  68.7GB               primary  lvm
[B] 2      68.7GB  2000GB  1932GB               primary  [COLOR=#0000ff]raid[/COLOR]
[/B]
```

(ignore my other - LVM - partition). You can use

```
sudo file -sL /dev/md127
```

to see what filesystem it thinks you have got on top of the RAID

---

### Post by roylefamily on 2013-06-28
Hi,

This is the parted output

Model: ATA WDC WD10EADS-11M (scsi) Disk /dev/sdb: 1000GB Sector size  (logical/physical): 512B/4096B Partition Table: msdos  Number  Start    End     Size    Type     File system  Flags  1      1049kB  1000GB   1000GB  primary  xfs          raid 

Model: ATA ST1000DM003-1CH1 (scsi) Disk /dev/sdc: 1000GB Sector size  (logical/physical): 512B/4096B Partition Table: msdos  Number  Start    End     Size    Type     File system  Flags  1      1049kB  1000GB   1000GB  primary  xfs          raid  

And for md127.                                                                            

Error: /dev/md127: unrecognised disk label


sudo file -sL /dev/md127

results in

/dev/md127: data

---

### Post by steeldriver on 2013-06-29
Well tbh I'm not sure if having the xfs filesystem on there before you created the array will be a problem or not - there are a couple a good RAID folks on the forum (darkod, rubylaser, ...) so it may be worth starting another thread with that subject specifically (since this one has drifted off the original topic). You could *try* creating your xfs now on top of the RAID device and see what it says - or since you don't have any data on the array yet you could just blow the whole thing away and start from scratch.

---

