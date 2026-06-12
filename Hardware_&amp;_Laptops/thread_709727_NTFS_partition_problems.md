---
title: "NTFS partition problems"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by jon_z on 2008-02-27
I have an NTFS partition with lots of important information.  the partition is listed below:

```
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49214920

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3194    25655773+  83  Linux
/dev/hda2            6678       24320   141717397+   7  HPFS/NTFS
/dev/hda3            3195        6677    27977197+   5  Extended
/dev/hda5            3339        6677    26820486    b  W95 FAT32
/dev/hda6            3195        3338     1156617   82  Linux swap / Solaris

```

/dev/hda2 is the NTFS partition.  This is not a bootable windowsxp partition, just a by-product of former windows install.   After fresh installing 7.10, i attempted to mount this partition.

```
jon@Geologic:~$ sudo mount /dev/hda2 -t ntfs-3g /media/Media
NTFS signature is missing.
Failed to mount '/dev/hda2': Invalid argument
The device '/dev/hda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

alright, time to run some tests to see what is wrong:

```
jon@Geologic:~$ sudo e2fsck -f /dev/hda2
e2fsck 1.40.2 (12-Jul-2007)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/hda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

alright, brick wall.. lets try something else:

```

jon@Geologic:~$ sudo e2fsck -f -y -v /dev/hda2
e2fsck 1.40.2 (12-Jul-2007)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/hda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

it seems that I have attempted to run all of the serious repairs and checks to get this drive up and running, and i would hate to loose all of the files on there.  I'm a geology student and geologic maps for my thesis are on there sooo it is kind of important that i get them off.

If anyone has any ideas what to do, i would really appreciate the help.

---

### Post by Rocket2DMn on 2008-02-27
The only suggestion I can think of without pulling the drive out and trying to mount it on a windows computer is to try using *ntfsfix* from the *ntfsprogs* package.
Probably something like
```
sudo ntfsfix /dev/sda2
```
Then try remounting.

---

### Post by jon_z on 2008-02-27
```
jon@Geologic:~$ sudo ntfsfix /dev/sda2
Mounting volume... Failed to startup volume : Invalid argument
FAILED
Attempting to correct errors... FAILED
Failed to startup volume : Invalid argument
Volume is corrupt. You should run chkdsk.

```

---

### Post by Rocket2DMn on 2008-02-27
OK, if that ntfs partition doesn't have windows installed on it, you need to take the drive out and put it into a windows computer and run chkdsk on it.  It may also be possible to put in a windows cd, boot from it and enter the recovery console.  From there you might be able to chkdsk, though you'll have to look up how to do that to get the correct drive letter (if it's even possible).
If the drive DOES have windows, try booting into it.

---

### Post by TSandman on 2008-02-27
I got the same error msg today...

Got it working again tho:  while using ntfs-config, I saw that it changed from using NTFS-3G fs type to FUSEBLK...   so I took a look at /etc/fstab to see what changed and 'lo and behold!

Originally, it was:
*/dev/sda5 /media/Triton **ntfs-3g defaults,force,locale=en_CA.UTF-8 0 0***

Now it is:
*/dev/sda5 /media/Triton **auto nouser,noauto,noatime,atime,noauto,rw,nodev,exec,suid 0 0***

I modified every entry regarding NTFS partition that I had and everything's working now.

---

### Post by jon_z on 2008-02-27
attempting: 
```
Originally, it was:
/dev/sda5 /media/Triton ntfs-3g defaults,force,locale=en_CA.UTF-8 0 0

Now it is:
/dev/sda5 /media/Triton auto nouser,noauto,noatime,atime,noauto,rw,nodev,exec,s uid 0 0
```

did not work.. says error on line 9 which is what the fstab entry is.  I have it formatted correctly too i believe:

```
/dev/hda2	/media/Media 	auto 	nouser,noauto,noatime,atime,noauto,rw,nodev,exec,s uid 0	 0
```

I will see what I can do about throwing this HD into another machine; I just fear that there is not enough hard drive space on the machine I would have a chance to put it into to hold everything, although i can network send it to this machine itself, for it has an empty 250 gig hard drive in it as well.

Thank you for your help, keep track of this I will update you when I attempt this;  Any other suggestions are welcome.

---

