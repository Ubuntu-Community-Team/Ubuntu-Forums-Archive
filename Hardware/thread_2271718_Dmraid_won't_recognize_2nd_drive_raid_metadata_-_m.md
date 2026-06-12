---
title: "Dmraid won't recognize 2nd drive raid metadata - must activate, mount"
date: 2015-04-01
forum: Hardware
---

### Post by aaron85 on 2015-04-01
Greetings, I'm a novice as far as the GNOME terminal and am running Ubuntu 14.10 as a recovery environment in order to attempt saving data on my isw (Intel Software Raid) raid 0 logical volume.  For this purpose I've become familiar with the Dmriad commands.  
    My problem is: when I try to activate the raid   “sudo dmraid -ay” I get 
[FONT=courier new]ERROR: isw: wrong number of devices in RAID set isw_baiegdbibf_Volume0" [1/2] on /dev/sda[/FONT]
[FONT=courier new]RAID set "isw_baiegdbibf_Volume0" was not activated[/FONT]


Dmraid doesn't seem to see the raid metadata on my /dev/sdb/ drive.
Listed Here: 


[FONT=courier new]Disk /dev/sdb: 238.5 GiB, 256060514304 bytes, 500118192 sectors[/FONT]
[FONT=courier new]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=courier new]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=courier new]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=courier new]Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors[/FONT]
[FONT=courier new]Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=courier new]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=courier new]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=courier new]Disklabel type: gpt[/FONT]
[FONT=courier new]Disk identifier: 23B32B95-BE47-4150-A7FA-F5C5567B[/FONT]2389


My goal is to activate this raid so that I can mount it and retrieve some files. My knowledge of linux and the terminal are still vey limited. If there is a way to fix the metadata so I could activate the raid that would be useful.  If there is any way to solve my problem or advice on it, it would appreciate that feedback. I can provide any follow-up information and would like to thank you for reading my post.


    
[COLOR=#000080]~Aaron[/COLOR]

---

