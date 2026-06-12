---
title: "Recovering Data from a Corrupted harddrive"
date: 2008-11-29
forum: Hardware
---

### Post by Adanhym on 2008-11-29
Hello, My friend's laptop's (still runnning Vista) motherboard melted and I believe corrupted the harddrive with it. I currently have Ubuntu LiveCD booted up and trying to recover some data from the Harddrive and I get the following error after using fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

```
After trying to force mount it with 
```
sudo mount -t ntfs-3g /dev/sda /media/mount -o force

```
I get the following error 
```
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

``` Is there any way I can create a partition table without destroying the data on it? By the way, this is a NTFS partition with just a standard Vista install on it, and GParted lists just 74.3GB of unallocated data on the drive and nothing has been done to the drive since it was removed from the laptop several months ago.

---

### Post by aysiu on 2008-11-29
I don't know how to use this program, but I think *GPart* (different from *GParted*) will help you.

---

### Post by Adanhym on 2008-11-29
Can you tell where/how to find GPart? I searchd for it with Synaptic and all I found was GParted.

---

### Post by aysiu on 2008-11-29
It should be in Synaptic if you have the Universe repositories enabled. Go to Settings > Repositories and make sure you have the Universe repositories checked, and then click Reload.

---

### Post by finito on 2008-11-29
Live CD doesnt have ntfs-3g. You have to install that first.

---

### Post by caljohnsmith on 2008-11-29
I would give "testdisk" a try to see if it can rebuild your partition table; to use testdisk, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", then do "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of the screen, and also select each partition and press "P" to list its root directory; let me know which partitions give a valid listing. 

If the above method works to find partitions on your HDD, let me know what partitions you think are valid based on your memory of what was supposed to be on the drive. We can work from there if you want. :)

---

### Post by Adanhym on 2008-11-29
After installing Testdisk and finishing the Deep Scan, I found the right partitions and was able to copy the necessary files back over to an external...sorry it took a while to post back; my friend sort of jumped me and hugged me repeatedly for getting the files back and I was told to send a /hug to all who posted and helped ^^

---

### Post by caljohnsmith on 2008-11-29
I think you missed doing the "deep scan"; in that first screen shot you posted, press "enter" to proceed, "Y" to search for Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. The deep search results are important to make sure you try and recover the correct partitions.

---

