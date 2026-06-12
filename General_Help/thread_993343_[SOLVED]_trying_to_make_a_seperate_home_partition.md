---
title: "[SOLVED] trying to make a seperate home partition"
date: 2008-11-25
forum: General Help
---

### Post by jakupl on 2008-11-25
I am trying to make a seperate home partition following [this guide]("http://www.psychocats.net/ubuntu/separatehome")

But when I try to do the strange command
```
find . -depth -print0 | cpio --null --sparse -pvd /new/
```
I get a lot of "permission denied", I also tried:
```
sudo find . -depth -print0 | cpio --null --sparse -pvd /new/
```
with the same result. what should I do?

---

### Post by jakupl on 2008-11-26
bump...

---

### Post by caljohnsmith on 2008-11-26
Although you can actually do it easier with a "cp -ax", to answer your question you could use:
```
find . -depth -print0 | [COLOR="Blue"]sudo[/COLOR] cpio --null --sparse -pvd /new/
```
Give that a shot and let me know how it goes. :)

---

### Post by jakupl on 2008-11-26
thanks it worked now. but when I now log in, i first get an error message saying:

User's $HOME/.dmrc file is being ignored. this prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

then I click okay and get another error message saying:

Could not update ICEauthority file /home/jakup/.ICEauthority

then I click Close and my desktop and everything appears, just like normal, until I get another error message saying:

An error occurred while loading or saving information for Power Manager. Some of your configuration settings may not work properly.

And then everything seems at though it is working... Any suggestions? any help is appreciated.
EDIT: no it does not seem as everything is working... I can't write to my home folder, only read.

---

### Post by jakupl on 2008-11-26
It seems as though I am not the owner of the files in my home folder, even though it says i am.

---

### Post by caljohnsmith on 2008-11-26
OK, sounds like a permissions problem; while you are in Ubuntu, how about posting:
```
mount
ls -al / /home /home/jakup
```
And we can go from there.

---

### Post by jakupl on 2008-11-26
> **caljohnsmith said:**
> OK, sounds like a permissions problem; while you are in Ubuntu, how about posting:
```
mount
ls -al / /home /home/jakup
```
And we can go from there.

here you go.
```

jakup@bobby:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /home type ext3 (rw,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jakup/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jakup)

```

