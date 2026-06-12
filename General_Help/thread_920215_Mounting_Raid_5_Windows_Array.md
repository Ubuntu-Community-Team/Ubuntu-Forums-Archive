---
title: "Mounting Raid 5 Windows Array"
date: 2008-09-15
forum: General Help
---

### Post by homergonerson on 2008-09-15
Hello all. I'm new to Ubuntu (8.04), and I was wondering how I mount my Windows RAID 5 array. It's 4 500gb drives, and my Ubuntu is installed on a separate sata drive. I tried using one method I found in a thread using mdadm, and here's how that went down:

```
joseph@joseph-ubuntu:~$ cat /proc/partitions
major minor  #blocks  name

   8     0  488386584 sda
   8    16  488386584 sdb
   8    32  488386584 sdc
   8    33   31455238 sdc1
   8    34          1 sdc2
   8    48  488386584 sdd
   8    64  312571224 sde
   8    65  306496071 sde1
   8    66          1 sde2
   8    69    6072538 sde5
joseph@joseph-ubuntu:~$ sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sda /dev/sdb /dev/sdc /dev/sdd
mdadm: requested 2 devices in array but listed 4
joseph@joseph-ubuntu:~$ sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=4 /dev/sda /dev/sdb /dev/sdc /dev/sdd
mdadm: array /dev/md0 built and started.
joseph@joseph-ubuntu:~$ sudo mkdir /media/Windows
joseph@joseph-ubuntu:~$ 
joseph@joseph-ubuntu:~$ sudo mount -t ntfs /dev/md0 /media/Windows
NTFS signature is missing.
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

Tried installing the NTFS Config Tool, but the enable support for internal device is greyed out, so I can't select it (not sure if that tool even works with a RAID array.)

Long story short, how do I get to my shite?

---

### Post by fjgaude on 2008-09-15
The only way I have known of to mount Windows raid is through the use of **dmraid** tool. The last time I noticed about two years ago, it didn't handle raid5, only raid0,1. That might have changed.

If the NTFS raid array is assembled by the BIOS on bootup you likely can see the array if you have something like **ntfs-3g** installed. Takes lots of understanding, learning to get all this to work correctly.

Good luck!

After looking over what you are doing I've come to conclude you are trying assemble an array with mdadm that is NTFS... I'm not sure really what you are doing... more details please.

---

### Post by homergonerson on 2008-09-15
I followed this post's walkthrough. I wasn't sure if it would work for RAID 5, because the original poster was asking for RAID 0.

[http://ubuntuforums.org/showpost.php?p=5217561&postcount=5](http://ubuntuforums.org/showpost.php?p=5217561&postcount=5)

---

### Post by hallsberg79 on 2008-09-15
with a little help from this page [_HOWTO_Install_Gentoo_with_NVRAID_using_dmraid_]("http://gentoo-wiki.com/HOWTO_Install_Gentoo_with_NVRAID_using_dmraid") I managed to mount my existing raid 5-partition (which I before used with a windows (2000) system as my storage drive).

I downloaded and installed dmraid. (sudo apt-get install dmraid)

I initiated the command
```
sudo dmraid -ay 
```
the result was:
```
RAID set "nvidia_bciddaii" already active
RAID set "nvidia_bciddaii1" already active
RAID set "nvidia_bciddaii5" already active
```
With my limited knowledge of my partition I guessed that nvidia_bciddaii was the whole raid "disc", bciddaii1 was the smaller partition with windows2k on it and bciddaii5 was the larger storage partition.

then I made a directory where I wanted to mount the storage partition to:
```
sudo mkdir /whatever
```
and mounted the bciddaii5-partition to that directory
```
sudo mount /dev/mapper/nvidia_bciddaii5 /whatever
```

I used the directory /mnt/raid5 for the purpose, perhaps there is a better place to mount the partition. But as the previous writer, Im also new to linux and ubuntu - but I dont lack the guts to try different sollutions to get a problem solved :)

hope there is some help in my text to you Joseph!
best regards Isak

---

### Post by homergonerson on 2008-09-16
> **hallsberg79 said:**
> with a little help from this page [_HOWTO_Install_Gentoo_with_NVRAID_using_dmraid_]("http://gentoo-wiki.com/HOWTO_Install_Gentoo_with_NVRAID_using_dmraid") I managed to mount my existing raid 5-partition (which I before used with a windows (2000) system as my storage drive).

I downloaded and installed dmraid. (sudo apt-get install dmraid)

I initiated the command
```
sudo dmraid -ay 
```
the result was:
```
RAID set "nvidia_bciddaii" already active
RAID set "nvidia_bciddaii1" already active
RAID set "nvidia_bciddaii5" already active
```
With my limited knowledge of my partition I guessed that nvidia_bciddaii was the whole raid "disc", bciddaii1 was the smaller partition with windows2k on it and bciddaii5 was the larger storage partition.

then I made a directory where I wanted to mount the storage partition to:
```
sudo mkdir /whatever
```
and mounted the bciddaii5-partition to that directory
```
sudo mount /dev/mapper/nvidia_bciddaii5 /whatever
```

I used the directory /mnt/raid5 for the purpose, perhaps there is a better place to mount the partition. But as the previous writer, Im also new to linux and ubuntu - but I dont lack the guts to try different sollutions to get a problem solved :)

hope there is some help in my text to you Joseph!
best regards Isak
Ohhhh! ThankyouThankyouThankyouThankyouThankyouThankyou! Worked like a charm! Now one last question, do you know if I'm allowed to edit/add files to what I mounted? I read in one thread that editing them could potentially corrupt some things because of the way Linux/Windows set up RAID drives. Something about 64 and 128 chunks :/

---

### Post by hallsberg79 on 2008-10-03
I don't know if you can write/edit on your mount. I was not planning to, I was to mount it and make a backup on a new drive.

I'm sorry

---

