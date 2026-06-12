---
title: "The rest of my hard drive??"
date: 2010-01-22
forum: Hardware
---

### Post by savaan on 2010-01-22
I installed Ubuntu Karmic on my computer the other day and I'm quite pleased. However, during the install I cut my hd into parts, allowing about 10gigs for swap area and another 350 gigs for storage area. I'd like to keep my music, videos, etc there but I can't seem to create an icon or anything for it on my desktop. I can SEE the drive in my disk utilites, so its there and mounted, I'd just like to be able to navigate there and store data and files there

Any help would be appreciated!

---

### Post by mikewhatever on 2010-01-23
You should be able to access the drive from the side panel in your file browser. Once mounted, an icon usually appear on the desktop.

---

### Post by savaan on 2010-01-23
I haven't used Linux in close to 10yrs. That's kind of what I remembered about it too...once the drive was mounted, I should have an icon for it. The disk utility shows that it IS in fact mounted, but I can't figure out how to create a desktop icon for it so I can begin storing my files there :( 
I can go to Places -> Computer but I only see my CD drive there and Filesystem. I should be able to see another 350gigs of partitioned space

Now..I am NOT in my root account. I'm on MY personal account (which has admin privs anyway) Should that make a difference?

---

### Post by amauk on 2010-01-23
I'd suggest making a permanent mount point for the drive

1) make a note of the device name for the drive
(you can use the partition editor for this)
it starts with '/dev' and ends with a digit

Eg. /dev/sda2

Also, make a note of the filesystem type
(EXT3 / EXT4 / etc.)


2) create a directory in /media for the drive to mount in
```
sudo mkdir /media/data
```


3) Open up the filesystem table in gedit
```
sudo gedit /etc/fstab
```


4) add an entry at the bottom for the data drive
change values to suit, as per 1) above
```
/dev/sda2  /media/data  ext4  defaults  0  2
```
Save the file, and exit gedit

5) issue the command to mount all filesystems
```
sudo mount -a
```

---

### Post by savaan on 2010-01-23
Tried that. In my disk utilities it shows 10gigs set as swap and 340gigs free to use. If I click on the 340gig space, it says its sda6, but if I click on the full 350gig icon above these, it shows it to be sda2. 

Now...I tried the terminal commands and instructions for both. The sda6 went through with no  problems, created the folder (which was suddenly filled with folders like "etc, games, bin" and so forth. When I tried to redo the instructions using the 340gig slot, THAT was labeled as sda2...and that threw off the following error:

mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

btw, thanks for the help. If I can smooth this out, I'm dropping Windows out of all my home computers. I've only been on this for 3 days and already I'm doing everything that I was able to do on Windows...

---

### Post by amauk on 2010-01-23
can you post the output of
```
sudo fdisk -l
```

^^ that's a lower case L at the end

---

### Post by mikewhatever on 2010-01-23
Please, disregard this comment. There was a mixup with another thread.

---

### Post by savaan on 2010-01-23
I've tried using both sda2 & sda6. The output is: 



===============

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18236   146480638+  83  Linux
/dev/sda2           18237       60801   341903362+   5  Extended
/dev/sda5           18237       19452     9767488+  82  Linux swap / Solaris
/dev/sda6           19453       60801   332135811   83  Linux

Disk /dev/sdb: 503 MB, 503840256 bytes
4 heads, 32 sectors/track, 7687 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7688      492015+   b  W95 FAT32

=====================

---

### Post by louieb on 2010-01-23
The data partition needs to be accessed through sda6 - sda2 is an extended partition -just a container for logical partitions.

amauk's suggestion in post #4 should work - just substitute sda6 where he has sda2.

If it does not work please post the output of - this will give the exact file-system type. 
```
sudo blkid -c /dev/null
```

---

### Post by mikewhatever on 2010-01-23
Right, so you should be mounting sda6 and not sda2, according to fdisk. Once done, and if there is no icon on the desktop, just create a link to it.

ln -s /media/storage ~/Desktop/sda6

Note, if '/media/storage' is not the mount point you chose, substitute the real mount point instead.

---

### Post by savaan on 2010-01-23
OK...still no icon on my desktop :( Again,  I'm not in my root account, but my user with Admin privs. This is the output:


==========
/dev/sda1: UUID="f4b13f52-d326-4f76-a2d1-c06a64fc9dee" TYPE="ext4" 
/dev/sda5: UUID="5e850e72-8fcc-4370-97dc-351ed861bcc0" TYPE="swap" 
/dev/sda6: LABEL="Storage" UUID="4a4281d3-ce7f-41b2-a491-0749a5826600" TYPE="ext4" 
/dev/sdb1: UUID="A8E1-329D" TYPE="vfat" 
==========

thanks again for all the help!

---

### Post by louieb on 2010-01-23
did you do the command?

```
sudo mount -a 
```

lets check some stuff
Go ahead a post the output of
```
mount
```
and 
```
ls /media
```
and the content of **/etc/fstab**

---

### Post by savaan on 2010-01-24
Mount:

==========
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda6 on /usr/local type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/techbot/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=techbot)
/dev/sda6 on /media/data type ext4 (rw)
=============

ls media:

cdrom  cdrom0  data



and my fstab:


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f4b13f52-d326-4f76-a2d1-c06a64fc9dee /               ext4    errors=remount-ro 0       1
# /usr/local was on /dev/sda6 during installation
UUID=4a4281d3-ce7f-41b2-a491-0749a5826600 /usr/local      ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=5e850e72-8fcc-4370-97dc-351ed861bcc0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda6  /media/data  ext4  defaults  0  2

---

### Post by huygens on 2010-01-24
Hi,

Instead of going into heavy command lines, I can proposed an alternative using the mouse and just a few keyboard keys ;-)

