---
title: "120 GB SSD 110 GB available, plus a very interesting problem"
date: 2011-01-14
forum: Hardware
---

### Post by deltacomp on 2011-01-14
Hello, I have a HP 2540P laptop which I upgraded with a OCZ Vertex 2 120 GB SSD, installed Ubuntu 10.10 without a problem (no swap/upgraded memory to 8GB). I then followed a guide which allowed me to disable journaling (as far as I can tell I have enabled "TRIM" after completing the guide). 

What I found later was that the system shows only 110 GB total, and 100 GB of available storage?!?!? Some questions I have asked my self: Is there a swap on there? When I check fdisk -l in terminal it shows total capacity of ~120 GB but again it shows 100 GB available, with no swap area/partition, so again where did the other 20 GB go?

Now the very interesting part, I noticed a couple days ago that after an update and a restart, the same update was available for download. I found this kind of strange, so I did some more checking and found that a lot of changes to files and new programs were also not saved on the system. After several attempts to save anything on the computer, I realized that after every restart, it would default back to a certain period/environment regardless of the changes. 

After spending several hours trying different things, changing the back round, colors, etc... I decided to reinstall Ubuntu. After reformatting the SSD and installing a fresh version of 10.10, I found that the SSD was still only showing 100 GB available (again no swap). Then after I tweaked the environment, I shut it down, turned it back on a while later and KAPOW!!! back to the old environment!!! I couldn't believe it, but some how after reformatting the SSD, the original environment was back. I ask my self if there is some partition in the SSD which is not showing up in fdsik -l and gparted that is storing this configuration and loading it as a default after every restart? If so how do I annihilate it? 

I have been searching several forums for some information on removing swaps and expanding SSDs but have come up empty. Any help would be greatly appreciated. 

Thanks in advance.

---

### Post by cchhrriiss121212 on 2011-01-14
A 120GB drive will only give you 110GB of actual storage, due to gigabyte naming conventions:
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)
Actual storage is roughly 93% of the advertised amount, so a "2TB" drive is actually 1.86TB.

How did you partition the drive? Manually, or with "use the whole drive" option?

---

### Post by gordintoronto on 2011-01-14
It also sounds like there is a hardware problem with the drive. The highest frequency for failure for computer components is right when you take them out of the box.

---

### Post by IcarusR on 2011-01-14
> I then followed a guide which allowed me to disable journaling (as far as I can tell I have enabled "TRIM" after completing the guide).


What guide did you follow, post a link so we can see what you did, may give us a clue.

Sounds like the file system is read only ?

---

### Post by deltacomp on 2011-01-14
> **cchhrriiss121212 said:**
> A 120GB drive will only give you 110GB of actual storage, due to gigabyte naming conventions:
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)
Actual storage is roughly 93% of the advertised amount, so a "2TB" drive is actually 1.86TB.

How did you partition the drive? Manually, or with "use the whole drive" option?

AAhhh thanks for the info. Thats something I had considered (kind of), but I would have thought 10GB would have been kind of a lot. I will look into the link when I have more time. 

I manually partitioned the SSD, then selected the entire drive. 

Thanks for your help

---

### Post by deltacomp on 2011-01-14
> **gordintoronto said:**
> It also sounds like there is a hardware problem with the drive. The highest frequency for failure for computer components is right when you take them out of the box.

I can't find any evidence that it is a drive issue. Though it was not one of my considerations, I will definitely look into it some more. 

Thanks

---

### Post by deltacomp on 2011-01-14
Just as an update: I took the SSD out of this comp, put it in my desktop, formatted the entire SSD, then put it back into the laptop (clean) and started the computer, and BAM! the same environment...

Thanks

---

### Post by slooksterpsv on 2011-01-14
120 * 1000 * 1000 * 1000 / 1024 / 1024 / 1024 = 111.7587GB
So a 120GB Drive is technically 111.75GB.

Technically 120 GB Drive should = 128849018880 Bytes
Where as 120 GB Drive is actually = 120000000000 Bytes

They consider a KB to be 1000 Bytes, when it's actually 1024.

So for a 1TB Drive:
1 * 1000 * 1000 * 1000 * 1000 / 1024 / 1024 / 1024 = 931.32 GB
There's 68.68GB that is actually not part of a 1 TB drive.

---

### Post by deltacomp on 2011-01-14
> **slooksterpsv said:**
> 120 * 1000 * 1000 * 1000 / 1024 / 1024 / 1024 = 111.7587GB
So a 120GB Drive is technically 111.75GB.

Technically 120 GB Drive should = 128849018880 Bytes
Where as 120 GB Drive is actually = 120000000000 Bytes

They consider a KB to be 1000 Bytes, when it's actually 1024.

