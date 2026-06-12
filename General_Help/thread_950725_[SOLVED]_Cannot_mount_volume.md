---
title: "[SOLVED] Cannot mount volume"
date: 2008-10-17
forum: General Help
---

### Post by Pacane on 2008-10-17
Hi, i am having a problem with my Data storage Hard drive. It used to work fine, but now it started to refuse mounting itself.

The exact error message is:
> Cannot mount volume.
Unable to mount the volume.
Details:
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

My result of sudo fdisk -l
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6fdd6fdd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bf70bf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9767488+  83  Linux
/dev/sdb2            1217        9730    68388705    5  Extended
/dev/sdb5            9245        9730     3903795   82  Linux swap / Solaris
/dev/sdb6            1217        9243    64476814+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93ff1122

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58895889

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       24322   195358615    7  HPFS/NTFS


result of gksudo gedit /etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=7be24728-bc4d-4a14-bd58-2f1276276618 /home           ext3    relatime        0       2
# /dev/sda5
UUID=f97c028d-924a-4726-a307-d48278a5f7dd none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


The disk/partition that doesnt mount is /dev/sda . I even tried formatting the whole disk, remaking the partition as EXT3, now it's in NTFS. If i manually mount the disk to /media/XYZ it works, but i'd like it to be accessed automatically. Is there a way to fix that? I know many people had this error message with a damaged partition of M$ but this on only contains DATA.

Also, I noticed that my fstab is not really corresponding to what my fdisk -l says. IE: sda6 (located in fstab) does not even exist in the fdisk file. (and according to GParted, the info in fdisk -l is correct...)

Any idea?
Thanks for your help, and let me know if you need more info.

---

### Post by TCSnyder on 2008-10-17
what is the name of the drive? 

> mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /) 

---

### Post by TCSnyder on 2008-10-17
aslo what is the output of 

```
df -h
```

---

### Post by dave.com on 2008-10-17
I'm getting a similar problem. After getting into Ubuntu the linux drives are not 'mounted' and grub don't recognise uuid's (altho its still booting teh flaming fs devices). This is somewhat complicated by a /home permissions bug which is currently 'bugging' me (well, it coulda been an irk, irksome was a contender but nah). It's harder for my situation to tell if we're related ;p

For what I'm worth, after scouring the Synaptic repository have discovered tho that ubuntu package "autofs" is not installed. Which is something I have no recollection for ever un-installing. Also I suggest checking if automount package installation like "discover" is another fugitive package possibility (lol scratch muh back).

Stay on it I need you!

---

### Post by Pacane on 2008-10-17
output of df -h
> Filesystem            Size  Used Avail Use% Mounted on
varrun               1013M  112K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  108K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   39M  975M   4% /lib/modules/2.6.24-21-generic/volatile
/dev/sdb6              62G  3.7G   55G   7% /home
gvfs-fuse-daemon      9.3G  3.5G  5.4G  40% /home/joel/.gvfs
/dev/sdc1             233G  171G   62G  74% /media/disk
/dev/sdd1             187G  122G   65G  66% /media/disk-1

> **TCSnyder said:**
> what is the name of the drive?
Well, if by "drive name" you mean the name it shows in "Places", it's 320.1GB Media. (If that's not what you asked for, let me know how I could get you that info)

Thanks for your replies.

---

### Post by jerome1232 on 2008-10-17
What's the output of this, it'll tell us what the label on sda1 is so we can figure out if it's causing mount problems
```
sudo apt-get install ntfsprogs
sudo ntfslabel /dev/sda1
```


Also I'm willing to bet plugging that external drive in just reodered your drives, the uuid's should be pointing to the correct areas (that's why fstab appears to be wrong)

these commands will help figure out where everything is (it looks like sdb is your main drive that has the os, once again the uuid's will be pointing to the correct device so it's not an issue that fstab appears to be incorrect)
```
mount
sudo blkid
```

---

### Post by Pacane on 2008-10-17
The output is blank for "sudo ntfslabel /dev/sda1"

mount:
> proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sdb6 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/joel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joel)
/dev/sdc1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdd1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


