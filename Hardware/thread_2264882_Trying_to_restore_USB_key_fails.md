---
title: "Trying to restore USB key fails"
date: 2015-02-10
forum: Hardware
---

### Post by coldraven on 2015-02-10
Last weekend I got my first ever car stereo that has an USB port. Hooray I thought and ran off to copy some music to a memory stick.
It worked beautifully and I drove around listening to some great tracks.
Yesterday I copied five more tracks to the stick, clicked the eject button and pulled it out. Now the stereo cannot detect any music at all.
I tried deleting the partition with gparted but that failed. See here:
[https://picasaweb.google.com/102130182469464429363/Errors?authuser=0&feat=directlink](https://picasaweb.google.com/102130182469464429363/Errors?authuser=0&feat=directlink)


I ran ```
sudo fsck.vfat -r /dev/sdb1
```which found some bad files and made them (IIRC) zero length. 
I ran ```
 sudo dosfsck -w -r -l -a -v -t /dev/sdb1
``` which found and relocated some clusters.

Still not working correctly even though I could play some tracks on my laptop.
I ran testdisk which found the partition OK but did not make any difference. If I try copying to the drive it goes read-only.

So now I try fdisk
```

#fdisk -l
Disk /dev/sdb: 8019 MB, 8019509248 bytes
134 heads, 28 sectors/track, 4174 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    15663103     7830528   83  Linux

```

```
# fdisk /dev/sdb

Command (m for help): d
Selected partition 1

Command (m for help): d
No partition is defined yet!

Command (m for help): n
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): 
Using default response p
Partition number (1-4, default 1): 
Using default value 1
First sector (2048-15663103, default 2048): 
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-15663103, default 15663103): 
Using default value 15663103

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.


```

I rebooted and tried again but got the same result, something is keeping the device busy and all the mp3s are still intact on the drive :(
Any ideas why?

---

### Post by sudodus on 2015-02-11
If your pendrive is read-only maybe it is failing with the 'gridlock' symptom. Or if you are lucky, something is confused in the partition table or file system. Try to wipe the first megabyte and after that re-format it. Or try to wipe the whole device. See this link, which might help with some tips and explanations

[http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

### Post by coldraven on 2015-02-11
Thanks sudodus, I followed your link to here and wiped the first megabyte.
[https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device)

I unplugged the stick and plugged it back in.
Then gparted saw the drive as unallocated, successfully created a new filesystem (msdos) and finally a FAT32 partition.

I will mark this a solved but i wonder if it was cased by a bug in Nautilus.
Last week I was copying files to a different stick that has an LED activity light. After pressing the eject button the light continued to flash for five or six seconds.
If I had pulled out promptly it would have corrupted something. What happened to the "It is now safe to remove...." message?

---

### Post by sudodus on 2015-02-11
That might have caused your problem. I usually unmount from a terminal window and wait until the prompt returns. the umount command runs sync before finishing and letting the terminal window return to prompt, so it should be safe. I don't know about Nautilus, but it *should* keep the eject symbol until the buffers are flashed and the drive is really unmounted.

On the other hand, I have at least one old pendrive, that keeps flashing after the umount command has finished and the terminal window has returned to prompt. I don't know what kind of activity is going on in such cases, maybe some kind of rematching of the flash memory cells to logical drive space blocks. And I'm afraid such activity might be sensitive to unplugging.

---

### Post by coldraven on 2015-02-12
I'm tempted to click the eject button in the middle of copying a large file to see what happens.
On the other hand I don't want to mess up my only other good pendrive. :(
Is it possible to capture stdout info from Nautilus? That way I could see if the pendrive activity matched the eject process.

---

### Post by sudodus on 2015-02-12
Install iotop

```
sudo apt-get install iotop
```

and watch the activity from a separate terminal window with

```
sudo iotop -o
```

---

