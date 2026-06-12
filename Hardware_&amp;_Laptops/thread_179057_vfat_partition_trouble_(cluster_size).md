---
title: "vfat partition trouble (cluster size?)"
date: 2006-05-18
forum: Hardware &amp; Laptops
---

### Post by anemetz on 2006-05-18
I am afraid I made a serious mistake. I was attempting to get LVM+XFS setup for a new Mythtv setup I was making. I put all my personal data/media files onto a large 250GB fat32 hard drive (hdb1) so I could convert my other two drives to XFS. 

Everything went fine, and I got two XFS partitioned correctly (hdd1 & hda4). I was going to copy my data onto these newly reformated partitions such that I could format my last fat32 drive (hdb1) to XFS. 

This is where the problems began.

I had about 150GB of data to move. Yet both my XFS partitions were smaller than that. I decided to use LVM. I typed:

> 
# umount -a
# pvcreate mythvg /dev/**hdb1**

Crap.... I had almost accidentally added my vfat partition to the LVM. I tried:
> # mount -a

And the drive wasn't mounting. I freaked out, and decided to get the partition off the LVM by using the command "# pvremove /dev/hdb1"

Which was successfull.

But then, when I attempted to mount -a, my results weren't so fantastic:
> root@ubuntuserver:~# mount -a
mount: wrong fs type, bad option, **bad superblock on /dev/hdb1,**
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


**My dmesg | tail:**
> root@ubuntuserver:~# dmesg | tail
[4295014.937000] FAT: bogus number of reserved sectors
[4295014.938000] VFS: Can't find a valid FAT filesystem on dev hdb1.


So it seems my vfat partition is in serious trouble. I've searched other threads in the ubuntuforums, and searched through all the google results I could find. I couldn't find a solution. 

I know my data is still there, I just can't get to it ](*,) 


Any suggestions would be extremely appreciated. [-o<

---

### Post by nanotube on 2006-05-18
have you tried running fsck on it?

---

### Post by anemetz on 2006-05-18
HAHA! good idea nanotube! thanks :)

Now I am almost positive the problem has to do with the cluster size being set to zero.

I attempted to fsck.vfat the partition and these are the results:
> root@ubuntuserver:~# fsck.vfat /dev/hdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
**Logical sector size is zero.**


I also attempted to get the drive mounted in linux & OsX using my external HD case, which didn't lead to any new insights other than that the partition intact, just inaccessible. (ie it wasnt re-formated)


Now I have absolutly no idea what to do, or how to (if its possible) ** set the cluster size back to its original number.**

:-|

---

### Post by nanotube on 2006-05-19
well, try running
```
sudo fsck.vfat -a /dev/hdb1
```
the -a option is so that it automatically attempts to repair, and the sudo is just in case it needs root privileges to change things on the partition. 
give it a shot, and see what happens.

---

### Post by anemetz on 2006-05-19
[QUOTE=nanotube]well, try running
```
sudo fsck.vfat -a /dev/hdb1
```
the -a option is so that it automatically attempts to repair, and the sudo is just in case it needs root privileges to change things on the partition. 
give it a shot, and see what happens.[/QUOTE]

nothing, same error. hmm...

---

### Post by nanotube on 2006-05-20
[QUOTE=anemetz]nothing, same error. hmm...[/QUOTE]
hmm indeed. i regret to say i am out of ideas on this one... anybody else?

---

### Post by Muffinn on 2006-05-22
Solution:

I was reading the "# man fsck" file and it suggested that with fat32 partitions you should use software made specifically for windows partitions.

I re-installed windows XP, the OS recognized the drive as healthy. Checked it with chkdsk and received an error stating the partition was a "RAW filesystem"

Googled it, got sent to [this microsoft support page.]("http://support.microsoft.com/?kbid=247575")

Followed the directions, which basicly instructs you to replace the bootsector (sector 0) of the drive with the backup on sector 6. And everything is back to normal 8) 

