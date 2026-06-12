---
title: "pre-partitioning linux drives from within windows"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by joelswatson on 2009-03-27
hi,

i am going from windows vista to a dual boot windows vista ubuntu 9.04 (when it get released)
i am going to do a clean install of windows vista (cause its due for one)
but what i would like to know, cause i have a 500gb hdd, i am going to have 4 partitions on it, 1 for vista, 1 for ubuntu, 1 for the swap file, and 1 for torrent.

what i want to know is can i create the partitions from within windows, but leave them as raw (unformatted) so i can format them into ext4 when i install ubuntu,

cause i want vista at the start of the drive, then ubuntu, then swap, and torrent at the end of the drive.

is this possible?

thanks

---

### Post by Anthon on 2009-03-27
Yes you can do things that way. If you don't need the torrent stuff from within Vista then things are easiest: just setup Vista without taking the full drive.
If you want to setup the torrent drive as an NTFS partition you should either boot Ubuntu from CD and create the remaining partitions using fdisk, or figure out how to do that under Vista (or ask on a vista forum).

---

### Post by Mark Phelps on 2009-03-27
> **joelswatson said:**
> hi,

what i want to know is can i create the partitions from within windows, but leave them as raw (unformatted) so i can format them into ext4 when i install ubuntu,

cause i want vista at the start of the drive, then ubuntu, then swap, and torrent at the end of the drive.

is this possible?

thanks

First of all, I don't think Vista will allow you to create unformatted partitions; in fact, I've not seen any tool that will.

Second, would be better to use the GParted Live CD (you can get it from distrowatch.com) and use that to format the Linux partitions, especially since that tool understands Ext3 and Linux-swap partition formatting.

Third, I wouldn't use ext4 right now.  Canonical did not make it the default for 9.04, and I would wait for a while until the Linux utilities mature to all handle ext4 before doing that.  I've read that the performance improvements are really minor using ext4.

---

### Post by Anthon on 2009-03-27
> **Mark Phelps said:**
> First of all, I don't think Vista will allow you to create unformatted partitions; in fact, I've not seen any tool that will.

Second, would be better to use the GParted Live CD (you can get it from distrowatch.com) and use that to format the Linux partitions, especially since that tool understands Ext3 and Linux-swap partition formatting.

Third, I wouldn't use ext4 right now.  Canonical did not make it the default for 9.04, and I would wait for a while until the Linux utilities mature to all handle ext4 before doing that.  I've read that the performance improvements are really minor using ext4.
fdisk (both under windows and under linux) do not format the partitions that you create.

---

### Post by Mark Phelps on 2009-03-27
> **Anthon said:**
> fdisk (both under windows and under linux) do not format the partitions that you create.

Sorry ... should have been more specific in my answer.

The OP was talking about using Vista to create unformatted partitions. fdisk is a DOS command and will not run in a command line in Vista (I know, I just tried it confirm it).

However, your mention of fdisk jogged my memory regarding the new Disk Part command that might be able to do what the OP wants.

See the link below for details:

[http://technet.microsoft.com/en-us/library/cc766465.aspx]("http://technet.microsoft.com/en-us/library/cc766465.aspx")

---

### Post by graysky on 2009-03-27
Don't do it from windows at all.  Download gparted (live cd) and do your disk editing there.  It rocks and you will be very happy.

My recommendation for partitions for a single drive/dual boot system:

#1) NTFS (your windows)
#2) / (root filesystem for ubuntu), ext3
#3) /torrent (or whatever windows share you wanna call it), NTFS
#4) LOGICAL PARTITION
#4a) /home (home partition for ubuntu, ext3
#4b) /swap (swap for ubuntu), swap


Note that there is a 4 primary partition limit for drives so you'll need to make a logical partition first, then put the others in it as I have shown you (i.e. #4a and #4b).

My system has two HDDs and I "tri-boot" between windows and two different LINUX flavors:

HDD #1
Partition #1) NTFS (windows)
Partition #2) NTFS (shared data space similar to your 'torrent' partition)
Partition #3) /boot (boot for LINUX), ext3

HDD #2
Partition #1) / (root filesystem for Debian), ext3
Partition #2) / (root filesystem for Ubunutu), ext3
Partition #3) /swap (linux swap)
Partition #4) LOGICAL PARTITION
Partition #4a) /home (homes for linux), ext3
Partition #4b) NTFS (shared data space #2 similar to your 'torrent' partition)

Anyway, you get the idea.

---

### Post by joelswatson on 2009-03-27
hi, 

thanks for everyones response, 

i wasnt going to create the partitions from within windows, but what i wanted to do is create the partitions for ubuntu before i go to install ubuntu, that way i have had the hard drive partitioned like i wanted it setup.

so once again, thanks to everyone again, my questions has been answered.

---

