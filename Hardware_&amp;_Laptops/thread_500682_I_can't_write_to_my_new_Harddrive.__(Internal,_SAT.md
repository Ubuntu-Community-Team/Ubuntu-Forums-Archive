---
title: "I can't write to my new Harddrive.  (Internal, SATA)"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by Sanjuro82 on 2007-07-14
I installed my new Harddrive last night and used Gparted to format it as a ext3 file system.  The harddrive shows up once Ubuntu loads up, everything is cool except that I can't write to the drive.

If I right click on the drive and go into "Properties" and then the "Permissions" tab, it has the Owner as "unknown", and the Access as "Read-only".

If I try to change the access to "Read and Write", I get an error message saying I can't change the permission.   Anyone know how to fix this, so I'll be able to Read and Write with my new harddrive?

here's my sudo fdisk -l

```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        5871    47102580    7  HPFS/NTFS
/dev/sda3            5979        9675    29696152+  83  Linux
/dev/sda4            9676        9726      409657+   5  Extended
/dev/sda5            9676        9726      409626   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   83  Linux
```

and here's df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              28G  6.6G   21G  25% /
varrun                506M   96K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  128K  505M   1% /proc/bus/usb
udev                  506M  128K  505M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1             276G   65M  262G   1% /media/disk

```

Let me know what to do.  Oh and I'm a Linux newbie here so thanks for the help!

---

### Post by Sanjuro82 on 2007-07-14
cat /etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6363c349-cbb3-450b-91c6-80ed6974c525 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3e195d73-16b8-4a61-adee-d2684a50d111 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
```

---

### Post by regomodo on 2007-07-14
give us the printout of 

$ ls -la /media

---

### Post by Sanjuro82 on 2007-07-14
```
total 24
drwxr-xr-x  5 root root 4096 2007-07-14 01:53 .
drwxr-xr-x 21 root root 4096 2007-07-05 02:06 ..
lrwxrwxrwx  1 root root    6 2007-07-04 20:33 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-07-04 20:33 cdrom0
drwxr-xr-x  2 root root 4096 2007-07-04 20:33 cdrom1
drwxr-xr-x  3 root root 4096 2007-07-13 20:32 disk
-rw-r--r--  1 root root   51 2007-07-14 01:53 .hal-mtab
-rw---x---  1 root root    0 2007-04-17 22:23 .hal-mtab-lock
```

---

### Post by dabl on 2007-07-14
> **Sanjuro82 said:**
> cat /etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6363c349-cbb3-450b-91c6-80ed6974c525 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3e195d73-16b8-4a61-adee-d2684a50d111 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
```

Your new drive is missing entirely from your /etc/fstab file, therefore it doesn't exist as far as the booted system is concerned.  I thought Ubuntu would dynamically assign it a position in fstab, even though it's not obvious that you have assigned it a mount point.  Did you make /dev/media/disk, or did the system do that by itself?

You might try adding a line in fstab something like this:

```
/dev/sdb1  /media/disk ext3  defaults        0       2
```

assuming that is the filesystem format and where you want it mounted.  Then you'll have to use the mount command to mount it for your use.

---

### Post by Sanjuro82 on 2007-07-14
dabl, 

I'll give that try.  But one quick question.  How do I go about adding that line of code in "fstab"?  

Thanks.

---

### Post by dabl on 2007-07-14
Ahhh, you're REAL new to Linux, eh?

Good, here's a learning experience for you.  Most of the important configuration files in your Linux system are plain ASCII text, so you modify them with a text editor.  Linux has right about a zillion text editors by my count, so the hardest part is picking one.  Ubuntu comes with gedit, and also nano and vi are in there, each progressively less user friendly. So, let's start with the friendliest, gedit.

To revise a system file, you must be operating as the Super User, or you won't have permission to save it.  So start gedit in a console with the command ```
gksu gedit
``` now you've got it running in Super User mode.  Click "open" and then browse to the file /etc/fstab.  In other words, click the single up-arrow on the menu bar until you get to "/", and you'll see the directory "/etc", open that directory, browse to the file "fstab".

The first thing you want to do, ALWAYS, is make sure you don't make things worse, so you back up the system file that you're getting ready to change. So, with fstab open, do a "File>Save As" and change the file name to "fstab.bak14JUL07" or something like that, and save it.

Now, it's still open, so cursor down to the line that says ```
UUID=3e195d73-16b8-4a61-adee-d2684a50d111 none            swap    sw              0       0
```
go to the end of it, hit "Enter" to add a line break and bring the cursor back to the beginning of the new line, and then enter ```
/dev/sdb1  /media/disk ext3  defaults        0       2
```

Don't use the "Enter" key at the end, or you'll add another line that you don't want.

Now, because you previously changed the file name to back it up, you need to use "File>Save As" again, and this time change it back to "fstab" and then save it.  It will show you a caution regarding you're about to overwrite the old fstab, and you say "YES".

Once finished, close gedit, and in your terminal you will need to mount the new device, so enter ```
sudo mount -t /dev/sdb1 /media/disk
``` and let's see what happens.  I'll cross my fingers. :)

---

### Post by Sanjuro82 on 2007-07-14
Awesome!  Thank you so much for the detailed instructions.  I'm up at the office right now, but I will give this a try as soon as I get home and let you know if it works.

Thanks again!

---

### Post by Sanjuro82 on 2007-07-14
```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
```

That was the output after following your above post.  Doesn't seem to have done anything.

---

### Post by merlinus on 2007-07-14
Try this:

```