Thanks for all the help (esp. you, nanotube), and I hope this thread may help someone with the same issue in the future.

Now to re-install Ubuntu :twisted:

---

### Post by nanotube on 2006-05-23
i'm glad it finally worked out. i wonder why the linux fsck util doesn't handle this case...
at any rate, thanks for sharing your solution, i'm sure it will come in handy to someone eventually. :)

---

### Post by onlymee on 2006-05-30
[QUOTE=Muffinn]Thanks for all the help (esp. you, nanotube), and I hope this thread may help someone with the same issue in the future.[/QUOTE]

I came across this thread having have the same 
```
Logical sector size is zero.
``` 
error from fsck.vfat

My problem is actually with a 512Mb USB memory stick (and mp3 player), I read your posts and looked at the Microsoft link but I only have XP on my dual boot laptop and I worried if the Dskprobe.exe tool would work or even exist. nb. there is a warning about incompatibilities on one of the linked pages.  Anyway I wanted a Linux only solution.  I guessed ad it worked.  
I started by taking a backup of the drives partition (detected as /dev/sdb1) to my hard disk:

```
dd if=/dev/sdb1 of=backup_mp3.fat32.img bs=512 count=1012942 conv=noerror,sync

```

The block size and count settings were simply copied from the output of sfdisk.  sfdisk reports in 1k blocks but using 512bytes (one sector) and doubling the number of blocks, one guarantees that at worst one sector is lost where there is an I/O error.  You could probably use smaller bu I'm not sure it will make and difference since I believe sectors are atomic.

Not also this is not a perfect backup as unreadable parts are replaced by zeros (that's what sync does)

(You could skip the backup and test and perform the operation straight on the disk, but I am being cautious)

Anyway, then read sector 6 from the backup (or the disk):

```
dd if=backup_mp3.fat32.img of=sector6.bin bs=512 count=1 skip=6 conv=noerror,sync

```

Now write that sector back over sector 0 of the backup. (notice the notrunc!!)

```
dd if=sector6.bin of=backup_mp3.fat32.img bs=512 count=1 conv=noerror,sync,notrunc

```

Now we can test the fixed partition with the loop back device.  If you have the loop device compiled into your kernel as a module you need to load it:
```

modprobe loop

```
Set up the loop back device, and mount it:
```

mkdir /media/vfat_backup
losetup /dev/loop0 /media/vfat_backup
mount -t vfat /dev/loop0 /media/vfat_backup
ls -l /media/vfat_backup

```
Voila!
Really one should fix any file system errors:
```

umount /dev/loop0
fsck.vfat /dev/loop0
mount -t vfat /dev/loop0 /media/vfat_backup
ls -l /media/vfat_backup

```
Now there after you can simply rewrite the sector 0 on the real device, fsck, and mount it:
```
dd if=sector6.bin of=/dev/sdb1 bs=512 count=1 conv=noerror,sync,notrunc
mount -t vfat /dev/sdb1 /media/vfat_device

```

This will certainly allow you to read your files in the backup, but, if the real device in not just corrupt but actually unwritable in sector 0 it may be necessary to repartition+reformat the disk and recover your files from the backup mounted via the loop back device.

Hope that helps someone else.

---

### Post by fang2415 on 2007-02-25
Onlymee, thanks a bunch for the walk-through.  It took me about a half hour to understand, but taught me a lot about how to use the essentials of the approach I need -- dd and losetup.  (Unfortunately I wasn't as lucky as you were -- looks like something's gone wrong with my backup sector as well...)

I think there is one slight error in your code, though.  Where you've got
> 
Set up the loop back device, and mount it:
```

mkdir /media/vfat_backup
losetup /dev/loop0 /media/vfat_backup
mount -t vfat /dev/loop0 /media/vfat_backup
ls -l /media/vfat_backup

```


...I'm guessing you meant that second line to be:

```

losetup /dev/loop0 backup_mp3.fat32.img

```

I know the thread's pretty old, but just in case someone (like me) stumbles across it...

F2

---

