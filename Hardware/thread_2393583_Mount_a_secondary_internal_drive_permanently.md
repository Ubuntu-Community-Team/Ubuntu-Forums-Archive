---
title: "Mount a secondary internal drive permanently"
date: 2018-06-05
forum: Hardware
---

### Post by casecrs87 on 2018-06-05
Hi there, 
I'm having an issue when trying watch movies/tv shows through Kodi where I have to manually open the drive with the media stored on it before Kodi will recognise that the drive is there. 
If i start my computer and open Kodi to try and watch a movie or TV show it will say the file is no longer available. When I close Kodi, navigate to the drive to where I can see the Folders on the drive, then open Kodi again everything works fine. 

Is there a way to setup the drive so that I don't need to open it manually every time I restart the computer?

---

### Post by slickymaster on 2018-06-05
Thread moved to **Hardware** for a better fit

---

### Post by #&amp;thj^% on 2018-06-05
The easiest way to auto mount drives is to open "Disks" from the Menu.
If it is not installed install with:
```
sudo apt-get install gnome-disks
```
Now with the GUI open click on the Drive or Drives wanted to "Automount"
Now below you will see Options with a Gear click that and select "Edit Mount options"
And if User Session Defaults is on click to "Off" and and make sure you check "Mount at Start up"
See Screen shot for more help.

---

### Post by casecrs87 on 2018-06-05
Thanks for the quick reply!
I've gone in and set it to "Automount" on startup but still have the issue. 
I switched over from Windows a few days ago so the drive with all the media on it is NTFS not sure if thats a problem or not.

---

### Post by #&amp;thj^% on 2018-06-05
You will need to reboot to see the changes.
And my drives are "Fat, ext4, and NTFS" and no problems here.

---

### Post by casecrs87 on 2018-06-05
I did reboot after i set it to automount but still have the issue

---

### Post by deadflowr on 2018-06-05
> **casecrs87 said:**
> I did reboot after i set it to automount but still have the issue

post the terminal output from
```
cat /etc/fstab
```

---

### Post by casecrs87 on 2018-06-05
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0


/dev/disk/by-uuid/5E38AE0638ADDCF1 /mnt/5E38AE0638ADDCF1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

---

### Post by deadflowr on 2018-06-05
I think you need to add something to the *x-gvfs-show* option.
Try
```
sudo nano /etc/fstab
```
and change the line 
```
x-gvfs-show
```
to
```
comment=x-gvfs-show
```
so the new whole line will read
```
/dev/disk/by-uuid/5E38AE0638ADDCF1 /mnt/5E38AE0638ADDCF1 auto nosuid,nodev,nofail,comment=x-gvfs-show 0 0
```
then press ctrl + x
then press Y
and then enter to save and exit.

There's an old bug on it:[lpbug]1011257[/lpbug]
sort of.

see if that helps

---

### Post by #&amp;thj^% on 2018-06-05
EDIT Ninja'd by deadflowr :)
Maybe this will show us more:
```
sudo blkid
```
Mine looks like:
```
/dev/sda2: UUID="b007b23d-e1b5-40de-a8fb-dc2d89f83347" TYPE="swap" PARTUUID="3b86fb28-be10-49fb-8bbc-64b2a91a1c82"
/dev/sda3: UUID="ed5a7d7e-281d-48d6-a50c-e9705c769a63" TYPE="ext4" PARTUUID="03d2c09d-ce8e-4cfa-bd65-70fed176fb32"
/dev/sda4: LABEL="Storage" UUID="09771289047AED44" TYPE="ntfs" PTTYPE="dos" PARTLABEL="Storage" PARTUUID="7cff8bbf-c228-4c1f-bb42-864f3bdeb706"
/dev/sdb1: UUID="25B65825105A7849" TYPE="ntfs" PTTYPE="dos" PARTUUID="4b00b5c7-01"
/dev/sdb2: UUID="b66538cb-b17b-4e11-b2eb-e7c049d2f762" TYPE="ext4" PARTUUID="4b00b5c7-02"
/dev/sda1: PARTUUID="47a9c679-9d08-4b0c-8b3f-7501d539a2c5"
/dev/sdd1: LABEL="Media Backup" UUID="5AE38C0C050290D6" TYPE="ntfs" PTTYPE="dos" PARTUUID="f3e03361-74bc-40b5-ad5f-6b324bcf85a3"
/dev/sdd5: LABEL="RECOVERY" UUID="BE0A01740A012ACB" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="57eb2928-b54e-4ca9-8ffb-40e08b429fb7"
/dev/sde1: UUID="454A-5FBC" TYPE="vfat" PARTUUID="000d4424-01"
/dev/sde2: UUID="D1E5-BBD1" TYPE="vfat" PARTUUID="000d4424-02"


```
And for what it's worth my NTFS lists as :
```
nosuid,nodev,nofail,**x-gvfs-show**
```