sudo blkid:
> 
/dev/sda1: UUID="9C7CB51B7CB4F0DE" TYPE="ntfs" 
/dev/sdb1: UUID="150e3e53-0e08-43ec-9ed6-45d7b1d1aa6a" TYPE="ext3" 
/dev/sdc1: UUID="E40AF6FF0AF6CD94" TYPE="ntfs" 
/dev/sdd1: UUID="047C87027C86EE2C" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="f97c028d-924a-4726-a307-d48278a5f7dd" 
/dev/sdb6: UUID="7be24728-bc4d-4a14-bd58-2f1276276618" SEC_TYPE="ext2" TYPE="ext3" 


---

### Post by jerome1232 on 2008-10-17
ok so it has no label, go ahead and slap a label on. whatever you want. Then reboot, it should mount itself as '/media/labelname' now.

```
sudo ntfslabel /dev/sda1 data
```

---

### Post by Pacane on 2008-10-17
Unfortunatly it didn't fix the thing. I'm still getting the error message saying that it contains some illegal character. However the label has been set.

---

### Post by Uchiha_madara on 2008-10-17
try this Link I faced the same Problem

[http://ubuntuforums.org/showthread.php?t=898654](http://ubuntuforums.org/showthread.php?t=898654)

Good Luck

---

### Post by jerome1232 on 2008-10-17
Ok, one last idea what does this command return? If there is anything other than disk, disk-1, cdrom0, or floppy0 then remove it. As you can see from your 'mount' command and fstab, those are the only 4 directories that should exist there right now.
```
ls -l /media
```


And just to confirm what I mentioned about your fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
[COLOR="Red"]# /dev/sda6
UUID=7be24728-bc4d-4a14-bd58-2f1276276618 /home ext3 relatime 0 2[/COLOR]
[COLOR="Blue"]# /dev/sda5
UUID=f97c028d-924a-4726-a307-d48278a5f7dd none swap sw 0 0[/COLOR]
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0 


> /dev/sda1: UUID="9C7CB51B7CB4F0DE" TYPE="ntfs"
/dev/sdb1: UUID="150e3e53-0e08-43ec-9ed6-45d7b1d1aa6a" TYPE="ext3"
/dev/sdc1: UUID="E40AF6FF0AF6CD94" TYPE="ntfs"
/dev/sdd1: UUID="047C87027C86EE2C" TYPE="ntfs"
[COLOR="Blue"]/dev/sdb5: TYPE="swap" UUID="f97c028d-924a-4726-a307-d48278a5f7dd"[/COLOR]
[COLOR="Red"]/dev/sdb6: UUID="7be24728-bc4d-4a14-bd58-2f1276276618" SEC_TYPE="ext2" TYPE="ext3"[/COLOR] 


Notice how the UUID's in fstab are ACTUALLy pointing at sdb entries, so that means fstab isn't messed up, the comments are just wrong atm, if you were to unplug that usb drive and reboot, your os would be back on sda :)

---

