---
title: "permission denied to move files across partitions"
date: 2010-04-19
forum: Hardware
---

### Post by simbeb on 2010-04-19
I have Ubuntu 9.10 Netbook remix installed on an Acer Aspire One A150X-3G netbook
 
my 120gb drive is partitioned into several drives:
-an ext3 one for my Ubuntu system
-2 NTFS ones with Windows XP and Windows 7 on
-2 FAT32 ones for file storage.
-oh, and a 16gb sd card in FAT32 in the left card slot of my netbook
 
Apart from the Linux partition, all are seen by Ubuntu as drives that can
be unmounted (or removable drives?)
 
I am using pysdm as my drive mounter/storage device manager
 
My problem is the following: I cannot delete , 
transfer to or from the FAT32 partitions and to the Linux partition, any file. I keep
getting the message telling me that the permission is denied
How can I permanently allow deletion and movement of files
between partitions and to my home folder?
(I am not too bothered about the NTFS partitions)
 
I hope I have given you enough info. I am a bit desperate as it's the
only thing that prevents me from using my netbook fully with an otherwise
perfectly functioning Ubuntu install :(
 
oh and please I am a fairly new user of Ubuntu - on the learning curve!

---

### Post by utnubuuser on 2010-04-19
Launch nautilus with Alt+F2, then - gksu nautilus  - that's superuser nautilus.

If that then works, it's just a permissions issue that can be adjusted.

---

### Post by Morbius1 on 2010-04-19
Post the output of the following commands and let's see what's up:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**
Type **mount**

---

### Post by simbeb on 2010-04-19
> **utnubuuser said:**
> Launch nautilus with Alt+F2, then - gksu nautilus  - that's superuser nautilus.

If that then works, it's just a permissions issue that can be adjusted.



I have followed your instructions, and I am getting this:

```
fred@Netbook:~$ gksu nautilus
Initializing nautilus-gdu extension

** (nautilus:1945): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1945): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1945): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.






```I don't get it. Any help welcome  - thanks

---

### Post by simbeb on 2010-04-19
> **Morbius1 said:**
> Post the output of the following commands and let's see what's up:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**
Type **mount**


Thank you for your offer of support. Please see below result after following your instructions. Also check my previous post. Cheers



```
fred@Netbook:~$ sudo blkid -c /dev/null
[sudo] password for fred: 
/dev/sda1: LABEL="WINDOWS XP" UUID="A481-D472" TYPE="vfat" 
/dev/sda2: UUID="0386af43-c034-4be1-b601-13ef9948c96f" TYPE="ext3" 
/dev/sda4: UUID="7470568670564F4C" LABEL="WINDOWS 7" TYPE="ntfs" 
/dev/sda5: UUID="07cd3de5-1e32-4966-a699-2353075b6c0c" TYPE="swap" 
/dev/sda6: LABEL="SHARE1" UUID="5357-8F60" TYPE="vfat" 
/dev/sda7: LABEL="SHARE2" UUID="9E5D-2C03" TYPE="vfat" 
/dev/mmcblk0p1: LABEL="APPS" UUID="4C51-341A" TYPE="vfat" 
fred@Netbook:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  defaults                    0  0  
# / was on /dev/sda2 during installation
UUID=0386af43-c034-4be1-b601-13ef9948c96f  /            ext3  relatime,errors=remount-ro  0  1  
# swap was on /dev/sda5 during installation
UUID=07cd3de5-1e32-4966-a699-2353075b6c0c  none         swap  sw                          0  0  
/dev/sda6                                  /media/sda6  vfat  uid=root,gid=users,users    0  0  
/dev/sda7                                  /media/sda7  vfat  defaults                    0  0  
/dev/sda4                                  /media/sda4  ntfs  defaults                    0  0  
/dev/sda1                                  /media/sda1  vfat  defaults                    0  0  
fred@Netbook:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda6 on /media/sda6 type vfat (rw,noexec,nosuid,nodev,uid=0,gid=100)
/dev/sda7 on /media/sda7 type vfat (rw)
/dev/sda4 on /media/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

---

### Post by Morbius1 on 2010-04-19
Step 1: Don't ever use PysDM again :)

Step 2: Create a backup of this fstab just in case....

OPen **Terminal**
Type **sudo cp /etc/fstab /etc/fstab.bak**

Step 3: Edit fstab to make the following changes:

Open **Terminal**
Type** gksu gedit /etc/fstab**

Put a # sign in front of the sda6 and sda7 vfat lines so that they look like this:
> #/dev/sda6                                  /media/sda6  vfat  uid=root,gid=users,users    0  0  
#/dev/sda7                                  /media/sda7  vfat  defaults                    0  0  Then add the following lines:
```
/dev/sda6 /media/sda6  vfat utf8,umask=007,gid=46 0 0  
/dev/sda7 /media/sda7  vfat utf8,umask=007,gid=46 0 0
```Save the file, exit gedit, and back in the terminal type:

[B]sudo umount /media/sda6
sudo umount /media/sda7
sudo mount -a[/B]

You should know immediately if you can read and write to those partitions.

---

### Post by simbeb on 2010-04-20
> **Morbius1 said:**
> Step 1: Don't ever use PysDM again :)
 
Step 2: Create a backup of this fstab just in case....
 
OPen **Terminal**
Type **sudo cp /etc/fstab /etc/fstab.bak**
 
Step 3: Edit fstab to make the following changes:
 
Open **Terminal**
Type** gksu gedit /etc/fstab**
 
Put a # sign in front of the sda6 and sda7 vfat lines so that they look like this:
Then add the following lines:
```
/dev/sda6 /media/sda6  vfat utf8,umask=007,gid=46 0 0  
/dev/sda7 /media/sda7  vfat utf8,umask=007,gid=46 0 0
```Save the file, exit gedit, and back in the terminal type:
 
**sudo umount /media/sda6**
**sudo umount /media/sda7**
**sudo mount -a**
 
 
You should know immediately if you can read and write to those partitions.
 
 
I am relatively new to Linux, but it is thanks to people like Morbius1 that it is useable by an increasing number of people...
I quickly followed your instructions during my short lunchtime at work and my first impression is that it is now all working fine. I tried transferring files across partitions and to the Linux one, and it is working. Haven't tried deleting any files yet but i can't see why it wouldn't work now. If there is anything wrong, I'll get back to you.
 
You must really be on a Ubuntu drip!
Eternally grateful :)

---