---

### Post by deadflowr on 2018-06-05
Also, being it's an NTFS partition, I'm not sure whether or not it needs a more definitive file system type instead of just auto.
Just a thought.

---

### Post by casecrs87 on 2018-06-05
switching it to comment=x-gvfs-show made it not work at all for some reason, was unable to get anything to play in kodi the way i could before I switched it to comment=x-gvfs-show.

Here's the output from blkid

```
/dev/sda1: UUID="5ZNwQT-eDZl-PGNY-jRnv-2FJc-Nt30-Xbcd0s" TYPE="LVM2_member" PARTUUID="e9d8d7f0-01"
/dev/sdb2: LABEL="Media" UUID="5E38AE0638ADDCF1" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="e5fcb311-d08c-4133-8de0-2360b0c44c19"
/dev/sdc1: LABEL="UBUNTU 18_0" UUID="82FE-7628" TYPE="vfat" PARTUUID="7f9e647b-01"
/dev/mapper/ubuntu--vg-root: UUID="b0a3dc1c-55e1-4ce2-b7dc-1726ee0a799d" TYPE="ext4"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sdb1: PARTLABEL="Microsoft reserved partition" PARTUUID="b8a0a625-0cb2-47d9-a325-43a4b2e643f5"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/mapper/ubuntu--vg-swap_1: UUID="0f51eb73-7569-4fd6-8620-1a5bfdb4aedb" TYPE="swap"
```

---

### Post by slickymaster on 2018-06-05
@casecrs87:

Please[ use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting terminal output, please.

---

### Post by deadflowr on 2018-06-05
run
```
sudo mount -a
```
and 
```
mount
```
post back results

---

### Post by casecrs87 on 2018-06-05
```
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1922512k,nr_inodes=480628,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=390580k,mode=755)
/dev/mapper/ubuntu--vg-root on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=40,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=15488)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
sunrpc on /run/rpc_pipefs type rpc_pipefs (rw,relatime)
/var/lib/snapd/snaps/gnome-system-monitor_36.snap on /snap/gnome-system-monitor/36 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_170.snap on /snap/gnome-calculator/170 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_25.snap on /snap/gnome-logs/25 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_69.snap on /snap/gnome-characters/69 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_96.snap on /snap/gnome-characters/96 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_59.snap on /snap/gnome-3-26-1604/59 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_4486.snap on /snap/core/4486 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_4650.snap on /snap/core/4650 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_154.snap on /snap/gnome-calculator/154 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_41.snap on /snap/gnome-system-monitor/41 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_64.snap on /snap/gnome-3-26-1604/64 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_34.snap on /snap/gnome-logs/34 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sdb2 on /mnt/5E38AE0638ADDCF1 type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096,x-gvfs-show)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=390576k,mode=700,uid=1000,gid=1000)
/etc/auto.data on /data type autofs (rw,relatime,fd=6,pgrp=995,timeout=300,minproto=5,maxproto=5,indirect,pipe_ino=24253)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdc1 on /media/media/UBUNTU 18_0 type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)
```

---

### Post by #&amp;thj^% on 2018-06-05
> **deadflowr said:**
> run
```
sudo mount -a
```
and 
```
mount
```
post back results

+1 ;)
I blew right by OP "fstab" entry
But mine:
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a device; this may
# be used with UUID= as a more robust way to name devices that works even if
# disks are added and removed. See fstab(5).
#
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=b007b23d-e1b5-40de-a8fb-dc2d89f83347 swap           swap    defaults,noatime 0 2
UUID=ed5a7d7e-281d-48d6-a50c-e9705c769a63 /              ext4    defaults,noatime 0 1
**UUID=09771289047AED44                    /Storage       ntfs    defaults,noatime 0 0**

```
So now we have you totally confused right? :p

---

### Post by Morbius1 on 2018-06-05
> /dev/sdb2 on /mnt/5E38AE0638ADDCF1 type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096,x-gvfs-show)
It is mounted.
What permissions are on the mount:
```
ls -dl /mnt/5E38AE0638ADDCF1
```

---

### Post by casecrs87 on 2018-06-05
```
drwxrwxrwx 1 root root 4096 Jun  4 09:02 /mnt/5E38AE0638ADDCF1


```

I ended up removing the media source from Kodi and then readding it and after rebooting a few times kodi seems to be able to see the drive all the time now.
Thanks for all the help!

---