```
jakup@bobby:~$ ls -al / /home /home/jakup
/:
total 92
drwxr-xr-x  21 root root  4096 2008-11-26 20:33 .
drwxr-xr-x  21 root root  4096 2008-11-26 20:33 ..
drwxr-xr-x   2 root root  4096 2008-11-20 00:45 bin
drwxr-xr-x   3 root root  4096 2008-11-23 23:28 boot
lrwxrwxrwx   1 root root    11 2008-11-01 23:38 cdrom -> media/cdrom
drwxr-xr-x  15 root root 14000 2008-11-26 21:36 dev
drwxr-xr-x 137 root root 12288 2008-11-26 20:58 etc
drwxr-xr-x   4 root root  4096 2008-11-26 20:32 home
drwxr-xr-x   3 root root  4096 2008-11-25 22:53 home_backup
lrwxrwxrwx   1 root root    32 2008-11-01 23:53 initrd.img -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root  4096 2008-11-20 00:46 lib
drwx------   2 root root 16384 2008-11-01 23:38 lost+found
drwxr-xr-x   3 root root  4096 2008-11-26 20:43 media
drwxr-xr-x   2 root root  4096 2008-10-20 14:27 mnt
drwxr-xr-x   2 root root  4096 2008-10-29 23:53 opt
dr-xr-xr-x 126 root root     0 2008-11-26 20:43 proc
drwxr-xr-x  28 root root  4096 2008-11-25 21:33 root
drwxr-xr-x   2 root root  4096 2008-11-23 20:39 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 23:53 srv
drwxr-xr-x  12 root root     0 2008-11-26 20:43 sys
drwxrwxrwt  12 root root  4096 2008-11-26 21:37 tmp
drwxr-xr-x  12 root root  4096 2008-11-02 00:18 usr
drwxr-xr-x  15 root root  4096 2008-10-30 00:12 var
lrwxrwxrwx   1 root root    29 2008-11-01 23:53 vmlinuz -> boot/vmlinuz-2.6.27-7-generic

/home:
total 28
drwxr-xr-x  4 root root  4096 2008-11-26 20:32 .
drwxr-xr-x 21 root root  4096 2008-11-26 20:33 ..
drwxr-xr-x 53 root root  4096 2008-11-26 20:32 jakup
drwx------  2 root root 16384 2008-11-25 21:11 lost+found

/home/jakup:
total 1404
drwxr-xr-x 53 root  root     4096 2008-11-26 20:32 .
drwxr-xr-x  4 root  root     4096 2008-11-26 20:32 ..
-rw-------  1 jakup jakup 1041544 2008-11-26 20:32 2008-11-26-201933_1280x800_scrot.png
drwxr-xr-x  3 root  root     4096 2008-11-26 20:32 .adobe
drwxr-xr-x  4 root  root     4096 2008-11-26 20:32 andreas
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 .aptoncd
-rw-r-----  1 jakup jakup    9178 2008-11-26 21:37 .bash_history
-rw-r-----  1 jakup jakup     439 2008-11-26 20:32 .bash_history~
-rw-r--r--  1 jakup jakup     220 2008-11-26 20:32 .bash_logout
-rw-r--r--  1 jakup jakup    3115 2008-11-26 20:32 .bashrc
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 .bogofilter
drwxr-xr-x  7 root  root     4096 2008-11-26 20:32 .cache
drwxr-xr-x 12 root  root     4096 2008-11-26 20:32 .config
drwxr-xr-x  3 root  root     4096 2008-11-26 20:32 .dbus
drwxr-xr-x  2 root  root     4096 2008-11-26 20:32 Desktop
-rw-------  1 jakup jakup      28 2008-11-26 20:32 .dmrc
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 Documents
-rw-r-----  1 jakup jakup      16 2008-11-26 20:32 .esd_auth
drwxr-xr-x  8 root  root     4096 2008-11-26 20:32 .evolution
lrwxrwxrwx  1 jakup jakup      26 2008-11-26 20:32 Examples -> /usr/share/example-content
drwxr-xr-x  2 root  root     4096 2008-11-26 20:32 .fontconfig
drwxr-xr-x  5 root  root     4096 2008-11-26 20:32 .gconf
drwxr-xr-x  2 root  root     4096 2008-11-26 20:32 .gconfd
drwxr-xr-x  4 root  root     4096 2008-11-26 20:32 .gegl-0.0
drwxr-xr-x 22 root  root     4096 2008-11-26 20:32 .gimp-2.6
-rw-r-----  1 jakup jakup       0 2008-11-26 21:10 .gksu.lock
drwxr-xr-x 14 root  root     4096 2008-11-26 20:32 .gnome2
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 .gnome2_private
drwxr-xr-x  2 root  root     4096 2008-11-26 20:32 .gnupg
drwxr-xr-x  2 root  root     4096 2008-11-26 20:32 .gpass
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 .gpilotd
-rw-r--r--  1 jakup jakup       4 2008-11-26 20:32 .gpilotd.pid
drwxr-xr-x  2 root  root     4096 2008-11-26 20:32 .gstreamer-0.10
-rw-------  1 jakup jakup     108 2008-11-26 20:55 .gtk-bookmarks
-rw-r--r--  1 jakup jakup   29662 2008-11-26 20:32 gtkorphan_0.4.2-2_all.deb
dr-x------  2 jakup jakup       0 2008-11-26 20:51 .gvfs
-rw-r--r--  1 jakup jakup     561 2008-11-26 20:32 .htoprc
-rw-------  1 jakup jakup    5753 2008-11-26 20:32 .ICEauthority
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 .icons
-rw-r--r--  1 jakup jakup     230 2008-11-26 20:32 intrepid.list
drwxr-xr-x  3 root  root     4096 2008-11-26 20:32 .kde
drwxr-xr-x  2 root  root     4096 2008-11-26 20:32 .keepassx
drwxr-xr-x  3 root  root     4096 2008-11-26 20:32 .local
drwxr-xr-x  3 root  root     4096 2008-11-26 20:32 .macromedia
drwxr-xr-x  3 root  root     4096 2008-11-26 20:32 .mcop
-rw-r-----  1 jakup jakup      31 2008-11-26 20:32 .mcoprc
drwxr-xr-x  4 root  root     4096 2008-11-26 20:32 .mozilla
drwxr-xr-x  3 root  root     4096 2008-11-26 20:32 .mozilla-thunderbird
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 Music
drwxr-xr-x  3 root  root     4096 2008-11-26 20:32 .nautilus
drwxr-xr-x  4 root  root     4096 2008-11-26 20:32 Nótar
drwxr-xr-x  3 root  root     4096 2008-11-26 20:32 .openoffice.org2
drwxr-xr-x 12 root  root     4096 2008-11-26 20:32 Pictures
-rw-r--r--  1 jakup jakup     675 2008-11-26 20:32 .profile
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 Public
drwxr-xr-x  2 root  root     4096 2008-11-26 20:32 .pulse
-rw-r-----  1 jakup jakup     256 2008-11-26 20:32 .pulse-cookie
drwxr-xr-x  2 root  root     4096 2008-11-26 20:32 .qt
-rw-r-----  1 jakup jakup     860 2008-11-26 20:32 .recently-used
-rw-------  1 jakup jakup   47673 2008-11-26 20:32 .recently-used.xbel
-rwxr-xr-x  1 jakup jakup      81 2008-11-26 20:32 .Sikra Lortid
-rw-r--r--  1 jakup jakup      89 2008-11-26 20:32 .Sikra Lortid~
drwxr-xr-x  4 root  root     4096 2008-11-26 20:32 .Skype
drwxr-xr-x  3 root  root     4096 2008-11-26 20:32 .sok
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 .ssh
-rw-r--r--  1 jakup jakup       0 2008-11-26 20:32 .sudo_as_admin_successful
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 Templates
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 .themes
drwxr-xr-x  5 root  root     4096 2008-11-26 20:32 .thumbnails
drwxr-xr-x  2 root  root     4096 2008-11-26 20:32 .TrueCrypt
drwxr-xr-x  4 root  root     4096 2008-11-26 20:32 .ubuntu-tweak
drwxr-xr-x  2 root  root     4096 2008-11-26 20:32 .update-manager-core
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 .update-notifier
-rw-r--r--  1 jakup jakup    1763 2008-11-26 20:32 .usb-creator.log
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 Videos
drwxr-xr-x  2 jakup jakup    4096 2008-11-26 20:32 .wapi
-rw-r--r--  1 jakup jakup     732 2008-11-26 20:32 wfwf.kdb
-rw-r--r--  1 jakup jakup    2084 2008-11-26 20:32 .xsession-errors
drwxr-xr-x  2 root  root     4096 2008-11-26 20:32 Ymiskt

```

