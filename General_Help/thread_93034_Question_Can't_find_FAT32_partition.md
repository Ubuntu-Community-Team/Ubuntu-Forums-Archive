---
title: "Question: Can't find FAT32 partition"
date: 2005-11-21
forum: General Help
---

### Post by Listoff78 on 2005-11-21
I am dual booting Ubuntu and Windows XP.  I have:

10GB NTFS partition for XP
10GB EXT3 partition for Ubuntu
40GB FAT32 partition for data to share between the two

I can see the FAT32 partition in XP, but when I boot to Ubuntu, I can't find this partition anywhere.  I know I must be missing something simple, but I'm super new to Linux.  Thank you in advance for any help that can be offered!

-Mike

---

### Post by adwait on 2005-11-21
You need to mount it. Execute
```
sudo fdisk -l
```
and post the output here. 
Also post the output of
```
sudo df
```

---

### Post by MrCheese on 2005-11-21
[QUOTE=Listoff78]I am dual booting Ubuntu and Windows XP.  I have:

10GB NTFS partition for XP
10GB EXT3 partition for Ubuntu
40GB FAT32 partition for data to share between the two

I can see the FAT32 partition in XP, but when I boot to Ubuntu, I can't find this partition anywhere.  I know I must be missing something simple, but I'm super new to Linux.  Thank you in advance for any help that can be offered!

-Mike[/QUOTE]

If that's the order of the partitions on the disk the data partition will be /dev/hda3 (to verify try "fdisk /dev/hda", "p" to inspect the partition table and q to quit without making changes). You can try manually mounting the partition : 

first create a mountpoint : sudo mkdir /mount/data
then mount the data       : sudo mount -t vfat /dev/hda3 /mnt/data

If that works ok you can edit /etc/fstab and put in a line to automount on boot :

/dev/hda3 /mnt/data vfat user,rw 0 0 (copy the format of the preceding lines) making sure you hit <return> at the end of the line.

See [http://www.ubuntuguide.org/#mountunmountfat]("http://www.ubuntuguide.org/#mountunmountfat") for details.

---

### Post by Listoff78 on 2005-11-21
It's weird, I went into System, Administration, Disk, and verified that it was a virtual Windows disk.  When I tried to enable it, I does nothing.  It says, Inaccessible and Free space not available.  I will try the above and see how it goes.

Thanks!
Mike

---

### Post by Listoff78 on 2005-11-21
Success!  I got the drive to mount and I added the code to allow it to mount automatically at bootup!  Thank you!

Only one issue remains.  For some reason, two or three folders are not giving me write access and won't let me change the permisisons saying I'm not the owner.  How do I overcome this?

Once this is resolved, I think I'm set to go!
Thanks!
Mike

---

