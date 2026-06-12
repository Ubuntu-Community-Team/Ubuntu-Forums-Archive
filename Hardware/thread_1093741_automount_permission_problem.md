---
title: "automount permission problem"
date: 2009-03-11
forum: Hardware
---

### Post by _BigWings_ on 2009-03-11
Hey all,

I have installed the pysdm graphical storage manager to make it automount my shared (with windows) partition on my hard drive. Th automount seems to work well if not for the fact that only the root user has write permission on it. How can I change it so every user has write permission?

I am new to ubuntu and I don't really get the concept of permissions anyways. Anyone care to explain why it is necessary to have file permissions if you are not sharing your pc with several people and you are accessing the computer physically, instead of through a network.
Why is it that I have to put 'sudo' in front of just about any terminal command I type? Isn't that just superfluous?

M

---

### Post by taurus on 2009-03-12
1.  What filesystem is the partition you want to write to?  Probably ntfs since you share that partition with windows.

Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

2.  Not every command requires you to run with sudo.  You only use sudo if you want to modify (or access) system files.  What happens when you run these commands without sudo from a terminal?

```
ls -la
whoami
finger
cd ~/Desktop
df -h
free -m
```

---

### Post by _BigWings_ on 2009-03-12
I am trying to write to a fat32 drive that I set up especially the purpose of sharing files between linux and windows.

Here are the results of the commands you suggested:
```

martijn@martijn-laptop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9f1b197

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30664   246300640    7  HPFS/NTFS
/dev/sda2           59223       60801    12680192    7  HPFS/NTFS
/dev/sda3           30665       56673   208917292+   b  W95 FAT32
/dev/sda4           56674       59222    20474842+  83  Linux

Partition table entries are not in disk order



martijn@martijn-laptop:~$ sudo blkid
/dev/sda1: UUID="0053406563D196BE" TYPE="ntfs" 
/dev/sda2: UUID="8A2000FF2000F3CB" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: LABEL="Data" UUID="499F-F750" TYPE="vfat" 
/dev/sda4: UUID="765f9b3a-8235-4bb7-a840-9bf3d523ed94" TYPE="ext2" 



martijn@martijn-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                           0  0  
# /dev/sda4
UUID=765f9b3a-8235-4bb7-a840-9bf3d523ed94  /                ext2         relatime,errors=remount-ro         0  1  
/dev/scd0                                  /media/cdrom0    udf,iso9660  user,noauto,exec,utf8              0  0  
/dev/sda3                                  /media/data      auto         defaults                           0  1  
/dev/sda2                                  /media/recovery  ntfs         nls=iso8859-1,noauto,umask=000,ro  0  0  
/dev/sda1                                  /media/Vista     ntfs         nls=iso8859-1,noauto,umask=000,ro  0  0 



martijn@martijn-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              20G  5.3G   14G  29% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.9M  1.5G   1% /dev
tmpfs                 1.5G  104K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda3             200G  1.8G  198G   1% /media/data
/dev/scd0             7.5G  7.5G     0 100% /media/cdrom0


```

and the second batch of commands:

