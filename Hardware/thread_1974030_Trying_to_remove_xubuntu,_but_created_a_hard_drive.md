---
title: "Trying to remove xubuntu, but created a hard drive problem"
date: 2012-05-05
forum: Hardware
---

### Post by likiud on 2012-05-05
I'm not sure what i could do and out of ideas. I think i screwed it up  myself. I have an older hp dv1660ca laptop. It runs Windows xp home  preinstalled.
 
 Here's what i did to screw it up. 
 
 I have xubuntu on it dual booting with winxp. Because my dad just  learned how to use computer i thought i should just remove the dual boot  and restore back to factory.  I used the hp recovery tool to restore  it. It removed linux but the HD was still not the full capacity (linux  used 20gb). 
 
 So i thought i could use disk management to delete and recreate the  partitions. I went in there deleted a partition.  There was 2 more  partitions i couldnt remove as it popped up an error.  I decided to try  removing it after rebooting. 
 
 When i reboot it, it wont boot back up.  It has the windows xp load  screen, and then the blue screen of death. shortly after it will reboot.   when it reboots it will still be like that.  safe mode is the same  thing.  i tried to boot into hp recovery, but it won't load either.  
 
 I don't have any hp recovery disks, but I have a windows xp pro disk.  i  could boot from the cd.  originally it can't find a hard disk and i  tried to repair in the recovery console or install windows xp .  So I  disabled SATA from the bios and ran it in legacy mode.  That worked and I  could go to recovery console.  
 
 I went to recovery console to try to fix the master boot record because  that's what i thought that went wrong.  When in recovery console, it  cannot find anything on the hard drive.  It just prompted to C:\.  I  can't get to windows directory so fixmbr wouldn't work.  I just exit and  rebooted back to windows setup.  
 
 When I tried to install windows again, it got me to the partition  screen.  at that screen it shows 76317 MB Disk 0 at Id 0 on bus 0 at  atapi <Setup cannot access this disk.> When I try to delete  partition or install it will create a blue screen of death.
 
I managed to get back to xubuntu via the live CD. When I got to gparted  it shows up there is 74gb of unallocated space and no partitions. I try  to create a partition from the unallocated space, it says there is no  partition table. When I went through the menu to create a partition  table it said this "this will erase all data on the entire disk  /dev/sda" . It also say default is to create an ms-dos partition table.  It allows me select through a drop down menu of other partition tables.
 
 I can see a 50gb file system on there too but I cant mount it.
 
 I dont want to erase the disk as I still want to keep the hp recovery partition.

 I am out of ideas now.  What I want to do is be able to boot back up,  recover the missing the hd space then use back the hp recovery to  restore back to original again.
 
 sorry if this is long, but i want to be as detailed as possible.  my  laptop was in very good working order before this happen and i am  confident the hard drive is still good.  any help is appreciated.

---

### Post by mips on 2012-05-05
From the ubuntu livecd post the output of **sudo fdisk -l**
You could also post a screenshot of Gparted (you can install gparted from the livecd).

---

### Post by likiud on 2012-05-05
output of sudo fdisk -l
fdisk: unable to seek on /dev/sda: Invalid argument
 
Heres a screenshot of gparted.
[http://db.tt/DLOpdmX2](http://db.tt/DLOpdmX2)

---

### Post by likiud on 2012-05-07
Bump...
Anyway, I figured sudo fdisk -l didn't work, so i googled up some stuff, and tried sudo parted -l
 
This is what it outputted. I had to type a few ignore commands
```
ubuntu@ubuntu:~$ sudo parted -l print
Error: Invalid argument during seek for read on /dev/sda                  
Retry/Ignore/Cancel? retry                                                
Error: Invalid argument during seek for read on /dev/sda                  
Retry/Ignore/Cancel? ignore
Error: Invalid partition table on /dev/sda -- wrong signature 9fea.       
Ignore/Cancel? ignore                                                     
Model: ATA HTS541080G9SA00 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
Number  Start   End     Size    Type      File system  Flags
1      32.3kB  50.4GB  50.4GB  primary   ntfs         boot
2      50.4GB  70.9GB  20.6GB  extended
3      70.9GB  78.9GB  8003MB  primary   fat32        lba
```
 
I'm thinking that number 1 is the main partition where windows is, 2 was the xubuntu partition that I originally installed it on, and 3 is the recovery partition. 
 
WIth the Live CD, I could access the 50GB partition and take the files out, but it doesn't see the 8GB partition.

---

### Post by ahallubuntu on 2012-05-07
The Linux partition appears to be gone.

Partition #1 is a primary partition, the Windows partition.
Partition #2 is an extended partition that probably had the Linux partition in it but now appears to be 20GB of unallocated space.
Partition #3 is probably the HP factory restore partition or a backup partition.

Partition #2 (extended) would have had logical partitions inside of it for Linux but they appear to be erased.

Not clear exactly what you did to mess things up, but the partition table appears to be corrupt.  This post suggests a way to fix it:

[http://techspalace.blogspot.com/2011/10/solved-invalid-partition-table-on.html](http://techspalace.blogspot.com/2011/10/solved-invalid-partition-table-on.html)

> sudo fdisk /dev/sda press p and then press w. You'll see a message "The partition table has been altered!".

---

