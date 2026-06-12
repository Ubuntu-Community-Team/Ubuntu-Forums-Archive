---
title: "Mouning a GPT Hard Drive"
date: 2012-02-19
forum: Hardware
---

### Post by spikesforu on 2012-02-19
Hello Everyone,
 
Well this is my first post, so if I miss anything please let me know. Got a Dell 2900 64bit Sever so that I may watch all the movies I have saved through the years, throughtout the house. After install Windows 2008r2 and finiding out that almost all php scripts run better on Linux, I decied to install my first Linux OS. I choose Ubuntu because of all the grreat reviews it has gotten. 
 
Here is my problem I have 5 drive in the server, of which 2 are on a Raid 1 for the OS. Then I have 1 drive with 500GB for downloads on a 0 raid. Finally I have 2 drive 3TB each on a ) raid for storing movies. Since windows MBR max is 2TB I had to change the partitions to GPT. As I have been reading Ubuntu does not see these drives easily. So why question is how do I get Ubuntu to see these drives. Another problem I have is these drives have about 2 TB of movies in them. I don't want to delete the partition and loose the data.
 
Any help would be appriciated.

---

### Post by oldfred on 2012-02-19
Welcome to the forum.

I use gpt with BIOS but not RAID and I know very little about RAID. Once formated with gpt there is no difference. And only with the first version of Ubuntu did I have to add a parameter to get my gpt boot drive to chain load to a MBR drive. I totally reformated my gpt drives and just used gparted. I also used gpt on my 16GB flash drive without any issue as long as I created the bios_grub partition.

Any drive modification has risks, so backups are important.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

If using gpt with BIOS create a 1MB bios_grub partition. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)

---

