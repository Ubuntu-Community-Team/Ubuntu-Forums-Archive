---
title: "How to Add/Auto Mount Linux Partitions fstab ext3"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by meka4996 on 2009-10-25
How to Add/Auto Mount Linux Partitions fstab ext3

------------==update 21 Nov 09
Mounting partitions temporarily, to see if it works
```
$ cd /mnt
```
```
$ sudo mkdir /mnt/dataYZY
```
```
$ sudo mount /dev/XYZ /mnt/dataXYZ
```  ...to mount partition, XYZ can be sda1, or hdb2, ..
```
$ df -h
```  ... check if it's mounted
```
$ ls dataXYZ
``` ... also use GUI to check if it's the right partition
```
$ sudo umount -a
``` ... to un-mount all but not going to un-mount the running distro's / partition
```
$ df -h
```  ... checking it is indeed un-mounted
```
$ sudo mkfs.ext3 /dev/XYZ
```  ... to format Partitions to ext3
```
$ sudo mount /dev/XYZ /mnt/dataXYZ
```
```
$ df -h
```
... check if it's mounted
If all is well and you decide to make it permanent, then continue on the following...

---------------==
1) Un-mount all devices
```
$ sudo umount -a  
```
... check it by "df -h", seeing it is indeed un-mounted

2) Make a folder in /media or /mnt, NOT under /home!!
under /mnt (no icon on your desktop, hiding partitions for guest users) or under /media (showing icon on your desktop). 
```
$ sudo mkdir /mnt/datasdb7 
```

3) Get the partition uuid
```
$ sudo blkid  
```

4) Back up the fstab file.
```
$ sudo cp /etc/fstab /etc/fstab.old22june09 
```
check if the new file fstab.old22june09 is actually there by 
```
$ less /etc/fstab.old22june09 
```
Press q to quit

5) Open the fstab file
```
$ sudo gedit /etc/fstab 
```

6) Add the following line in /etc/fstab
# /dev/sdb7
UUID=5da3c09a-8984-4d27-88b6-55d322203e08 /mnt/datasdb7         ext3    relatime,errors=remount-ro 0       1

[http://blogs.koolwal.net/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/](http://blogs.koolwal.net/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/)
3. relatime &#8211; A filesystem mount with this option causes the access time to be updated if they are (before the update has occurred) earlier than the modification time. This significantly cuts down the writes caused by atime updates. However not many people use this option because they are simply not aware of it.

To summarize, relatime is a good compromise between  atime (most expensive) and noatime (least expensive).

[http://ubuntuforums.org/showthread.php?t=199587](http://ubuntuforums.org/showthread.php?t=199587)
errors=remount-ro will mount the filesystem in read-only mode in case there are any problems with it. This prevents you from potentially losing data using a bad filesystem.

If this happened to one of your partitions, you should probably boot from a livecd or floppy (if it's not on your root partition, you can boot on recovery mode) and then run fsck on the affected disk.

7) re-login/reboot ubuntu

8_1) check where the partition mount point is: 
```
$ df -h 
```
   check the partition ownership: ```
$ ls -l /mnt 
```

8_2) change the owner of the folder using chown. 
```
$ sudo chown your_username:your_username /mnt/dataXYZ 
```
```
$ sudo chown JohnK:JohnK /mnt/datasdbXYZ 
```
```
$ sudo chown -R JohnK:JohnK /mnt/datasdbXYZ 
```
-R is to change the permission on all files that are in the subdirectories.[Recurrsive function]
```
$ sudo chown JohnK:JohnK myfile 
```

##Note: Fat32 partitions do not support permissions on files

8_3) copy a file[with size of a few MB] into it, then check if the disk space of that partition decreases: 
```
$ df -h 
```

9) Then create a symbolic link [they only appear to be folders inside a partition...]
right click on the folder-> make link-> cut and paste links to your home directory
1link to datasda8/home/userXYZ

10) Boot up each linux os for testing.

References:
How to edit and understand /etc/fstab - 1.1
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

GUI Fstab Editing with PySDM
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Can access mounted data partition only as root
[http://ubuntuforums.org/archive/index.php/t-996665.html](http://ubuntuforums.org/archive/index.php/t-996665.html)

To revoke partition authorization:
System-> Administration-> Authorizations-> Storage: Mount File Systems From Internal Drives-> Revoke

---

