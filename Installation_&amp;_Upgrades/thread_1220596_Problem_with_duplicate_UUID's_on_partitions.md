---
title: "Problem with duplicate UUID's on partitions"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by deejay_99 on 2009-07-23
I just installed Ubuntu 9.04 and have the following partitions:



[LIST]
[*]dev/sda1  ... mounted as "windows_old" .... fat 32 on separate old  27 gig hard drive .... UUID=1174-1cd3
[*]dev/sdb1 ... ... mounted as "windows" .... fat 32 - 117gig partition for windows xp on new hard drive ... UUID=1174-1cd3
[*]dev/sdb2 ..... ubuntu "/"  .....  47 gig partition on new hard drive
[*]dev/sdb5 .... ubuntu "/home"  .... 66 gig partition on new hard drive
[*]dev/sdb3 ... swap ... 2 gig partition on new hard drive
[/LIST]


Both "windows_old" and "windows" are mounting the dev/sdb1 ... when "windows_old" should be mounting the /dev/sda1 partition.


Here is my fstab:


[B]# /etc/fstab: static file system information.

# / was on /dev/sdb2 during installation
UUID=1665d875-436c-4cf3-a777-b6f03504d6e5 /               ext3    relatime,errors=remount-ro 0       1
[/B]

[B]# /home was on /dev/sdb5 during installation
UUID=8e41ee9e-15e0-4d8d-a3d2-9fc9d1a5dd32 /home           ext3    relatime        0       2
[/B]

[B]# /windows was on /dev/sdb1 during installation
UUID=1174-1CD3  /windows        vfat    utf8,umask=007,gid=46 0       1
[/B]

[B]# /windows_orig was on /dev/sda1 during installation
UUID=1174-1CD3  /windows_orig   vfat    utf8,umask=007,gid=46 0       1
[/B]

[B]/dev/sdb3       none            swap    sw              0       0
[/B]

**/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0**


Here is my mtab:


[B]/dev/sdb2 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-13-generic/volatile tmpfs rw,mode=755 0 0
/dev/sdb5 /home ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/doug/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=doug 0 0
/dev/sdc1 /media/USB\040Mobile\040Drive fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /windows_orig vfat rw,utf8,umask=007,gid=46 0 0
/dev/sdb1 /windows vfat rw [/B]0 0


The bottom two lines show both "windows" and "windows_old" mounts pointing to /dev/sdb1 ... I assume because they have been both assigned the same UUID.


Any ideas on how I can fix this? 


(Also, in mtab, why does the first line  **/dev/sdb2 / ext3 rw,relatime,errors=remount-ro 0 0 **show an error?Does this need fixing?[B])
[/B]

---

### Post by eternalsword on 2009-07-23
> **deejay_99 said:**
> (Also, in mtab, why does the first line  **/dev/sdb2 / ext3 rw,relatime,errors=remount-ro 0 0 **show an error?Does this need fixing?[B])
[/B]

all that means is if there are errors with mounting the disk normally, it will try remounting it read-only so you can possibly recover data from a failing partition.  Nothing to fix there.

The primary issue is that windows_orig and windows have been assigned to mount the same partition, hence identical UUIDs.  To fix this, you'll need to find out the UUID for /dev/sda1

you can find out the UUID for /dev/sda1 by entering the following command in a terminal
```

ls -l /dev/disk/by-uuid | grep 'sda1'
```

this should produce something like
```
lrwxrwxrwx 1 root root 10 2009-07-05 23:04 **edc5f364-2a69-4204-a328-11c059e00f71** -> ../../sda1
```

the section containing the uuid is in bold, go ahead and copy that part from your output to your clipboard.

if the UUID matches 1174-1CD3, rerun the previous command except replace sda1 with sdb1.

now make a backup of your fstab (always good practice to back-up system files before modification).

```
sudo cp /etc/fstab /etc/fstab.bak
```

now edit the fstab

```
gksu gedit /etc/fstab
```

paste in the UUID that you copied earlier in the line corresponding to windows_orig if sda1 gave you a different UUID or to windows if sdb1 gave you a different UUID.

---

### Post by deejay_99 on 2009-07-23
Thanks for your suggestion. The uuid's show the same for both:

root@ubuntu1:~# blkid
/dev/sda1: UUID="1174-1CD3" TYPE="vfat" LABEL="WINDOWS_ORI" 
/dev/sdb1: UUID="1174-1CD3" TYPE="vfat" LABEL="WINDOWS" 
/dev/sdb2: UUID="1665d875-436c-4cf3-a777-b6f03504d6e5" TYPE="ext3" 
/dev/sdb3: TYPE="swap" 
/dev/sdb5: UUID="8e41ee9e-15e0-4d8d-a3d2-9fc9d1a5dd32" TYPE="ext3" 
/dev/sdc1: UUID="74D4F67CD4F63FC2" LABEL="USB Mobile Drive" TYPE="ntfs" 

Why would Ubuntu issue the same UUID to two different partitions (on separate hard drives!)?

I should mention that the "windows" and "windows_orig" files/directories were an exact copy of the other  ... could this have confused ubuntu, thinking they were the same info, so it gave them the same UUID?

Is there any way to change or create a new UUID? If I unmount, modify the partition, and remount would a new UUID be assigned? Any other way?

---

### Post by dandnsmith on 2009-07-23
There is some info (I suggest google for it) about UUIDs and Windows.

An important thing to remember is that Ubuntu **doesn't** issue the UUIDs for the Windows partitions, they are information which has been put there by the Windows installation.

If you try changing UUID with linux tools, you may find you've clobbered the Windows installation (and it will treat it as a corrupt filesystem) - so do some research first.

---

### Post by eternalsword on 2009-07-23
Since they are reporting the same UUID, you can use the actual devices instead.  

So this
```
# /windows was on /dev/sdb1 during installation
UUID=1174-1CD3 /windows vfat utf8,umask=007,gid=46 0 1


# /windows_orig was on /dev/sda1 during installation
UUID=1174-1CD3 /windows_orig vfat utf8,umask=007,gid=46 0 1
```

would become
```
# /windows was on /dev/sdb1 during installation
/dev/sdb1 /windows vfat utf8,umask=007,gid=46 0 1


# /windows_orig was on /dev/sda1 during installation
/dev/sda1 /windows_orig vfat utf8,umask=007,gid=46 0 1
```

UUID in fstab is really only needed for mounting devices that shift around in order.  In your case I think you would be safe.

---

### Post by deejay_99 on 2009-07-23
Thanks for all your help. I didn't realize UUID was assigned by Windows!

I did some more digging, and found out you can mount partitions by label. I unmounted the two partitions, labelled them and remounted using the label as the reference, not the UUID ... it worked!!!

All your comments helped this newbie learn more about Ubuntu, mounitng partitions and the file system.

---

