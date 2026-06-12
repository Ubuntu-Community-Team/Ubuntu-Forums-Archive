---
title: "Spare Still Seen As Full"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by Eschguy on 2007-12-12
So I'm running 7.10 and I had a lot of stuff on my slave 120GB hdd. I moved it all over to my master drive once I was set up. However, though there is nothing on that drive, it still says there is 400MB of free space when there should be 120GB. So I figure I can just wipe the hard drive, but I have no idea how to go about that. Can anybody help?

---

### Post by Eschguy on 2007-12-14
It still has yet to be solved. If anybody has any ideas, please help.

---

### Post by taurus on 2007-12-14
You can unmount it first and use gparted (install it if you don't have it in System -> Administration) to reformat it.

What filesystem is does that harddrive use right now?

```
sudo fdisk -l
```

---

### Post by Eschguy on 2007-12-14
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20642064

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   5  Extended
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x153e032e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+   7  HPFS/NTFS

I don't even know how to read half of that

---

### Post by Eschguy on 2007-12-14
That was before using gparted. Afterwards I get:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20642064

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   5  Extended
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x153e032e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+  83  Linux

---

### Post by taurus on 2007-12-14
So looks like you have converted your /dev/hdb1 from ntfs filesystem to ext3.  Try to mount it and see what how space it has.

```
sudo mkdir /media/hdb1
sudo mount -t ext3 /dev/hdb1 /media/hdb1
df -h
```
Post the output of the last command here.

---

### Post by antbully on 2007-12-14
Ok, assuming you're *really sure* you've got everything off this disk, you can do as taurus suggests.  I don't know all the graphical commands, but I can tell you the command line way to do this.

1) Use hdparm to confirm you're really dealing with the right disk:
    "sudo -i /dev/hd[x]", where "[x]" is replaced with letter "a" or "b"

2) It isn't clear which drive is the one you want to work with - from your post with all the disk info, /dev/hda looks like it has several partitions, but /dev/hdb is an NTFS partition.  Can you post the output of the "df" command?

3) If you're really sure which disk you want to reformat, it's simple.  Make sure it's unmounted:
    "sudo umount <disk partition name>", where <disk partition name> is listed in the output of "df", and is something like /dev/hda1, or /dev/hdb1, etc.  Unmount all the partitions for that disk.

4) If a partition will not unmount, it's because for some reason, you're still using it, whether you realize it or not.  You're gonna have to figure out how this is happening.  One possibility is that you have some file still open on this drive, like you are running a program from there, or you have a shell open and are cd'd to a directory on that drive.  Sometimes a reboot will help...

5) Use gparted or fdisk to repartition the disk.  That'll surely erase everything that's there, so that's why the extreme caution :-)

6) You'll probably want to give this disk a new mount point and make it always present on boot.  I'll leave that description to someone else :guitar:

Best of luck,

Antbully

---

### Post by Eschguy on 2007-12-14
> **taurus said:**
> So looks like you have converted your /dev/hdb1 from ntfs filesystem to ext3.  Try to mount it and see what how space it has.

```
sudo mkdir /media/hdb1
sudo mount -t ext3 /dev/hdb1 /media/hdb1
df -h
```
Post the output of the last command here.

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             108G   89G   14G  87% /
varrun                506M  212K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   72K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/hdb1             113G  188M  107G   1% /media/hdb1

```

---

### Post by taurus on 2007-12-14
> **Eschguy said:**
> ```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             108G   89G   14G  87% /
varrun                506M  212K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   72K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
**[COLOR="Blue"]/dev/hdb1             113G  188M  107G   1% /media/hdb1[/COLOR]**

```

There you go.  It's all empty and really to be used.

---

### Post by Eschguy on 2007-12-14
Awesome! Thanks man. 

If I can be nitpicky for a second. How do I get it to have a disk mount point? I used to be able to just go to Computer and it'd be there. Not important, but I'm just curious.

---

### Post by antbully on 2007-12-14
> **Eschguy said:**
> Awesome! Thanks man. 

If I can be nitpicky for a second. How do I get it to have a disk mount point? I used to be able to just go to Computer and it'd be there. Not important, but I'm just curious.

Simple - just make a directory "mkdir foo" somewhere.  For a whole disk, I usually put it off of root, so go "mkdir /newdisk" or whatever, and then tell mount to use that: "mount /dev/whatever /newdisk".  It might  also be convenient to mount it off your home directory, like "/home/myusername/newdisk", then you can make it your own by doing "sudo chown -R myusername newdisk" - that will change it from being owned by root to being owned by myusername, etc; I've done that on occasion.

Goes without saying to read the man pages for these various commands :-)

---

### Post by Eschguy on 2007-12-14
Hmm....it's not letting me write to it at all.

---

### Post by Eschguy on 2007-12-14
Yeah, so I can't do anything to it. Write, make a directory, nothing. It says I don't have permission.

---

### Post by taurus on 2007-12-14
> **Eschguy said:**
> Yeah, so I can't do anything to it. Write, make a directory, nothing. It says I don't have permission.

_Assuming_ your login name is **guy**, do

```
sudo chown -R **guy**:**guy** /media/hdb1
ls -la /media
```

---

### Post by Eschguy on 2007-12-14
```

drwxr-xr-x  5 root   root   4096 2007-12-14 20:38 .
drwxr-xr-x 20 root   root   4096 2007-11-22 00:34 ..
lrwxrwxrwx  1 root   root      6 2007-11-21 14:06 cdrom -> cdrom0
drwxr-xr-x  2 root   root   4096 2007-11-21 14:06 cdrom0
lrwxrwxrwx  1 root   root      7 2007-11-21 14:06 floppy -> floppy0
drwxr-xr-x  2 root   root   4096 2007-11-21 14:06 floppy0
-rw-r--r--  1 root   root      0 2007-12-14 20:10 .hal-mtab
-rw-------  1 root   root      0 2007-12-14 18:51 .hal-mtab-lock
drwxr-xr-x  3 austin austin 4096 2007-12-14 20:31 hdb1

```

Well that fixed it. Thank you for all your help.

---

