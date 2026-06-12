---
title: "how do i partition?"
date: 2005-12-22
forum: Hardware &amp; Laptops
---

### Post by 0okami on 2005-12-22
I have an 80GB disk which is split in 2. 20gb for windowsXP and program files, and 30gb for games and storage. Problem is, after installing windows, it wont see the 60gb partition. In fact, i dont even remember creating it. And i dont remember how to create it. 

Then, i have another disk which is 60gb where I have ubuntu. 

My question is:
 Is there a tool I can use in ubuntu to create a partition and format for use with windows? 

if not, what other options do i have? 

I love both operating systems very much.

---

### Post by manicka on 2005-12-22
Gparted will create the partition for you in Ubuntu, but you'll find that you need to use this disk manager in Windows to reformat and allocate the new partition  a drive number, as Windows won't fully recognise the partion that Gparted set up..... typical.

---

### Post by 0okami on 2005-12-22
ok, tried gparted. xp didnt seem to like it :( meh. 

I did find a way around. I took the XP disk, went through all the steps as if i were to install a clean XP, but when it reached the partitioning guide, i told it to use the unpartitioned space, it created the partition, and right before it went to install XP, i stoped everything and rebooted.

This left the partition existing, but raw... In XP, i proceeded to format... the only option was NTFS, i was actually hoping for FAT32 so i can read/write to it from linux as well..... but ah well. Its working at least. 

thanks for the reply.

---

### Post by manicka on 2005-12-22
[QUOTE=0okami

This left the partition existing, but raw... In XP, i proceeded to format... the only option was NTFS, i was actually hoping for FAT32 so i can read/write to it from linux as well..... but ah well. Its working at least. 
.[/QUOTE]

You couldn't choose fat32 because the partition is larger than 32gb. Try using the Disk Management tool ("My Computer" -> Manage -> Disk Management) to make some smaller partitions if want them to be fat32.

---

### Post by 0okami on 2005-12-22
EEEK!!!!!!!!!!!! it appears now that linux is gone.. its not asking to boot into linux anymore! curse you MS! LOL 

OMG! this is bad... and funny at the same time. 
noooo! my poor kawaii neko-mimi collection!

---

### Post by psusi on 2005-12-22
[QUOTE=manicka]You couldn't choose fat32 because the partition is larger than 32gb. Try using the Disk Management tool ("My Computer" -> Manage -> Disk Management) to make some smaller partitions if want them to be fat32.[/QUOTE]

Or format it in linux, it has no problem formatting > 32 gigs for fat32.  Just another place Microsoft decided to tell you you can't go today ( they want people to use NTFS ).  They did the same thing with fat16 vs fat32: 9x refused to format anything over 2 gigs as fat16, NT went to 4... technically fat16 can be as large as 8 gigs.  

[QUOTE=0okami]EEEK!!!!!!!!!!!! it appears now that linux is gone.. its not asking to boot into linux anymore! curse you MS! LOL 

OMG! this is bad... and funny at the same time. 
noooo! my poor kawaii neko-mimi collection![/QUOTE]

Disk manager probably trashed the grub MBR.  Reinstall grub from the livecd and everything should be fine.

---

