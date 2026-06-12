---
title: "HDD rights Ubuntu"
date: 2018-10-11
forum: Hardware
---

### Post by kirill732 on 2018-10-11
Hello! I have a problem with HDD rights on Ubuntu. I installed Ubuntu alongside windows 10. I have HDD witch formatted ntfs. I can't make some new folders, new files on Ubuntu, but I can do it on windows 10. I can only read the HDD. What I have to do to solve this problem? I'm rookie in Linux.

---

### Post by TheFu on 2018-10-11
Linux is a multi-user system from the ground up.  Every directory and file has permissions.  Every file system has mount options which can control the permissions at a higher level if the file system isn't native to Linux/Unix.

NTFS is not a native Linux file system. Permissions are controlled during mount. HDDs don't really have "rights", but partitions can, if that is what you meant.

To be of any help, you'll need to be clear on which file system is being used for the storage where you are having issues and which permissions are wanted for which userids and groups.

If you open a shell, change the directory to the place you want to write some files/create directories, then run these commands:
```
df -Th .
mount
ls -al 
id
```
we can probably help.  Linux is extremely powerful and flexible, but that power brings some complexity.

Welcome to the forums.  No need to bold text or change the default text formatting.

---

### Post by kirill732 on 2018-10-11
```
srpb@srpb-Vostro-3578:/media/srpb/&#1053;&#1086;&#1074;&#1099;&#1081; &#1090;&#1086;&#1084;$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3,8G     0  3,8G   0% /dev
tmpfs          tmpfs     775M  2,1M  773M   1% /run
/dev/sda3      ext4       28G  9,4G   17G  37% /
tmpfs          tmpfs     3,8G   11M  3,8G   1% /dev/shm
tmpfs          tmpfs     5,0M  4,0K  5,0M   1% /run/lock
tmpfs          tmpfs     3,8G     0  3,8G   0% /sys/fs/cgroup
/dev/loop0     squashfs  2,4M  2,4M     0 100% /snap/gnome-calculator/180
/dev/loop3     squashfs   87M   87M     0 100% /snap/core/4917
/dev/loop2     squashfs   13M   13M     0 100% /snap/gnome-characters/103
/dev/loop1     squashfs  3,8M  3,8M     0 100% /snap/gnome-system-monitor/51
/dev/loop4     squashfs   35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop5     squashfs   15M   15M     0 100% /snap/gnome-logs/37
/dev/loop6     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/sda6      ext4       42G  5,9G   34G  16% /home
tmpfs          tmpfs     775M   16K  775M   1% /run/user/121
tmpfs          tmpfs     775M   40K  775M   1% /run/user/1000
/dev/sdb3      fuseblk   918G   63G  856G   7% /media/srpb/&#1053;&#1086;&#1074;&#1099;&#1081; &#1090;&#1086;&#1084;
```


```
srpb@srpb-Vostro-3578:/media/srpb/&#1053;&#1086;&#1074;&#1099;&#1081; &#1090;&#1086;&#1084;$ ls -al
total 8
drwxrwxrwx  1 srpb srpb 4096 &#1086;&#1082;&#1090;  8 17:03  .
drwxr-x---+ 3 root root 4096 &#1086;&#1082;&#1090; 11 12:37  ..
drwxrwxrwx  1 srpb srpb    0 &#1072;&#1074;&#1075; 13 16:25  kirill
drwxrwxrwx  1 srpb srpb    0 &#1080;&#1102;&#1085; 28 00:00 '$RECYCLE.BIN'
drwxrwxrwx  1 srpb srpb    0 &#1080;&#1102;&#1085; 27 23:40 'System Volume Information'

```

```
srpb@srpb-Vostro-3578:/media/srpb/&#1053;&#1086;&#1074;&#1099;&#1081; &#1090;&#1086;&#1084;$ id
uid=1000(srpb) gid=1000(srpb) groups=1000(srpb),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare)

srpb@srpb-Vostro-3578:/media/srpb/&#1053;&#1086;&#1074;&#1099;&#1081; &#1090;&#1086;&#1084;$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=3933448k,nr_inodes=983362,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=792740k,mode=755)
/dev/sda3 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=24,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=20602)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
/var/lib/snapd/snaps/gnome-calculator_180.snap on /snap/gnome-calculator/180 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_4917.snap on /snap/core/4917 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_103.snap on /snap/gnome-characters/103 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_51.snap on /snap/gnome-system-monitor/51 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_319.snap on /snap/gtk-common-themes/319 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_37.snap on /snap/gnome-logs/37 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_70.snap on /snap/gnome-3-26-1604/70 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sda6 on /home type ext4 (rw,relatime,data=ordered)
tmpfs on /run/user/121 type tmpfs (rw,nosuid,nodev,relatime,size=792736k,mode=700,uid=121,gid=125)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=792736k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdb3 on /media/srpb/&#1053;&#1086;&#1074;&#1099;&#1081; &#1090;&#1086;&#1084; type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
```

---

### Post by TheFu on 2018-10-11
code tags, like I used, would be very helpful for readability. Please.   Edit--> Go Advanced(#) or Adv Reply for new posts. Or you can just use the "quote" tags and manually change quote --> "code"

---

### Post by kirill732 on 2018-10-11
I’ve solved the problem. I used recursive chmod for all files on the HDD.

---

### Post by TheFu on 2018-10-11
> **kirill732 said:**
> I’ve solved the problem. I used recursive chmod for all files on the HDD.

That does NOTHING on an NTFS file system.
Doing it on an OS file system will break the install.

---

