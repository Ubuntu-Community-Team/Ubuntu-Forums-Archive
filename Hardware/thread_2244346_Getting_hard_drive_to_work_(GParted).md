---
title: "Getting hard drive to work (GParted)"
date: 2014-09-15
forum: Hardware
---

### Post by timmyk.2 on 2014-09-15
Greetings. I have Ubuntu Studio installed on a 64 GB SSD drive. I added a 1 TB HDD to my computer for storage, and used GParted to make a 900 GB partition on the HDD (I kept 100 GB in case I ever wanted a dual-boot). Anyway, this 900 GB partition does show up, but I can't put anything on it. Can someone explain? If you have any questions what I did, I followed the top answer in the below forum.

[http://askubuntu.com/questions/476212/how-to-add-a-new-hard-drive-to-ubuntu](http://askubuntu.com/questions/476212/how-to-add-a-new-hard-drive-to-ubuntu)

Thanks for any help!

---

### Post by Bashing-om on 2014-09-15
timmyk.2; Hi !

Have you met the pre-requisites ?
a) a partition does exist ?
b) There is a file system imposed on the partition ?
c) There is a mount point to attach to the file system ?

For the 1st 2; post back - between code tags - the output of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
and for the 'mount point'; what did you make it as ? 

For a "data partition" I am not a proponent of auto mounting it. My preference is to mount it as on-demand from terminal. Your use case may vary .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by timmyk.2 on 2014-09-15
```

timmy@timmy-desktop:~$ sudo fdisk -lu
[sudo] password for timmy: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004893d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1758175231   879086592   83  Linux

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00040fb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   108910591    54454272   83  Linux
/dev/sdb2       108912638   125044735     8066049    5  Extended
/dev/sdb5       108912640   125044735     8066048   82  Linux swap / Solaris
timmy@timmy-desktop:~$ sudo parted -l
Model: ATA WDC WD10EZEX-08M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  900GB  900GB  primary  ext4


Model: ATA SAMSUNG 470 Seri (scsi)
Disk /dev/sdb: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  55.8GB  55.8GB  primary   ext4            boot
 2      55.8GB  64.0GB  8260MB  extended
 5      55.8GB  64.0GB  8260MB  logical   linux-swap(v1)

```

I'm not sure; how would I find what I made the mount point? I don't remember seeing anything about that when partitioning. Sorry, this is my first time partitioning a hard drive!

---

### Post by Bashing-om on 2014-09-15
timmyk.2; Hey hey !

OK, you are aware that the SSD that holds your operating system is 'sdb', and the 1TB hard drive is 'sda', right - may not be as you intended or wanted.
As is, let's mount the data drive and see what is:
```

sudo mdir /mnt/data
sudo mount /dev/sda1 /mnt/data
sudo mkdir /mnt/data/save
sudo mkdir /mnt/data/backup
sudo chown timmy:timmy /mnt/data/save
sudo chown timmy:timmy /mnt/data/backup

``` Where 'save & backup' are fictions of my own mind, your name for your directories may indeed differ, do as you desire. It is your system.
The 'mkdir' commands are done only once to make that mount point; and to set up directories on the hard drive.

OK, now to copy some file(s) - say from your home directory.
What files exist in your home that you might want to backup ?
```

ls -al /home/timmy
##from that output do:##
cp <somefile> /mnt/data/save

```
Once done ReMeMbeR to (UN)mount that manually mounted file system .. else data corruption CAN result - tie a string around your finger if you have to !
```

sudo umount /mnt/data

```

And that my friend is all there is too it.

[INDENT][INDENT]ready and set -> GO.
[/INDENT][/INDENT]

---

### Post by timmyk.2 on 2014-09-16
Before I do that, I have a few questions. Firstly, if I right-click the drive in GParted, it only gives an option to unmount, implying it already is mounted. Also, will I have to mount and unmount every time I want to use it? I want this drive to be easily accessable since I will be copying files onto it quite often.

---

### Post by Bashing-om on 2014-09-16
timmyk.2; Welp'

Yeah, I agree that "  it only gives an option to unmount, implying it already is mounted." indicates it is mounted. To my knowledge the only way this could be is if there is an entry in the file "/etc/fstab".
IF you desire that the drive be available every time you boot, then an entry must exist in the referenced file.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Let's look and see what is :
```

cat /etc/fstab
mount

```

[INDENT][INDENT]we will
[INDENT][INDENT][INDENT]make it so
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by timmyk.2 on 2014-09-16
```
timmy@timmy-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=6f3ff036-efe7-4d04-bc9e-b28f9459a177 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=aedafaac-c9a8-4eff-bb5f-313e14797e73 none            swap    sw              0       0
timmy@timmy-desktop:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=timmy)
/dev/sda1 on /media/timmy/8997d846-b673-4b84-8633-f3632749cc3e type ext4 (rw,nosuid,nodev,uhelper=udisks2)

```

