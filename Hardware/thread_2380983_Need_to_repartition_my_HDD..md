---
title: "Need to repartition my HDD."
date: 2017-12-24
forum: Hardware
---

### Post by splatman2 on 2017-12-24
Hi all,
I have posted before about not being able to access all partitions, and was told that I messed up on the install.
I have installed 16.04.3 LTS, and have divided my 1TB HDD into 4  partitions: 1/4 for a possible future Windows install, 1/4 for Ubuntu,  100G for Swap (at the end of the drive), and the remainder for storage.

By entering the following into Terminal:
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL

[FONT=arial]I get:[/FONT]
NAME   FSTYPE   SIZE MOUNTPOINT                LABEL
sdb            59.7G                           
&#9492;&#9472;sdb1 exfat   59.6G /media/splatman/9C33-6BBD 
sr0            1024M                           
sda           931.5G                           
&#9500;&#9472;sda4 ext4   372.6G /home                     Splat
&#9500;&#9472;sda2 ext4   232.9G /                         
&#9500;&#9472;sda5 vfat      95M /boot/efi                 
&#9500;&#9472;sda3 swap    93.1G [SWAP]                    
&#9492;&#9472;sda1 vfat   232.9G /windows                  

I have been made aware that I do not need anywhere near 100G for Swap. How much should it be? I have 16G of memory.
As far as the rest goes, how do I go about fixing this mess? Use GParted?

---

### Post by oldfred on 2017-12-24
With UEFI Windows wants more than one partition.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Ubuntu needs / (root), just about all other partitions then become optional. With UEFI one ESP - efi system partition (FAT32) is shared with all UEFI boot installs.
       
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
    
        
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by splatman2 on 2017-12-24
Thanks oldfred. I'll take my time to read it.

---