So for a 1TB Drive:
1 * 1000 * 1000 * 1000 * 1000 / 1024 / 1024 / 1024 = 931.32 GB
There's 68.68GB that is actually not part of a 1 TB drive.

Yes, good point, and thanks for the reply. Regarding an earlier post, if the files are read only, does that mean that even with a reformat, the files will be untouched. Either way, does any one know how to remove/change the file owner/permission of / ? Simply using the sudo chmod/chown command in the terminal does nothing. 

Thanks

---

### Post by efflandt on 2011-01-14
Did you use tmpfs for anything other than /tmp. or do use ramfs for anything?  Maybe something is saving configuration to somewhere not permanent.  What exactly are you changing in your environment and what is it changing back to?

I originally used my Intel 80 GB SSD for Maverick and am now using it for Natty without any drive issues (no swap).  I am using 512K aligned cylinders (32 heads, 32 sectors), ext4 w/journal disabled and following in fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=e70810eb-379d-4f9f-9087-54c2f1cd96f9 /    ext4    noatime,discard,errors=remount-ro 0       1
tmpfs        /tmp        tmpfs    nodev,nosuid    0    0
```and following in /etc/rc.local:

```
echo deadline > /sys/block/sdb/queue/scheduler
echo 1 > /sys/block/sdb/queue/iosched/fifo_batch
```Of course if you are running Natty, don't expect that to be stable yet.  Mine was flip flopping between good icons and bad icons for a while and has now settled on good icons.  But that has nothing to do with the drive and everything to do with changing packages and libraries and working out development bugs.  Nothing has disappeared that I have installed.

---

### Post by deltacomp on 2011-01-30
Ok, sorry its been a little while, I was able to reformat the SSD completely using a BIOS option. I have reinstalled Ubuntu 10.10 and I am still experiencing the same problem. Again if I save something to a directory or create a new file it is still missing after a restart. I checked my fstab file and compared it with an earlier post and found no significant difference between the two. I will keep checking on the temp file storage but am unsure what/where to look for. 

Thanks.

---

### Post by slooksterpsv on 2011-01-30
You can use Disk Usage Analyzer to find out where your space is allocated to:

380.6 GB Partition (80GB used for Xubuntu 11.04 Alpha 1)
125.2 GB Used for / - with it subsectioned into:
116.9GB /home
5.9 GB /usr
1.8 GB /var
430.5 MB /lib
96.3 MB /opt
71.2 MB /boot
15.8 MB /etc
11.1 MB /sbin
9.8 MB /dev
8.0 MB /bin
7.5 MB /lib32
1.4 MB /tmp
228.0 KB /root
8.0 KB /media
4.0 KB /mnt
4.0 KB /srv
4.0 KB /selinux

That's how my system looks, for a 500 GB HDD = 465.76 GB Actual.
465.76 - 386.65 = 79.11
79.11 - 76.30 (80GB Partition for Xubuntu 11.04 Alpha 1) = 2.81GB
2.81 - 2.81 (SWAP) = 0
1.02MB unallocated

So it looks like I'm missing 5GB... odd... how big are the nodes and links on an ext4 partition? Could that be it?

EDIT: It may be Metadata, which is fine with me 5GB isn't no sweat off my back.

---

### Post by deltacomp on 2011-01-30
> **slooksterpsv said:**
> You can use Disk Usage Analyzer to find out where your space is allocated to:

380.6 GB Partition (80GB used for Xubuntu 11.04 Alpha 1)
125.2 GB Used for / - with it subsectioned into:
116.9GB /home
5.9 GB /usr
1.8 GB /var
430.5 MB /lib
96.3 MB /opt
71.2 MB /boot
15.8 MB /etc
11.1 MB /sbin
9.8 MB /dev
8.0 MB /bin
7.5 MB /lib32
1.4 MB /tmp
228.0 KB /root
8.0 KB /media
4.0 KB /mnt
4.0 KB /srv
4.0 KB /selinux

That's how my system looks, for a 500 GB HDD = 465.76 GB Actual.
465.76 - 386.65 = 79.11
79.11 - 76.30 (80GB Partition for Xubuntu 11.04 Alpha 1) = 2.81GB
2.81 - 2.81 (SWAP) = 0
1.02MB unallocated

So it looks like I'm missing 5GB... odd... how big are the nodes and links on an ext4 partition? Could that be it?

EDIT: It may be Metadata, which is fine with me 5GB isn't no sweat off my back.

Hey thanks for the info and taking the time to address my problem, I found this forum which explains that is a problem with the actual drive and not the OS. 

[http://phoronix.com/forums/showthread.php?25290-OCZ-Vertex-2-SSD-So-fast-it-can-time-travel](http://phoronix.com/forums/showthread.php?25290-OCZ-Vertex-2-SSD-So-fast-it-can-time-travel)

I really appreciate all the help!

---

