---
title: "[SOLVED] unable to mount drive after editing mount point"
date: 2008-05-09
forum: Hardware
---

### Post by werries on 2008-05-09
Ok. So I have two harddrives. One is a 160 gb internal, and is partitioned to 80gb of windows, and the rest is split between ubuntu and the swap partition. and i also have an external drive.

Now, I wanted my windows partition to always mount at a specific spot, as the external would mount first if it was plugged in, and thus causing issues when i mounted the windows one and then plugging in the external second (such as banshee being unable to find my music.)

So, being a bit of a linux noob, i used the GUI. Right clicked the drive on the desktop, went to properties > Volume and edited the mount options to be /media/disk-1. Needless to say, unmounting and remounting broke it.

so i haven't edited mtab or fstab nor have i ever tried. So when I try to mount, it says "cannot mount volume". with details as "mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)".

I would like to know how to reset these settings and make it the default or automatically assign or whatever. I went to Places > Computer and then right clicked the unmounted partition, but when i looked in the properties there was no volume tab. Help?

---

### Post by Patb on 2008-05-10
Werries, perhaps [this recent discussion]("http://ubuntuforums.org/showthread.php?t=782689#2") might help.  I would be inclined to edit /etc/fstab rather than use symbolic links but then I'm perhaps a bit of a control freak :).  

If you need specific guidance in addition to what's in that thread, please post.  

Cheers, Pat.

---

### Post by shamael on 2008-05-10
I am not familiar with modification of fstab through the GUI, so you might be able to get things done that way too, however I suggest you get your fstab right and mount your win partition in some directory in /mnt/. When that is working, you can create a symlink to it and place it wherever you find appropriate.
Furthermore, you'll almost certainly need to know how to edit fstab for other tasks in the future, so I think that spending half an hour with it will prove to be very useful!

Try going through the fstab and mount man pages, they are well documented, and if you still have problems report here.

Good luck

---

### Post by werries on 2008-05-10
ok. some sort of progress.
after looking at that thread, i edited my fstab and mtab.
for fstab i added the line
```
/dev/sda1 /media/sda1     ntfs    defaults        0       2
```
and then i tried
```
sudo mount -a
```
and it said cannot create link to mtab, stale lock file.
so i went to mtab and added 
```
/dev/sda1 /media/sda1 ntfs rw 0 0
```
And went to mount, tried mounting all again, and that ran without errors. but it didnt actually mount anything. Tried using the gui mounter, nothin. it just didnt mount, no errors.
Anything you guys see wrong with what i added?

---

### Post by shaggy999 on 2008-05-10
My recommendation is that you go back to using the GUI. The problem you ran into originally was that you probably put something like "/media/disk-1" as the mount point. However, what you actually want to put is just "disk-1" and it will mount as "/media/disk-1". You can't put "/" characters into the mountpoint, just a simple name, and it will get mounted to "/media/nameyouchose".

---

### Post by werries on 2008-05-10
i would but the problem is when i right click on the drive, and bring up the properties, there is no volume tab for some reason. So i cannot change the mount options via GUI.

---

### Post by vanadium on 2008-05-10
> and then i tried
Code:

sudo mount -a

and it said cannot create link to mtab, stale lock file.
so i went to mtab and added 


Why don't you just copy/paste all output of this command here? mtab is not intended to be edited, so stay away from it.

I agree with the suggestion of shamael.

---

### Post by werries on 2008-05-10
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8bfa3512-be95-4c80-968d-f4da8b65745e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ee0634f1-c9ab-4261-998b-a1aea8b2161e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 /media/sda1     ntfs    defaults        0       0
```
Last line is the line i added.

```
/dev/sda6 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/adam/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=adam 0 0
/dev/sdb1 /media/disk fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sda1 /media/sda1 ntfs rw 0 0
```
last line added.

and if so, should i just remove the last line or something?

---

### Post by ASULutzy on 2008-05-10
Use UUID's instead of /dev/whatever.

If you have an external drive that is getting mounted in different orders each time and causing problems, you should issue the command blkid /dev/whatever and it will give you the UUID of the drive you asked for (you may need to do sudo blkid /dev/whatever if you're not a member of the disk group)

If you use UUID's it won't matter which order things get connected in. Here's my fstab to show what I mean.```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=6C84980B8497D644     /media/TB    ntfs-3g   force    0    0
UUID=a0d72a95-f804-4881-96de-8de3ceafe674   /   ext3   relatime,errors=remount-ro    0 1
UUID=2718cdf7-1459-48d1-bc38-cc9563805eb5      none     swap     sw     0     0
UUID=427e4989-2a85-8f0c-76d1-19d92e132bd9   none  swap     sw      0     0
UUID=1048F91148F8F676        /media/newdisk      ntfs-3g       force     0       0 
UUID=786AD4166AD3CECE        /media/Big\040drive     ntfs-3g     force     0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by werries on 2008-05-10
so i went out. shut down computer
came back, and booted.
drive automatically mounted. it worked!
also changed to UUID afterwards, worked after boot also. :)
thanks all

---

### Post by bananafishbones on 2009-03-29
> **ASULutzy said:**
> Use UUID's instead of /dev/whatever.

If you have an external drive that is getting mounted in different orders each time and causing problems, you should issue the command blkid /dev/whatever and it will give you the UUID of the drive you asked for (you may need to do sudo blkid /dev/whatever if you're not a member of the disk group)

If you use UUID's it won't matter which order things get connected in. Here's my fstab to show what I mean.```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=6C84980B8497D644     /media/TB    ntfs-3g   force    0    0
UUID=a0d72a95-f804-4881-96de-8de3ceafe674   /   ext3   relatime,errors=remount-ro    0 1
UUID=2718cdf7-1459-48d1-bc38-cc9563805eb5      none     swap     sw     0     0
UUID=427e4989-2a85-8f0c-76d1-19d92e132bd9   none  swap     sw      0     0
UUID=1048F91148F8F676        /media/newdisk      ntfs-3g       force     0       0 
UUID=786AD4166AD3CECE        /media/Big\040drive     ntfs-3g     force     0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Thanks for you help!! I have two 500GB USB drives and one is used as a backup. So I wanted to setup their mounting to be consistent every time so that my backups would work correctly. USB drives will mount with different /dev/sd whatevers every time. I didn't know how to setup UUID's until I found your post. Big thanks again!
Cheers,
BF

---