---

### Post by caljohnsmith on 2008-11-26
OK, how about:
```
sudo chown -R jakup:jakup /home/jakup
```
Then reboot, and let me know what happens. :)

---

### Post by jakupl on 2008-11-26
I got:

```
jakup@bobby:~$ sudo chown -R jakup:jakup /home/jakup
[sudo] password for jakup: 
chown: cannot access `/home/jakup/.gvfs': Permission denied
```

EDIT: I just tried it again with the verbose flag, looks good. I will reboot.

---

### Post by jakupl on 2008-11-26
YEEY it works! Finally a Seperate home partition. NICE.

why is it only possible to press the thanks button once? ;)

Thank you very much.

---

### Post by caljohnsmith on 2008-11-26
You're certainly welcome, I'm glad your /home directory is working now. I'm wondering how some of the permissions on files/directories in your home directory were changed to root though, because not all of them were. You might want to look in your /home_backup/jakup folder and see if your original home directory had all the permissions OK. Anyway, cheers and have fun with Ubuntu. :)

---

### Post by jakupl on 2008-11-27
> **caljohnsmith said:**
> You're certainly welcome, I'm glad your /home directory is working now. I'm wondering how some of the permissions on files/directories in your home directory were changed to root though, because not all of them were. You might want to look in your /home_backup/jakup folder and see if your original home directory had all the permissions OK. Anyway, cheers and have fun with Ubuntu. :)

well, It seems as though I had the same problem half a year ago. [here is the thread.]("http://ubuntuforums.org/showthread.php?t=805642")

---