### Post by Pacane on 2008-10-17
Alright I did what you said, unplugged the 320GB drive (which is however not USB by the way (and I don't think that it would really matter anyway)).

so..

ls -l /media, results as:
> 
lrwxrwxrwx 1 root root     6 2008-07-28 06:06 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2008-07-28 06:06 cdrom0
drwxrwxrwx 1 root root 12288 2008-10-15 23:00 disk
drwxrwxrwx 1 root root 16384 2008-10-16 23:43 disk-1
lrwxrwxrwx 1 root root     7 2008-07-28 06:06 floppy -> floppy0
drwxr-xr-x 2 root root  4096 2008-07-28 06:06 floppy0


now the df -h results as:
> Filesystem            Size  Used Avail Use% Mounted on
varrun               1013M  112K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  104K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   39M  975M   4% /lib/modules/2.6.24-21-generic/volatile
/dev/sda6              62G  3.7G   55G   7% /home
gvfs-fuse-daemon      9.3G  3.5G  5.4G  40% /home/joel/.gvfs
/dev/sdc1             187G  122G   65G  66% /media/disk
/dev/sdb1             233G  171G   62G  74% /media/disk-1


So basically as you said, the drives got mounted on disk and disk-1. The 320GB is still unplugged though.

The sudo fdisk -l output:
> Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bf70bf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        9730    68388705    5  Extended
/dev/sda5            9245        9730     3903795   82  Linux swap / Solaris
/dev/sda6            1217        9243    64476814+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93ff1122

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58895889

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24322   195358615    7  HPFS/NTFS


and finally the fstab:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=7be24728-bc4d-4a14-bd58-2f1276276618 /home           ext3    relatime        0       2
# /dev/sda5
UUID=f97c028d-924a-4726-a307-d48278a5f7dd none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Now, should I do something else before re-plugging the 320GB?

---

### Post by jerome1232 on 2008-10-17
Is it an internal drive?

---

### Post by Pacane on 2008-10-17
It is.... Sata2 drive.

---

### Post by jerome1232 on 2008-10-17
It matters, I was going at this like it was a usb drive my bad.
(they auto mount to /media)

What we need to do is edit your fstab :)

So go ahead and boot up with that thing plugged in. 
Then edit your fstab like so. I fixed the comments in fstab to so that it will be accurate with the new disk plugged in.

Use sudo blkid to make sure I'm entering the right uuid for that drive, and change the mountpoint to whatever you want.

After editing the fstab make the dir for that mount point then try mounting it.
```
sudo mkdir /mnt/data
sudo mount -a
```

Ask questions if you want clarification on anything.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb6
UUID=7be24728-bc4d-4a14-bd58-2f1276276618 /home ext3 relatime 0 2
# /dev/sdb5
UUID=f97c028d-924a-4726-a307-d48278a5f7dd none swap sw 0 0
# This is an entry for the ntfs partition
# /dev/sda1
UUID=9C7CB51B7CB4F0DE /mnt/data ntfs-3g defaults,locale=en_US.utf8 0 0
# This entries are for external optical drives and the floppy
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0 
```

---

### Post by Pacane on 2008-10-18
Alright Alright. So that partly worked.

In fact, it works fine when I mount it manually.

However, I cannot see the "Storage" drive in the "Places" menu.

I DO see it in GParted and Windows XP though.

So I dont know what's missing but for the other drives, I just have to click on their name in "places" and an icon appears with the drive name and etc...

Would there be missing something so the drive appears in that menu?

By the way, thanks for all your help. Really appreciated.

---

### Post by jerome1232 on 2008-10-18
If you want it to appear on your desktop (I think in places as well) Then change the mountpoint from /mnt/mountpoint to /media/mountpoint

(In the fstab I gave you it was mounted at /mnt/data)

if you want it mounted during boot time then remove the noauto option.
so the fstab would be 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb6
UUID=7be24728-bc4d-4a14-bd58-2f1276276618 /home ext3 relatime 0 2
# /dev/sdb5
UUID=f97c028d-924a-4726-a307-d48278a5f7dd none swap sw 0 0
[COLOR="Red"]# This is an entry for the ntfs partition
# /dev/sda1
UUID=9C7CB51B7CB4F0DE /media/data ntfs-3g defaults,locale=en_US.utf8,noauto 0 0[/COLOR]
# This entries are for external optical drives and the floppy
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
```

---

### Post by Pacane on 2008-10-18
Ok, it seems to work, but this time im having an error message about "You are not privileged to mount this volume", I'm guessing it's in the fstab; some parameter has got to be wrong. But this time, it appears in the "places".

(Sub question: Let's say I want to label another disk, is there a risk of data lost? if so, could I proceed the same way as you told me to do before? Thanks)

---

### Post by jerome1232 on 2008-10-18
No there's no risk for data loss, there are different methods for different file systems though.

Try adding the 'users' option to fstab, that should make it mountable without sudo.

```
UUID=9C7CB51B7CB4F0DE /media/data ntfs-3g defaults,locale=en_US.utf8,noauto,[COLOR="Red"]users[/COLOR] 0 0
```


here is the link to help with labeling various filesystem (ignore that it's for usb disks it doesn't actually matter)

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by Pacane on 2008-10-18
Now i am getting a different error message:

> Unprivilieged user can not mount NTFS block devices using the external FUSE library. Either mount the volume as a root, or rebuild NTFS-3G with integrated FUSE support and make it setuid root. Please see more info at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

---

### Post by jerome1232 on 2008-10-18
yeesh, try it with ntfs instead of ntfs-3g (I never use ntfs anymore)

edit: And I forgot you'll want to set it's permissions too, If you take off the noauto it'll just be mounted on bootup and be on your desktop.

```
UUID=9C7CB51B7CB4F0DE /media/data ntfs defaults,locale=en_US.utf8,noauto,users,dmask=027,fmask=137  0 0
```

---

### Post by Pacane on 2008-10-18
Again, new error message:
> Cannot mount volume
unable to mount the volume

[mtent]: line 11 in /etc/fstab is bad
mount: can't find /media/data in /etc/fstab or /etc/mtab

and of course, /media/data exists.

edit:
with this line:
> UUID=9C7CB51B7CB4F0DE /media/data ntfs defaults,locale=en_US.utf8,noauto,usersdmask=027,fmask=137  0 0
I also tried removing the "noauto" and in both cases:
i'm getting the message about "you are not privileged"

---

### Post by jerome1232 on 2008-10-18
I forgot a comma and edited it now. I'm actually taking off right now but hopefully that get's her done.

---

### Post by Pacane on 2008-10-18
Tried with the line from your last edit and now I get the same error message as before:
> Unprivilieged user can not mount NTFS block devices using the external FUSE library. Either mount the volume as a root, or rebuild NTFS-3G with integrated FUSE support and make it setuid root. Please see more info at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

Anyways, thanks for your help. Really appreciated, Just come back whenever you want :)

---

### Post by mc4man on 2008-10-18
Out of curiosity if you run 
```
gconf-editor
``` do you see an entry for that volume (drive) under system -> storage and in either 'volumes' or 'drives' and if so what's the key entry?

---

### Post by Pacane on 2008-10-18
No, i do not

---

### Post by Pacane on 2008-10-18
Any idea anyone?

Also, does anyone have some docs about how the fstab exactly works? Like all the options and parameters...

Thanks

---

### Post by jerome1232 on 2008-10-18
I found a bug workaround that looked exactly like your problem, I'm trying to find it again.

As for fstab a good general how-to I thought was this [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

It's a bit dated but very applicable.


Here we go the bug with the workaround [http://ubuntuforums.org/showpost.php?p=5530231&postcount=44](http://ubuntuforums.org/showpost.php?p=5530231&postcount=44)

basically remove the fstab crap, mount the thing to /media/something, right click on it's icon, and start following what it says to do under #4 in that post.

---

### Post by Pacane on 2008-10-18
When you say "remove the fstab crap", does that mean to delete the whole line about the volume or just the automounting parameters?

---

### Post by jerome1232 on 2008-10-18
The whole line, you can just comment it out if you like (with a # sign)

---

### Post by Pacane on 2008-10-19
Oh Wow, it worked! Thanks alot Jerome, for your patience and your grateful help, seriously.

What has been done for others who have the same issue:

Mounted the disk with
sudo mount /dev/yourdrive /media/yourdirformount

then: 
> 4- With the drive mounted successfully return to the HH gui and go to an icon for the drive (I used the icon on the desktop). Right click and select &#8220;properties&#8221; then the &#8220;Drive&#8221; tab of the resulting pop-up. On the &#8220;Drive&#8221; tab click &#8220;settings&#8221; to expand the options and delete anything that is in the three fields (Mount Point; File System; Mount Options) that appear. Then select the &#8220;Volume&#8221; tab and click on &#8220;Settings&#8221; and clear the three fields that appear. Click close on the bottom right side of the pop up.

5- Reboot the system with the drive attached. It should restart with the drive mounted into a default location like /media/DriveLable. At this point you are back where you started and can set a new mount point correctly.


---

### Post by jerlinux on 2008-10-27
Is there any chance that the next upgrade to ubuntu will "fix" this for me?
It is plain that I am in over my head but for 6 months, this thing worked perfectly.  All of a sudden - yeah I know that I must have done something but I sure don't know what - I get the can't start with g message.  I have followed these threads all the way to the ends and still don't see myself finding a fix since I don't even know where to begin.

I do not want to reformat and begin again since I have loaded a lot of things onto this drive and I would also loose all the saved emails.  So, if I wait for the next upgrade, will it overwrite all of my mistakes or will it keep the same settings for the dvd drive?

Thanks

---

### Post by BLTicklemonster on 2009-03-04
I was having fits trying to get my ntfs partitions to load on boot, and was following this thread, and kept putting this

```
/dev/sdc1 /media/disk-1 ntfs rw,user,umask=0111,dmask=0000 0 0
```
(there were several other partitions, also)

in fstab, but was still getting (whether by clicking in nautilus, or doing sudo mount -a)

mount point not there/does not exist (or whatever)

... then it dawned on me...

remove all the added partition stuff from fstab, save, then click on all in nautilus, check their mount points, unmount them, re-edit fstab, save, then:

```
sudo mkdir /media/disk-1
```
and for all the other partitions...

then

```
sudo mount -a
```

and voila.

rebooted, and they are there.

---