---

### Post by Bashing-om on 2014-09-16
timmyk.2; Humm,

Per that output, presently you are not automounting 'sda1';
Though it is currently mounted per the output of "mount'

OK, safely unmount 'sda1' via the GUI file manager, and reboot without doing other before:
```

mount

```
Now what shows ??

[INDENT][INDENT]because inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by timmyk.2 on 2014-09-17
```

timmy@timmy-desktop:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=timmy)
timmy@timmy-desktop:~$ 


```

---

### Post by Bashing-om on 2014-09-17
timmyk.2; OK;

That mount output looks proper. At this time 'sda1' is not mounted.
There are three ways to now mount it.

1) click on the device icon in the file manager
2) explicitly mount 'sda1' from terminal
3) Make a entry in " /etc/fstab " with a 'mount point' created before hand for the purpose to auto mount 'sda1'

Now as you have indicated you would like to have 'sda1' auto mount at boot we create ( or use and existing) a mount point.
And, make an entry in the " /etc/fstab " file.
To make that entry we need to know a couple of parameters; the device name ( which we already know) and it unique identifier.
We get the identifier:
```

sudo blkid

```

Pass that back and we can formulate the syntax to automount 'sda1'.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by timmyk.2 on 2014-09-17
```

timmy@timmy-desktop:~$ sudo blkid
[sudo] password for timmy: 
/dev/sda1: UUID="8997d846-b673-4b84-8633-f3632749cc3e" TYPE="ext4" 
/dev/sdb1: UUID="6f3ff036-efe7-4d04-bc9e-b28f9459a177" TYPE="ext4" 
/dev/sdb5: UUID="aedafaac-c9a8-4eff-bb5f-313e14797e73" TYPE="swap" 
timmy@timmy-desktop:~$ 

```

---

### Post by Bashing-om on 2014-09-17
timmyk.2; OK;

Auto mount. edit the file " /etc/fstab ".
Standard operating procedure is to make a back up file prior to editing, never can tell what might perchance.
```

sudo cp /etc/fstab /etc/fstab-16sep2014

```
open the file in the text editor with admin privileges, here I use gedit:
```

gksudo gedit /etc/fstab

```
and insert these lines:
```

#sda1 automount created 16Sep2014 mount point /mnt/data
UUID=8997d846-b673-4b84-8633-f3632749cc3e /mnt/data               ext4    defaults  0       0

```

Now, reload " /etc/fstab " check and see if there are errors:
```

sudo mount -a

```


If there are no errors reported by the mount command;
Reboot and let's see the effect. The partition is automounted, and ready immediately for use, and does not require to be manually (UN)mounted, the system will take care of it.

[INDENT][INDENT]easy as falling out of bed
[INDENT][INDENT][INDENT][INDENT]wide awake
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by timmyk.2 on 2014-09-17
Hmm... I did all that, and at the "sudo mount -a" command I got
```

timmy@timmy-desktop:~$ sudo mount -a
mount: mount point /mnt/data does not exist

```
I'm assuming I was supposed to insert those lines at the bottom of the file? Also, I don't know if this is normal or not, but at the "gksudo gedit /etc/fstab" command I got
```

(gedit:3754): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```

---

### Post by Elfy on 2014-09-17
```
sudo mkdir /mnt/data
sudo mount -a
```

the /mnt/data folder hasn't been created previously - hence it won't mount there

---

### Post by timmyk.2 on 2014-09-17
OK, I did all that, and no errors came up. However, after a reboot, it's not automounted, and even if I manually mount it, I can't put anything on it.

---

### Post by Bashing-om on 2014-09-17
timmyk.2; Hey !

We are making progress !

I bet it is mounted !
Post back:
```

mount
cat /etc/mtab
ls -al /mnt
ls -al /mnt/data

```
and let's get ready to 'chown'  that mount point to "you" .. to resolve this issue.

[INDENT][INDENT]so I think
[/INDENT][/INDENT]

---