So first right click on your desktop and select "Create launcher..." in the popup menu.
You should get a small dialog box. Choose the **Type** of your launcher as "Location". Give a **Name** to your shortcut. And add the location, you can use the browse button (which is a bit buggy, you have to select a file inside the directory/drive you want to select, then once validated, you delete the filename in the **Location** area). You can change the icon by clicking on it.
That's it :-)

I hope this help.

---

### Post by louieb on 2010-01-24
Everything looks ok except for sda6 is mounted in two spots. The /usr/local mount would work just fine (wonder how that happened) - but it won't display the link on the desktop. Only mounts in /meda get a desktop icon. 

from the mount command. 
```

...
/dev/sda6 on /usr/local type ext4 (rw)
...
/dev/sda6 on /media/data type ext4 (rw)

```It is mounted on two lines in /etc/fstab 
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f4b13f52-d326-4f76-a2d1-c06a64fc9dee /               ext4    errors=remount-ro 0       1
# /usr/local was on /dev/sda6 during installation
[COLOR=Red]UUID=4a4281d3-ce7f-41b2-a491-0749a5826600 [COLOR=Purple]/usr/local [/COLOR]     ext4    defaults        0       2[/COLOR]
# swap was on /dev/sda5 during installation
UUID=5e850e72-8fcc-4370-97dc-351ed861bcc0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

[COLOR=Red]/dev/sda6  /media/data  ext4  defaults  0  2     [/COLOR]

```Change **/usr/local **to **/meda/data **in **/etc/fstab**
and get rid of the last line or comment it out. (start the line with a #)

now either reboot or run the following commands - you should now get a desktop icon for /meda/data every time.   

```

sudo umount /usr/local
sudo umount /meda/data 
sudo mount -a
```@huygens - :DNice I'll try to remember that.

---

### Post by savaan on 2010-01-24
Louie, that worked! However, inside sda6 are files like bin, etc, games, lib and so on...looks like Linux system files. Are these OK to delete or do they need to stay for the file structure of the drive? If they have to stay, is there a way to hide those so my personal data files aren't mixed up with these? Thanks for all the help in getting this set up. I should be moving my wife's computer over to Ubuntu this week. I don't anticipate any problems seeing the ease of setup:P

---

### Post by louieb on 2010-01-24
> **savaan said:**
> However, inside sda6 are files like bin, etc, games, lib and so on...looks like Linux system files. ...:P

Those folders are left over from the partition being mounted on /usr/local.  That folder is not  required - just looked at my 8.04 install and it does not have one.   

If everything is working then its safe to delete then - they can't be found by looking in /usr/local.   (or you could move them to /usr/local).

:D - more that you want to know  you can look it up in the [Filesystem Hierarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html") - Ubuntu follows this for the most part.

---

