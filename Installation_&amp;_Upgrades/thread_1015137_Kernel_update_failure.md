---
title: "Kernel update failure"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by popie on 2008-12-18
I issued the command: 
```
sudo apt-get dist-upgrade
```
A new kernel appeared (v 2.6.27-9) and I tried to let it install, but I saw an error, and still have the old kernel (v2.6.27-7). Now, no upgrades or dist-upgrades appear when I use apt-get.

The following error message appeared during the upgrade attempt.
```
Your /usr is broken, please fix it before call this wrapper!
```

Can someone point me to the next step? I just installed this OS tonight, not what might be "broken."

---

### Post by arrange on 2008-12-18
If you type ```
cat /usr/sbin/update-grub
``` into the Terminal, does it say that the file doesn't exist? It seems like the script in /sbin/update-grub checks if /usr/sbin/update-grub exists, and if it doesn't, it issues this error message. But I'm not sure if this is really your problem.

---

### Post by taurus on 2008-12-18
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la
```
Is Ubuntu the only OS on that machine or do you have it dualboot--windows & Ubuntu?

```
sudo fdisk
cat /etc/fstab
df -h
```

---

### Post by popie on 2008-12-18
> **arrange said:**
> If you type ```
cat /usr/sbin/update-grub
``` into the Terminal, does it say that the file doesn't exist? It seems like the script in /sbin/update-grub checks if /usr/sbin/update-grub exists, and if it doesn't, it issues this error message. But I'm not sure if this is really your problem.

That file exists, and the cat command lists its contents, which fill several screens.

---

### Post by popie on 2008-12-18
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la
```
Is Ubuntu the only OS on that machine or do you have it dualboot--windows & Ubuntu?

```
sudo fdisk
cat /etc/fstab
df -h
```


