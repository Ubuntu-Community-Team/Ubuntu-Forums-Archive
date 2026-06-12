---
title: "Two Unmountable HDDs"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by derrekito on 2007-06-18
I have 7 hard drives hooked up to my system.  I am dual booting with windows and all my drives work on that OS.  however, when I switch to ubuntu all but TWO hdds get detected and are auto mounted.  Now the two that are not auto mounted ARE detected, but when I try to mount them Gnome spits out a:

```


Cannot mount volume.

Unable to mount the volume.

Details
  mount: Operation not supported


```

the two hard drives I suspect are connected on the same cable, however I am not postive.  Also, they are both on IDE interface, however I am unsure if they are on the primary or secondary ide.

I am running on a Asus A8N32-SLI Deluxe.

any help is of course appreciated!

---

### Post by derrekito on 2007-06-20
Bump

---

### Post by derrekito on 2007-06-20
> **derrekito said:**
> Bump
Ironically enough, these two hard drives are vital to me being able to run my OS choice, otherwise I have to boot back into windows so the people I live with can watch their movies etc.  Also it is hard not having access to 600 GB of data.

---

### Post by derrekito on 2007-06-24
bump :(

---

### Post by elsaturnino on 2007-06-24
Hrmm... what does your /etc/fstab look like?

---

### Post by derrekito on 2007-06-24
> **elsaturnino said:**
> Hrmm... what does your /etc/fstab look like?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda1 :
UUID=ace36df0-37d4-4852-a835-ac7c3239b7a6	/	ext3	defaults,errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=7E34C3E234C39B91	/media/sdb1	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdc1 :
UUID=8C84CF3784CF2316	/media/Audio	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdd1 :
UUID=102CC1BF2CC1A058	/media/Anime	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/hdd1 :
UUID=C480FA8880FA806A	/media/Sort	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda5 :
UUID=7e55605a-6aa5-4a3c-ae22-1c71060bdeca	none	swap	sw	0	0
/dev/hdc	/media/cdrom0	udf,iso9660	user,noauto	0	0

##	End	of	Automatix	mounted	partitions


```
sda1 is linux - sata drive
sdb1 is my windows partition. - sata drive
sdc1 is music - it works
sdd1 is anime - it works - USB drive
hdd1 is a misc drive - it works

There are two drives not on the fstab - they do show up on the places side bar in gnome, but i cannot mount.  Also I have no idea what the device names are.

I only have three sata drives.  One IDE drive hooked up via USB.  the rest are IDE channels.

under /dev I do have a hda, hdb, hdc, and hdd device.

```

derrekito@derrekito-desktop:/dev$ ls hd*
hda  hda1  hdb  hdb1  hdc  hdd  hdd1
derrekito@derrekito-desktop:/dev$ sudo mount /dev/hda1 /media/Video
mount: Operation not supported
derrekito@derrekito-desktop:/dev$ sudo mount /dev/hdb1 /media/Video
mount: Operation not supported
derrekito@derrekito-desktop:/dev$ sudo mount /dev/hdc /media/Video
mount: No medium found
derrekito@derrekito-desktop:/dev$ sudo mount /dev/hdd1 /media/Video
mount: /dev/hdd1 already mounted or /media/Video busy

```

hdd1 is already mounted - it is my "Sort" drive... Misc.

hdc doesnt exist, so I assume the other two drives that I get the SAME error in gnome are the correct drives.

---

### Post by elsaturnino on 2007-06-24
The lack of entries in your fstab might be the culprit.

What do you get when you run the following commands?

```
dmesg | grep hda
dmesg | grep hdb
```

---

### Post by derrekito on 2007-06-24
> **elsaturnino said:**
> The lack of entries in your fstab might be the culprit.

What do you get when you run the following commands?

```
dmesg | grep hda
dmesg | grep hdb
```

The other drives worked prior to me adding them to the fstab, however these two drives never worked.

```

derrekito@derrekito-desktop:~$ dmesg | grep hda
[   53.806739]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[   54.098305] hda: WDC WD3200JB-22KFA0, ATA DISK drive
[   60.375347] hda: max request size: 512KiB
[   60.375682] hda: 625142448 sectors (320072 MB) w/8192KiB Cache, CHS=38913/255/63, UDMA(100)
[   60.375756] hda: cache flushes supported
[   60.375783]  hda: hda1

```
```

derrekito@derrekito-desktop:~$ dmesg | grep hdb
[   53.806739]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[   54.378022] hdb: WDC WD3000JB-00KFA0, ATA DISK drive
[   60.393603] hdb: max request size: 512KiB
[   60.393674] hdb: 586072368 sectors (300069 MB) w/8192KiB Cache, CHS=36481/255/63, UDMA(100)
[   60.393746] hdb: cache flushes supported
[   60.393765]  hdb: hdb1

```

All my drives except the linux partiton is running on NTFS.  I also wanted to note that these two hard drvies do not show up under the NTFS Configuration Tool under System --> Administration

I tried mounting it via fstab, and now look what I get:

```

derrekito@derrekito-desktop:~$ dmesg | grep hda
[   53.806739]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[   54.098305] hda: WDC WD3200JB-22KFA0, ATA DISK drive
[   60.375347] hda: max request size: 512KiB
[   60.375682] hda: 625142448 sectors (320072 MB) w/8192KiB Cache, CHS=38913/255/63, UDMA(100)
[   60.375756] hda: cache flushes supported
[   60.375783]  hda: hda1
[  580.876798] ReiserFS: hda1: found reiserfs format "3.6" with standard journal
[  580.876814] ReiserFS: hda1: using ordered data mode
[  580.889572] ReiserFS: hda1: warning: sh-461: journal_init: wrong transaction max size (649941668). Changed to 1024
[  580.889579] ReiserFS: hda1: journal params: device hda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 4024615715, max trans age 30
[  580.890918] ReiserFS: hda1: checking transaction log (hda1)
[  580.910899] ReiserFS: hda1: warning: vs-5150: search_by_key: invalid format found in block 39002529. Fsck?
[  580.910903] ReiserFS: hda1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [1 2 0x0 SD]
[  580.911321] ReiserFS: hda1: Using r5 hash to sort names
[  580.911426] ReiserFS: hda1: warning: xattrs/ACLs enabled and couldn't find/create .reiserfs_priv. Failing mount.
derrekito@derrekito-desktop:~$ dmesg | grep hdb
[   53.806739]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[   54.378022] hdb: WDC WD3000JB-00KFA0, ATA DISK drive
[   60.393603] hdb: max request size: 512KiB
[   60.393674] hdb: 586072368 sectors (300069 MB) w/8192KiB Cache, CHS=36481/255/63, UDMA(100)
[   60.393746] hdb: cache flushes supported
[   60.393765]  hdb: hdb1
[  581.037740] ReiserFS: hdb1: found reiserfs format "3.6" with standard journal
[  581.037757] ReiserFS: hdb1: using ordered data mode
[  581.056225] ReiserFS: hdb1: warning: sh-461: journal_init: wrong transaction max size (4035313740). Changed to 1024
[  581.056233] ReiserFS: hdb1: journal params: device hdb1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 307486811, max trans age 30
[  581.057368] ReiserFS: hdb1: checking transaction log (hdb1)
[  581.616795] ReiserFS: hdb1: warning: vs-5150: search_by_key: invalid format found in block 32309251. Fsck?
[  581.616799] ReiserFS: hdb1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [1 2 0x0 SD]
[  581.616818] ReiserFS: hdb1: Using r5 hash to sort names
[  581.616833] ReiserFS: hdb1: warning: xattrs/ACLs enabled and couldn't find/create .reiserfs_priv. Failing mount.

```

why is it picking up a reiserFS?

Also I was trying to determine the UUID of the devices and I get:
```

derrekito@derrekito-desktop:~$ sudo vol_id -u /dev/hda
/dev/hda: unknown volume type
derrekito@derrekito-desktop:~$ sudo vol_id -u /dev/hdb
/dev/hdb: unknown volume type

```

The partitions work fine in windows, and have little reason to beleive that the partition is corrupt or anything.  Also it is unfortunatly not in my best interest to try to back up 600 gigs or so and reformat the HDDs... What do you think is going on.

---

### Post by elsaturnino on 2007-06-24
I'm not too sure what is going on here. How did you go about using fstab to try to mount the disks? You also might want to try the "blkid" command to find the UUID.

---

### Post by derrekito on 2007-06-24
> **elsaturnino said:**
> I'm not too sure what is going on here. How did you go about using fstab to try to mount the disks? You also might want to try the "blkid" command to find the UUID.

```

blkid
/dev/sda1: UUID="ace36df0-37d4-4852-a835-ac7c3239b7a6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="7e55605a-6aa5-4a3c-ae22-1c71060bdeca" TYPE="swap" 
/dev/sdb1: TYPE="ntfs" 
/dev/sdc1: TYPE="ntfs" 
/dev/sdd1: TYPE="ntfs" 
/dev/hda1: TYPE="ntfs" 
/dev/hdb1: TYPE="ntfs" 
/dev/hdd1: TYPE="ntfs" 

```
actually to mount it via fstab i messed up, didnt work at all becuase I was re mounting another drive to a different point, I need the UUID.

---

### Post by elsaturnino on 2007-06-24
You should be able to use /dev/hda1 and /dev/hdb1 instead of the UUIDs. Give it a try and see what happens.

---

### Post by derrekito on 2007-06-24
You sir are a bad ***. IT WORKED!  Now something strange happened, my USB hard drive is no longer being auto mounted at start like the rest of them. and I also lost rights to the drive.  I cannot even look at what is inside without being root.

---

### Post by derrekito on 2007-06-24
I went into gksudo nautilus to change the folder's permission, however I get an error stating the the Hard drive is read-only.  Any idea how this happened?  It happened after I got the other two drives working.

Here if my update fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda1 :
UUID=ace36df0-37d4-4852-a835-ac7c3239b7a6    /    ext3    defaults,errors=remount-ro    0    1
#Entry for /dev/sdb1 :
UUID=7E34C3E234C39B91    /media/sdb1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdc1 :
UUID=8C84CF3784CF2316    /media/Audio    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdd1 :
UUID=102CC1BF2CC1A058    /media/Anime    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/hdd1 :
UUID=C480FA8880FA806A    /media/Sort    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/hda1 :
/dev/hda1               /media/TV    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/hdb1 :
/dev/hdb1               /media/Video    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/hdc :
UUID=7e55605a-6aa5-4a3c-ae22-1c71060bdeca    none    swap    sw    0    0
/dev/hdc    /media/cdrom0    udf,iso9660    user,noauto    0    0

##    End    of    Automatix    mounted    partitions


```the drive in question is mounted at /media/Anime which is device /dev/sdd1.





***_EDIT:_***  I moved the hdd1 entry down, then reboot... boom it works.  Whateva.  Thank YOU SO MUCH!

---

### Post by elsaturnino on 2007-06-24
Glad to see ya got it workin! :)

---