sudo mount -t ext3 /dev/sdb1 /media/disk

```-merlin

---

### Post by Sanjuro82 on 2007-07-14
```
mount: mount point /media/disk does not exist

```

---

### Post by merlinus on 2007-07-14
OK.  You will need to make the mount point:

```

sudo mkdir /media/disk

```

-merlin

---

### Post by Sanjuro82 on 2007-07-14
Ok it mounted the drive but I still can't use the harddrive for some reason.  If I try to drag a file to the drive I get this error:

```
Error while coping to "/media/disk".
You do not have permission to write to this drive
```

---

### Post by merlinus on 2007-07-14
Install the drivers:

```

sudo apt-get install ntfs-3g ntfs-config

```

then:

```

sudo ntfs-config

```

Tick the appropriate boxes and restart.

-merlin

---

### Post by Sanjuro82 on 2007-07-14
merlinus,

"Enable write support for internal device" is not available for my to select.  I did put a check in the box for "Enable write support for external device" even though I do not have a external device.  

Also why would I use ntfs-config if my new drive is ext3?  Sorry for asking stupid question.  You've been a big help so far.

---

### Post by merlinus on 2007-07-14
Sorry, my mistake.

What does this give now:

```

sudo fdisk -l
cat /etc/fstab

```

(l is a lowercase L)

-merlin

---

### Post by Sanjuro82 on 2007-07-14
sudo fdisk -l

```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        5871    47102580    7  HPFS/NTFS
/dev/sda3            5979        9675    29696152+  83  Linux
/dev/sda4            9676        9726      409657+   5  Extended
/dev/sda5            9676        9726      409626   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   83  Linux
```

---

### Post by Sanjuro82 on 2007-07-14
cat /etc/fstab:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=6363c349-cbb3-450b-91c6-80ed6974c525 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=3e195d73-16b8-4a61-adee-d2684a50d111 none swap sw 0 0
/dev/sdb1 /media/disk ext3 defaults 0 2
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0

```

---

### Post by merlinus on 2007-07-14
Try this:

```

sudo chown -R username:username /media/disk

```where username is your login

-merlin

---

### Post by Sanjuro82 on 2007-07-14
Sweet!  That worked (for the most part)!!  I was able to copy over a file to my new harddrive.  The only thing I notice that is odd now is that I can't create new folders in the drive.  Got any suggestions for that?? 

A million thanks for getting me this far!!!  Merlin you rock!

---

### Post by merlinus on 2007-07-14
Check the permissions for the drive to make sure they are correct.

If you don't know how, post back....

-merlin

---

### Post by Sanjuro82 on 2007-07-14
Well I think it's all working now!  After rebooting I can now create folders!

---

### Post by merlinus on 2007-07-14
Great!!!  Good for you for hanging in there....

All the best....

-merlin

---