Thanks, The machine is actually LinuxMint, which is mostly Ubuntu, and that is the only OS installed.
Here's the output you requested (ls -la)
```

leeb@gigabyte:~$ ls -la
total 10348
drwxr-xr-x  51 leeb leeb    4096 2008-12-18 11:59 .
drwxr-xr-x   3 root root    4096 2008-12-17 19:13 ..
drwx------   3 leeb leeb    4096 2008-12-17 21:56 .adobe
-rw-------   1 leeb leeb    2111 2008-12-18 11:56 .bash_history
-rw-r--r--   1 leeb leeb     220 2008-12-17 19:13 .bash_logout
-rw-r--r--   1 leeb leeb    2925 2008-08-11 19:00 .bashrc
drwxr-xr-x   3 leeb leeb    4096 2008-12-17 19:17 .cache
drwx------   3 leeb leeb    4096 2008-12-17 23:46 .compiz
drwxr-xr-x   9 leeb leeb    4096 2008-12-17 23:49 .config
-rw-r--r--   1 leeb leeb  876686 2008-12-17 18:07 corruption.png
drwx------   3 leeb leeb    4096 2008-12-17 19:17 .dbus
drwxr-xr-x 118 leeb leeb    4096 2008-12-17 21:28 Depot
drwxr-xr-x   2 leeb leeb    4096 2008-12-17 21:53 Desktop
-rw-------   1 leeb leeb      28 2008-12-18 11:59 .dmrc
drwxr-xr-x  38 leeb leeb   12288 2008-12-17 20:27 Documents
drwxr-xr-x   6 leeb leeb    4096 2008-12-17 20:27 dot-purple
drwxr-xr-x   3 leeb leeb    4096 2008-12-17 20:27 dot-VirtualBox
drwxr-xr-x   3 leeb leeb    4096 2008-12-17 20:39 Downloads
-rw-------   1 leeb leeb      16 2008-12-17 19:17 .esd_auth
-rw-r--r--   1 leeb leeb 3115966 2008-12-17 18:07 Firefox_wallpaper.png
drwxr-xr-x   2 leeb leeb    4096 2008-12-18 11:50 .fontconfig
drwx------   5 leeb leeb    4096 2008-12-18 11:59 .gconf
drwx------   2 leeb leeb    4096 2008-12-18 14:04 .gconfd
-rw-r-----   1 leeb leeb       0 2008-12-18 11:43 .gksu.lock
drwx------  10 leeb leeb    4096 2008-12-17 23:46 .gnome2
drwx------   2 leeb leeb    4096 2008-12-17 19:17 .gnome2_private
drwx------   2 leeb leeb    4096 2008-12-17 19:17 .gnupg
drwxr-xr-x   3 leeb leeb    4096 2008-12-18 09:46 .google
drwxr-xr-x   2 leeb leeb    4096 2008-12-17 23:32 .gstreamer-0.10
-rw-r--r--   1 leeb leeb     104 2008-12-18 11:59 .gtk-bookmarks
dr-x------   2 leeb leeb       0 2008-12-18 11:59 .gvfs
drwxr-----   2 leeb leeb    4096 2008-12-17 22:34 .hplip
-rw-------   1 leeb leeb    1141 2008-12-18 11:59 .ICEauthority
drwxr-xr-x   2 leeb leeb    4096 2008-12-17 22:08 .icons
drwxr-xr-x   3 leeb leeb    4096 2008-12-17 21:31 .kde
drwxr-xr-x   5 leeb leeb    4096 2008-12-17 22:06 .linuxmint
drwx------   3 leeb leeb    4096 2008-12-17 19:17 .local
drwx------   3 leeb leeb    4096 2008-12-17 21:56 .macromedia
-rw-r--r--   1 leeb leeb   55901 2008-12-17 18:42 Mint Sound Prefs-HeadsetMic.png
-rw-r--r--   1 leeb leeb   56467 2008-12-17 18:42 Mint Sound Prefs-WebcamMic.png
-rw-r--r--   1 leeb leeb   21114 2008-12-17 18:42 Mint-VolControl-HeadsetMic.png
drwx------   4 leeb leeb    4096 2008-12-17 21:11 .mozilla
drwx------   3 leeb leeb    4096 2008-12-17 21:11 .mozilla-thunderbird
drwxr-xr-x   2 leeb leeb    4096 2008-12-17 23:24 .mplayer
drwxr-xr-x  37 leeb leeb    4096 2008-12-17 20:51 Music
-rw-r--r--   1 leeb leeb   31189 2008-12-17 18:42 my-compiz-settings
drwxr-xr-x   3 leeb leeb    4096 2008-12-17 23:46 .nautilus
-rw-r--r--   1 leeb leeb    1098 2008-12-17 21:37 .nvidia-settings-rc
drwxr-xr-x   3 leeb leeb    4096 2008-12-18 11:56 .openoffice.org
drwx------   3 leeb leeb    4096 2008-12-17 23:13 .openoffice.org2
drwxr-xr-x 110 leeb leeb   12288 2008-12-18 10:20 Pictures
-rw-r--r--   1 leeb leeb     675 2008-12-17 19:13 .profile
drwxr-xr-x   2 leeb leeb    4096 2008-12-17 19:17 Projects
drwxr-xr-x   2 leeb leeb    4096 2008-12-17 23:32 .pulse
drwxr-xr-x   4 leeb leeb    4096 2008-12-17 23:25 pulse-backup
-rw-------   1 leeb leeb     256 2008-12-17 19:17 .pulse-cookie
drwx------   6 leeb leeb    4096 2008-12-18 14:00 .purple
-rw-------   1 leeb leeb    7433 2008-12-18 10:46 .recently-used.xbel
drwx------   3 leeb leeb    4096 2008-12-18 14:03 .Skype
drwxr-xr-x   2 leeb leeb    4096 2008-12-17 20:58 Sonant-db
drwxr-xr-x   4 leeb leeb    4096 2008-12-17 20:58 ssvnc
-rw-r--r--   1 leeb leeb 6085605 2008-12-17 18:42 ssvnc_unix_only-1.0.21.tar.gz
-rw-r--r--   1 leeb leeb       0 2008-12-17 19:17 .sudo_as_admin_successful
drwxr-xr-x   7 leeb leeb    4096 2008-12-17 20:59 Temp
drwxr-xr-x   2 leeb leeb    4096 2008-12-17 22:08 .themes
drwx------   3 leeb leeb    4096 2008-12-17 21:03 .thumbnails
drwxr-xr-x   4 leeb leeb    4096 2008-12-17 19:17 .tomboy
-rw-r--r--   1 leeb leeb    4817 2008-12-18 11:59 .tomboy.log
drwxr-xr-x  18 leeb leeb    4096 2008-12-17 21:02 Tools
drwxr-xr-x   7 leeb leeb   12288 2008-12-17 21:03 Translations
drwxr-xr-x   2 leeb leeb    4096 2008-12-17 19:17 Videos
drwxr-xr-x   2 leeb leeb    4096 2008-12-18 11:59 .wapi
-rw-------   1 leeb leeb     119 2008-12-18 11:59 .Xauthority
-rw-r--r--   1 leeb leeb   17149 2008-12-18 13:51 .xsession-errors
leeb@gigabyte:~$ 

```