```

martijn@martijn-laptop:~$ ls -la
total 412
drwxr-xr-x 48 martijn martijn   4096 2009-03-12 22:32 .
drwxr-xr-x  3 root    root      4096 2009-02-21 08:00 ..
drwx------  3 martijn martijn   4096 2009-02-28 13:35 .adobe
-rw-------  1 martijn martijn    934 2009-03-12 02:01 .bash_history
-rw-r--r--  1 martijn martijn    220 2009-02-21 08:00 .bash_logout
-rw-r--r--  1 martijn martijn   3115 2009-02-21 08:00 .bashrc
-rw-r--r--  1 martijn martijn 132672 2009-03-11 22:12 .B.blend
drwxr-xr-x  5 martijn martijn   4096 2009-03-12 02:02 .blender
-rw-r--r--  1 martijn martijn    176 2009-03-12 00:32 .Blog
drwxr-xr-x  4 martijn martijn   4096 2009-03-01 18:56 .cache
drwx------  3 martijn martijn   4096 2009-03-09 23:05 .compiz
drwxr-xr-x  8 martijn martijn   4096 2009-03-08 19:58 .config
drwx------  3 martijn martijn   4096 2009-02-21 08:04 .dbus
drwxr-xr-x  2 martijn martijn   4096 2009-03-11 22:07 Desktop
-rw-------  1 martijn martijn      2 2009-03-12 22:32 .dmrc
drwxr-xr-x  2 martijn martijn   4096 2009-03-12 00:36 Documents
-rw-------  1 martijn martijn     16 2009-02-21 08:04 .esd_auth
lrwxrwxrwx  1 martijn martijn     26 2009-02-21 08:00 Examples -> /usr/share/example-content
drwxr-xr-x  2 martijn martijn   4096 2009-03-07 15:36 .fontconfig
drwx------  5 martijn martijn   4096 2009-03-12 22:32 .gconf
drwx------  2 martijn martijn   4096 2009-03-12 22:38 .gconfd
drwx------  4 martijn martijn   4096 2009-03-01 19:52 .gegl-0.0
drwxr-xr-x 22 martijn martijn   4096 2009-03-08 21:58 .gimp-2.6
-rw-r-----  1 martijn martijn      0 2009-03-11 22:20 .gksu.lock
drwx------ 12 martijn martijn   4096 2009-03-10 00:20 .gnome2
drwx------  2 martijn martijn   4096 2009-02-21 08:04 .gnome2_private
drwx------  2 martijn martijn   4096 2009-02-21 08:04 .gnupg
drwxr-xr-x  2 martijn martijn   4096 2009-03-10 00:04 .gstreamer-0.10
-rw-r--r--  1 martijn martijn    108 2009-03-12 22:32 .gtk-bookmarks
dr-x------  2 martijn martijn      0 2009-03-12 22:32 .gvfs
drwx------  2 martijn martijn   4096 2009-03-01 19:21 .homebank
-rw-------  1 martijn martijn   4200 2009-03-12 22:32 .ICEauthority
drwxr-xr-x  2 martijn martijn   4096 2009-03-07 13:07 .icons
drwxr-x---  7 martijn martijn   4096 2009-03-01 19:49 .inkscape
drwxr-xr-x  3 martijn martijn   4096 2009-03-07 03:15 .java
drwxr-xr-x  8 martijn martijn   4096 2009-03-09 23:40 .jedit
drwx------  3 martijn martijn   4096 2009-03-07 19:20 .kde
drwx------  3 martijn martijn   4096 2009-02-21 08:04 .local
drwx------  3 martijn martijn   4096 2009-02-28 13:35 .macromedia
drwxr-xr-x  3 martijn martijn   4096 2009-03-07 19:22 .mcop
-rw-------  1 martijn martijn     31 2009-03-07 19:22 .mcoprc
drwx------  4 martijn martijn   4096 2009-03-01 19:08 .mozilla
drwx------  3 martijn martijn   4096 2009-03-01 19:08 .mozilla-thunderbird
drwxr-xr-x  2 martijn martijn   4096 2009-02-21 08:04 Music
drwxr-xr-x  3 martijn martijn   4096 2009-03-09 23:05 .nautilus
-rw-r--r--  1 martijn martijn   1176 2009-03-09 22:36 .nvidia-settings-rc
drwxr-xr-x  2 martijn martijn   4096 2009-02-21 08:04 Pictures
-rw-r--r--  1 martijn martijn    675 2009-02-21 08:00 .profile
drwxr-xr-x  2 martijn martijn   4096 2009-02-21 08:04 Public
drwxr-xr-x  2 martijn martijn   4096 2009-02-21 08:04 .pulse
-rw-------  1 martijn martijn    256 2009-02-21 08:04 .pulse-cookie
drwx------  6 martijn martijn   4096 2009-03-12 02:02 .purple
drwxr-xr-x  2 martijn martijn   4096 2009-03-07 19:20 .qt
-rw-------  1 martijn martijn  20599 2009-03-11 22:05 .recently-used.xbel
drwxrwx---  3 martijn martijn   4096 2009-03-07 03:01 .sane
drwx------  2 martijn martijn   4096 2009-03-11 22:16 .scim
drwx------  4 martijn martijn   4096 2009-03-01 19:27 .songbird2
-rw-r--r--  1 martijn martijn      0 2009-02-21 07:12 .sudo_as_admin_successful
drwxr-xr-x  2 martijn martijn   4096 2009-02-21 08:04 Templates
drwxr-xr-x  2 martijn martijn   4096 2009-03-07 13:07 .themes
drwx------  4 martijn martijn   4096 2009-03-07 13:09 .thumbnails
drwxr-xr-x  2 martijn martijn   4096 2009-02-21 19:20 .update-manager-core
drwx------  2 martijn martijn   4096 2009-03-08 21:35 .update-notifier
drwxr-xr-x  2 martijn martijn   4096 2009-02-21 08:04 Videos
drwxr-xr-x  2 martijn martijn   4096 2009-03-07 13:09 .wapi
-rw-------  1 martijn martijn    125 2009-03-12 22:32 .Xauthority
-rw-r--r--  1 martijn martijn    129 2009-03-07 13:08 .xscreensaver-getimage.cache
-rw-r--r--  1 martijn martijn   1740 2009-03-12 22:32 .xsession-errors

martijn@martijn-laptop:~$ whoami
martijn

martijn@martijn-laptop:~$ finger
Login     Name       Tty      Idle  Login Time   Office     Office Phone
martijn   Martijn    tty7     4:21  Mar 12 22:32 (:0)
martijn   Martijn    pts/0          Mar 12 22:38 (:0.0)

martijn@martijn-laptop:~$ cd ~/Desktop
martijn@martijn-laptop:~/Desktop$ dh -h
The program 'dh' is currently not installed.  You can install it by typing:
sudo apt-get install debhelper
bash: dh: command not found

martijn@martijn-laptop:~/Desktop$ free -m
             total       used       free     shared    buffers     cached
Mem:          3036        667       2369          0         57        261
-/+ buffers/cache:        348       2688
Swap:            0          0          0

``` 


hope that helps you to help me out with this.

M

---

### Post by taurus on 2009-03-12
> **_BigWings_ said:**
> 

martijn@martijn-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                           0  0  
# /dev/sda4
UUID=765f9b3a-8235-4bb7-a840-9bf3d523ed94  /                ext2         relatime,errors=remount-ro         0  1  
/dev/scd0                                  /media/cdrom0    udf,iso9660  user,noauto,exec,utf8              0  0  
**[COLOR="Red"]/dev/sda3                                  /media/data      auto         defaults                           0  1  [/COLOR]**
/dev/sda2                                  /media/recovery  ntfs         nls=iso8859-1,noauto,umask=000,ro  0  0  
/dev/sda1                                  /media/Vista     ntfs         nls=iso8859-1,noauto,umask=000,ro  0  0 


Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace the entry for /dev/sda3 with this one.

```
/dev/sda3   /media/data   vfat   iocharset=utf8,umask=000   0   0
```
Save it and reboot.  Now, see if you can write to /media/data.

---

### Post by _BigWings_ on 2009-03-14
works like a charm now. Thanks!
One more question Taurus: 27.700 posts?!?!
Thats 7 and a half posts per day for ten years straight!

---

