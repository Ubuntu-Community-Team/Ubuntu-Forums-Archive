---
title: "[SOLVED] Musicplayers forgetting mounted drives after reboot - Won't load music prope"
date: 2008-08-16
forum: General Help
---

### Post by jdiuqil on 2008-08-16
Greetings!

I'm a new Ubuntu user. I did a fresh install with Ubuntu 8.04. Everything has been going pretty swell, but I've been having a particular problem.

When I partitioned, I made 4 partitions. A Windows XP partition, a Ubuntu partition, a Swap partition, and a storage partition (Fat32) to store and share files between both OS. I did not not name them.

I noticed that with both my music players (Rhythm Box & Banshee), the music loads and plays fine. Once I reboot and load these programs again. I see my play list, I try to play but the music players can't seem to find the music. Once I open media and go to the storage partition (without even opening a file), it will "resync" my files and they will work again. 

Is there a way to fix this so? The following is a screen shot of the error I get and my partition names.

[IMG]http://img239.imageshack.us/img239/6674/errorlt2.png[/IMG]
[IMG]http://img244.imageshack.us/img244/4964/error2gt2.png[/IMG]

Thanks for your help!

---

### Post by drs305 on 2008-08-16
Are your drives set to automount? 
```
gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount 'true'
```

There are two other solutions I can think of. 
Have you tried to access the partition before running your music player? The external fat32 partition probably isn't mounted when the player tries to access it if you haven't. 

One way would be to write a script which first mounts the drive and then starts your music player. The problem would be that mounting would require 'sudo' unless you have an entry in fstab. If you have to do that anyway...

You could also include the partition in fstab so that it automounts on boot, if the problem is indeed that it is not mounted when the player tries to access it.

Create the mountpoint:
```
sudo mkdir /media/***mountpoint***
```
Add this line to fstab, making sure you have the correct device and mount points:
```
/dev/sd**aX** /media/***mountpoint*** vfat utf8,uid=1000,gid=1000,dmask=027,fmask=111 0 0
```

---

### Post by jdiuqil on 2008-08-16
How can I set automount? (or is it the steps you've listed?)

I am a new ubuntu/linux user, so I'm not that familiar with everything. But if I access the drive first, the music works.

So, I guess I have to figure out how to automount.

edit: I just tried "gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount 'true'" and it didn't change anything. What was this line suppose to do?

---

### Post by drs305 on 2008-08-16
If you run the first command in my previous post it will set the automount option. The command will work for external media - I am not sure if it would work with internal partitions. If it doesn't, your best bet is to work with fstab. It would appear your fat32 partition isn't included or at least not mounting your partition.

Since you say you are new to ubuntu, to get your fstab set up, please run these commands in terminal and post the results: ( -l is a small L)
```
cat /etc/fstab
sudo fdisk -l
sudo blkid
```

Also decide what you want the name of the mountpoint to be and include it in your post.

---

### Post by jdiuqil on 2008-08-16
jonnie@jonnie-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=525091c8-256b-498d-bffa-fb2ced307daa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=be7448f8-0d20-4d22-a3db-f058c545350c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
jonnie@jonnie-laptop:~$ sudo fdisk -l
[sudo] password for jonnie: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2772a4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3923    31511466    7  HPFS/NTFS
/dev/sda2            3924       10367    51761430    b  W95 FAT32
/dev/sda3           10857       12161    10482412+  83  Linux
/dev/sda4           10368       10856     3927892+  82  Linux swap / Solaris

Partition table entries are not in disk order
jonnie@jonnie-laptop:~$ sudo blkid
/dev/sda1: UUID="2A984DFC984DC753" TYPE="ntfs" 
/dev/sda2: UUID="48A5-02B3" TYPE="vfat" 
/dev/sda3: UUID="525091c8-256b-498d-bffa-fb2ced307daa" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="be7448f8-0d20-4d22-a3db-f058c545350c" 

-> I'd like the storage name to be just Storage Drive

THANKS!

---

### Post by drs305 on 2008-08-16
The fat32 partition wasn't mounting automatically because it wasn't listed in fstab.

Since you say you are pretty new, here is how to do it:
Make a backup of your fstab file and open with a text editor (example uses gedit):
```
sudo cp /etc/fstab /etc/fstab-backup
gksu gedit /etc/fstab
```

Add this line:
```
UUID=48A5-02B3 /media/Storage_Drive vfat utf8,uid=1000,gid=1000,dmask=027,fmask=111 0 0
```
Save the file.

Make the mount point. I've changed it to Storage_Drive. You can use "Storage Drive" with the format Storage\ Drive but it would be easier to avoid spaces. Suit yourself.  ;-)
```
sudo mkdir /media/Storage_Drive
```

Then unmount your drive and remount it. Check for any error messages and you should be set:
```
sudo umount /dev/sda2
sudo mount /dev/sda2
```


Added:
I noticed your NTFS windows partition also isn't listed in fstab. If you want to add it:

Add this line:
```
UUID=2A984DFC984DC753 /media/windows ntfs-3g utf8,uid=1000,gid=1000,dmask=027,fmask=111 0 0
```


Make the mount point. I've named it *windows*
```
sudo mkdir /media/windows
```

In answer to your question about what the 'gconf-editor...' command does - it sets it so any external media (flash drives,etc) automount when they are inserted. You can change the setting to 'false' and run the same command if you don't want then to automount.

---

### Post by jdiuqil on 2008-08-16
Worked like a charm! Thank you very much! Is there anyway to +rep you or something?

---

### Post by drs305 on 2008-08-16
> **jdiuqil said:**
> Worked like a charm! Thank you very much! Is there anyway to +rep you or something?

I will respond to your question as it will effect others. There are two things you can do. The most important is to mark the thread "SOLVED" once you have all your questions answered. You do this with the "Thread Tools" link at the top right of the original post.

Marking it solved does two things - it saves the time of those looking to help other users, and it also serves as a guide to those searching for answers either through the forum's search function or via Google. It saves the trouble of looking at problems for which no solution has been found.

The other thing, which is what you asked about, is accomplished by clicking the little gold star at the lower right of any post you find particularly enlightening.

One further note, both of these are fully reversible should things not turn out the way you thought!  ;-)

Welcome to ubuntu...

---