```
leeb@gigabyte:~$ sudo fdisk
[sudo] password for leeb: 

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
leeb@gigabyte:~$ sudo fdisk -l
[sudo] password for leeb: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23998be4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38158   306504103+  83  Linux
/dev/sda2           38159       38913     6064537+   5  Extended
/dev/sda5           38159       38913     6064506   82  Linux swap / Solaris
leeb@gigabyte:~$ 

```
```

leeb@gigabyte:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7a060213-478d-4625-b486-ae0f694c72bb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=42876e69-9432-4e09-8777-06f4520eaa2b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
```

leeb@gigabyte:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             288G   39G  235G  15% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  324K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  172K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-7-generic/volatile
leeb@gigabyte:~$ 


```

---

### Post by Jesamyn on 2008-12-20
I ran into this error this evening with my new install of Mint.  I did some digging around, and it turned out to be a permissions issue.

Do:
```
 ls -l /usr/sbin/update-grub
```

It probably looks like:
```
-rw-r--r-- 1 root    root    38778 2008-12-19 23:19 update-grub
```

It's not executable, so it can't be run.  So do:
```
sudo chmod 766 /usr/sbin/update-grub
```

This gives execute permissions to root.  Now you can:
```
sudo update-grub
```

This fixed the issue for me, so hopefully it'll help you.

---

### Post by popie on 2008-12-20
> **Jesamyn said:**
> It probably looks like:
```
-rw-r--r-- 1 root    root    38778 2008-12-19 23:19 update-grub
```

It's not executable, so it can't be run.  So do:
```
sudo chmod 766 /usr/sbin/update-grub
```


Yes! Thanks so much! That worked, (with chmod 755).

I think you have a typo in the chmod command. It should be 755 to make the file executable.

```
sudo chmod 755 /usr/sbin/update-grub
```

That worked for me (and made perms match those of other files in that directory)
```
-rwxr-xr-x 1 root root 38778 2008-12-17 19:32 update-grub
```

---

### Post by Jesamyn on 2008-12-20
chmod 755 makes it executable by any user.  chmod 766 makes it executable by root, read/write by any user.  I used 766 with the idea that you're going to have either be using sudo to run it or one of the package managers is running it, in which case you'd have used sudo to invoke it.  Either way, as long as it works...all good!  Glad it helped. :)

Edited to add:  And I totally understand matching the rest of the directory.  At 3am this morning, I just wanted it to run and didn't check. ;)

---

### Post by popie on 2008-12-20
Of course, you're correct. I had my blinders on...so to speak. "7" is rwx, and we're running it as root. I knew that, but wasn't thinking clearly... Thanks again. :)

---

### Post by dodgefan on 2008-12-27
just wanted to confirm, i had this issue too and making update-grub executable worked for me as well. thanks!

---

### Post by usinguuu on 2009-02-22
> **dodgefan said:**
> just wanted to confirm, i had this issue too and making update-grub executable worked for me as well. thanks!

Seems to be a common issue in Mint. Just do a chmod on update-grub as shown above and everything is ok.

BTW: 755 is the correct file mode. ;)

---

