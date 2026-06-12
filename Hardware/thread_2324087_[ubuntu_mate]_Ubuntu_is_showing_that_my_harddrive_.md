---
title: "[ubuntu_mate] Ubuntu is showing that my harddrive is nearly full when it shouldn't be"
date: 2016-05-10
forum: Hardware
---

### Post by jasminejacquelin on 2016-05-10
Hi y'all,
I'm completely stumped with this issue. When I check my system monitor it states that my root partition has 450 GB total, 61 GB free, 37.9 available, and 389 GB used. Thing is I have absolutely no idea how I could possibly have 389 GB used on the computer. So I checked the properties of a bunch of different folders on my computer including the file system and it stated that it only contained 241 GB of data in it, which is much more in line with what I'd expect. My home folder contains 236 GB of data on it. So where did the alleged 153 GB of additional data come from and where could it possibly be stored. My trash is empty, and I've tried just restarting the computer. I used to run Arch and recently decided to switch to Ubuntu because I found that after a few years I wasn't keeping up well enough with the rolling releases and wanted something more stable, but this has me totally confused :confused:

The only situation I've had thus far that I think could possibly be linked was while copying backed up data to my recent install I encountered an issue with my music where the computer was copying over about 3 times the amount of music that I actually had (again have no idea where the extra data even was) and it totaled about 150 GB if I remember correctly. I deleted all the music from my computer and tried importing it directly into rythmbox which somehow imported the appropriate 50 GB of music onto my computer. But again, I deleted the old files that were totaling to wayyy to much data and emptied the trash. Actually I believe I just deleted the files in terminal with rm -r

Thanks

My theory as of the moment is that while backing up files there must have been a mess up and some broken, but not visible files were made and can't be deleted because they aren't visible? I have no idea how I would locate these files and delete them though, they don't show up with ls -a and I would've thought they would all have gotten deleted when I deleted the whole folder they would have been in...

---

### Post by weatherman2 on 2016-05-10
Open a terminal (Ctrl Alt t keys) and type these commands:

```

df
sudo parted -l

```

and please provide the output here.

---

### Post by jasminejacquelin on 2016-05-10
```
df
Filesystem                        1K-blocks      Used Available Use% Mounted on
udev                                3902472         0   3902472   0% /dev
tmpfs                                784504     17796    766708   3% /run
/dev/mapper/ubuntu--mate--vg-root 472165672 408447936  39710056  92% /
tmpfs                               3922512      1664   3920848   1% /dev/shm
tmpfs                                  5120         4      5116   1% /run/lock
tmpfs                               3922512         0   3922512   0% /sys/fs/cgroup
/dev/sda1                            482922    107302    350686  24% /boot
tmpfs                                784504        72    784432   1% /run/user/1000

sudo parted -l
[sudo] password for jazzy: 
Model: ATA HGST HTS725050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  512MB  511MB  primary   ext2         boot
 2      513MB   500GB  500GB  extended
 5      513MB   500GB  500GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--mate--vg-swap_1: 8250MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  8250MB  8250MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--mate--vg-root: 491GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  491GB  491GB  ext4


Model: SD SL64G (sd/mmc)
Disk /dev/mmcblk0: 62.6GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  62.6GB  62.6GB  fat32              msftdata
```

---

### Post by Bucky Ball on 2016-05-10
Have you looked in trash? Sometimes large files get in there and are either forgotten or them getting their is unnoticed.

PS: Please use code tags for terminal output. I have added a set in your previous post. See the green link in my signature at bottom of this post for how.

---

### Post by jasminejacquelin on 2016-05-10
> **jasminejacquelin said:**
>  My trash is empty, and I've tried just restarting the computer. .

---

### Post by weatherman2 on 2016-05-10
OK, you have only one Linux partition and it is indeed almost full.

Now you need to find the largest files and folders.  Here are some helpful suggestions:

[http://www.cyberciti.biz/faq/how-do-i-find-the-largest-filesdirectories-on-a-linuxunixbsd-filesystem/](http://www.cyberciti.biz/faq/how-do-i-find-the-largest-filesdirectories-on-a-linuxunixbsd-filesystem/)

---

### Post by Yellow Pasque on 2016-05-10
[https://help.ubuntu.com/community/Baobab](https://help.ubuntu.com/community/Baobab)

EDIT: I didn't realize MATE had its own disk usage analyzer, but it is in the mate-utils package, which is probably installed by default on your system. Look for the usage analyzer in your menu,

---

### Post by jasminejacquelin on 2016-05-11
Thank you weatherman2! 
It turns out it was indeed the music files I  had deleted. I had emptied the trash, but the file permissions didn't  allow them to be fully deleted so they still existed in  .local/share/Trash/expunged/

---

