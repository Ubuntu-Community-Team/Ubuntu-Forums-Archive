---
title: "Cannot access other partitions."
date: 2017-12-24
forum: Hardware
---

### Post by splatman2 on 2017-12-24
Hi all,
I have installed 16.04.3 LTS, and have divided my 1TB HDD into 4 partitions: 1/4 for a possible future Windows install, 1/4 for Ubuntu, 100G for Swap (at the end of the drive), and the remainder for storage.

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

[FONT=arial]The issue is, I cannot access any partition other than the one the OS is in.
I don't care if I cannot get to the swap or the ones that are less than 100G.
I mainly would like to get to the 931.5G partition, so I can copy the contents of my old 500G external HDD.[/FONT]

---

### Post by coffeecat on 2017-12-24
> **splatman2 said:**
> 100G for Swap (at the end of the drive)

Eh, what?! That's H-U-G-E. Why so big? The ancient rule-of-thumb was 2xRAM but that was before the days of Gigabyte+ sized RAM, and that's not good advice now. These days, allocate the same size as your RAM if you intend to hibernate, otherwise you can generally get away with much less. From Ubuntu 17.10, the default is a swap file rather than a swap partition. 

> **splatman2 said:**
> I mainly would like to get to the 931.5G partition

According to the information you've given, you don't have a 931.5G partition. You have a 931.5G hard drive. You mount partitions, more specifically the filesystems within partitions, not a whole drive.

---

### Post by coffeecat on 2017-12-24
Oh dear. I've seen something else. You have defined a 232.9G root partition for Ubuntu with a separate 372.6G /home. If you're going to have a separate /home, about 20-30G is plenty for the root partition in most cases. 

Why don't you start over and ask for partitioning advice based on what you perceive as your needs?

---

### Post by splatman2 on 2017-12-24
Ok, will start new thread. Thanks.

---