### Post by timmyk.2 on 2014-09-17
```

timmy@timmy-desktop:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sdb1 on /mnt/data type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=timmy)
```
```

timmy@timmy-desktop:~$ cat /etc/mtab
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
none /sys/fs/pstore pstore rw 0 0
/dev/sdb1 /mnt/data ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=timmy 0 0
```
```

timmy@timmy-desktop:~$ ls -al /mnt
total 12
drwxr-xr-x  3 root root 4096 Sep 17 10:44 .
drwxr-xr-x 22 root root 4096 Sep 14 09:10 ..
drwxr-xr-x 22 root root 4096 Sep 14 09:10 data
```
```

timmy@timmy-desktop:~$ ls -al /mnt/data
total 116
drwxr-xr-x  22 root root  4096 Sep 14 09:10 .
drwxr-xr-x   3 root root  4096 Sep 17 10:44 ..
drwxr-xr-x   2 root root  4096 Sep 14 09:10 bin
drwxr-xr-x   3 root root  4096 Sep 14 09:10 boot
drwxr-xr-x   2 root root  4096 Sep  8 12:07 cdrom
drwxr-xr-x   4 root root  4096 Jul 22 16:13 dev
drwxr-xr-x 153 root root 12288 Sep 17 11:02 etc
drwxr-xr-x   3 root root  4096 Apr 10 15:11 home
lrwxrwxrwx   1 root root    36 Sep 14 09:10 initrd.img -> boot/initrd.img-3.13.0-35-lowlatency
lrwxrwxrwx   1 root root    36 Sep 13 21:42 initrd.img.old -> boot/initrd.img-3.13.0-32-lowlatency
drwxr-xr-x  23 root root  4096 Sep 14 09:09 lib
drwx------   2 root root 16384 Sep  8 12:02 lost+found
drwxr-xr-x   3 root root  4096 Jul 22 15:48 media
drwxr-xr-x   3 root root  4096 Sep 17 10:44 mnt
drwxr-xr-x   4 root root  4096 Sep 13 23:37 opt
drwxr-xr-x   2 root root  4096 Apr 10 15:11 proc
drwx------   7 root root  4096 Sep 16 22:00 root
drwxr-xr-x  12 root root  4096 Jul 22 16:15 run
drwxr-xr-x   2 root root 12288 Sep 14 09:10 sbin
drwxr-xr-x   2 root root  4096 Jul 22 15:48 srv
drwxr-xr-x   2 root root  4096 Mar 12  2014 sys
drwxrwxrwt   9 root root  4096 Sep 17 13:19 tmp
drwxr-xr-x  10 root root  4096 Jul 22 15:48 usr
drwxr-xr-x  12 root root  4096 Jul 22 16:18 var
lrwxrwxrwx   1 root root    33 Sep 14 09:10 vmlinuz -> boot/vmlinuz-3.13.0-35-lowlatency
lrwxrwxrwx   1 root root    33 Sep 13 21:42 vmlinuz.old -> boot/vmlinuz-3.13.0-32-lowlatency
timmy@timmy-desktop:~$ 


```

---

### Post by Bashing-om on 2014-09-17
timmyk.2; HUH ??

> 
timmy@timmy-desktop:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
##as opposed to:
/dev/sdb1 on /mnt/data type ext4 (rw)


I sure messed this one up - small slip of the paste here on my part !
MY sincere apologies !

Back to the file "/etc/fstab" that line for 'sda1's' UUID should be:
```

8997d846-b673-4b84-8633-f3632749cc3e

```
Not even "6f3ff036-efe7-4d04-bc9e-b28f9459a177"
My mind set must have gotten in the way of what was right !

That re-done, we look at the permissions for access to 'sda1' !

again, sorry, I will correct the posting to what is true.

[INDENT][INDENT]the good thing is;
[INDENT][INDENT][INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT][INDENT][INDENT]it is all fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by timmyk.2 on 2014-09-17
OK, so I changed the incorrect code to
```
#sda1 automount created 16Sep2014 mount point /mnt/data UUID=8997d846-b673-4b84-8633-f3632749cc3e /mnt/data               ext4    defaults  0       0
```
Now there are no errors when I type in
```
sudo mount -a
```
However, when I rebooted, the hard drive does not appear in the file manager and there is no icon on the desktop like there was before.

---

### Post by Bashing-om on 2014-09-17
timmyk.2; OK !

Whewhh, I feel better !

The device not now appearing in nautilus is expected behavior as "nautilus" does not see that mount point.
If it is your desire that nautilus does see it, -as some do not want it -  will have to change the mount point.
```

sudo mkdir /media/timmy/data

```
and back to "/etc/fstab" and change "/mnt/data" to :
```

/media/timmy/data

```
In both places.

Now are we ready to look at the access' to 'sda1' ??

[INDENT][INDENT]step by step, a little 
[INDENT][INDENT][INDENT][INDENT]at the time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by timmyk.2 on 2014-09-17
Great, its back and is automounting! I still can't put anything on it though. I'm assuming this is because I don't have access yet?

---

### Post by Bashing-om on 2014-09-17
timmyk.2; Great !

We are doing good: OK, access !
```

sudo chown timmy:timmy /media/timmy/data

```
That gives "you" and as well root alone access to that partition. Else, if you desire others to access it, will have to get specific.

[INDENT][INDENT]workie great
[INDENT][INDENT][INDENT]last long time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by timmyk.2 on 2014-09-18
Awesome! Thank you so much for the help!

---

### Post by Bashing-om on 2014-09-18
timmyk.2; Good deal !

I hope you are just that much more comfortable with this our operating system of choice and gain a greater realization of what is possible.

Happy trails to you.
[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

