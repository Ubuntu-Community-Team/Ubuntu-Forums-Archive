---
title: "Backup tar xvpfz backup.tgz -C / Permission Denied"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by ProgressionMurph on 2009-05-01
Hello Everyone,

I'm trying to backup my root.

I have backup.tgz in my root and I type tar xvpfz backup.tgz -C / in and I receive the following errors.

tar:backup.tgz: Cannot open: Permission denied
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Feeling lost.

Thanks.

---

### Post by taurus on 2009-05-01
Did you log in as root (not the first user that you created during the installing process)?  Otherwise, add the **sudo** in front for root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ProgressionMurph on 2009-05-01
root@alex-laptop:/home/alex# tar xvpfz backup.tgz -C /
tar: backup.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting nowdo.
tar: Child returned status 2t to 
tar: Error exit delayed from previous errors

[LEFT]No longer recieve the permission error.  Hmm.. Well.. the file is in the root area.  I don't have much knowledge with linux.  Unless I made the root backup wrong.  I don't know wha
[/LEFT]

---

### Post by taurus on 2009-05-01
Are you in the right directory where backup.tgz resided?  Remember, you are in /home/alex's home directory.

```
ls -la
```

---

### Post by ProgressionMurph on 2009-05-01
root@alex-laptop:/home/alex# ls -la
ls: cannot access .gvfs: Permission denied
total 156
drwxr-xr-x 26 alex alex 4096 2009-05-01 19:07 .
drwxr-xr-x  4 root root 4096 2009-05-01 13:47 ..
-rw-------  1 alex alex   59 2009-05-01 19:07 .bash_history
-rw-r--r--  1 alex alex  220 2009-05-01 13:47 .bash_logout
-rw-r--r--  1 alex alex 3115 2009-05-01 13:47 .bashrc
drwx------  3 alex alex 4096 2009-05-01 09:57 .cache
drwxr-xr-x  4 alex alex 4096 2009-05-01 09:57 .config
drwx------  3 alex alex 4096 2009-05-01 09:57 .dbus
drwxr-xr-x  2 alex alex 4096 2009-05-01 10:12 Desktop
-rw-------  1 alex alex   28 2009-05-01 09:57 .dmrc
drwxr-xr-x  2 alex alex 4096 2009-05-01 09:57 Documents
-rw-------  1 alex alex   16 2009-05-01 09:57 .esd_auth
-rwx------  1 alex alex  357 2009-04-27 07:12 examples.desktop
drwxr-xr-x  2 alex alex 4096 2009-05-01 09:57 .fontconfig
drwx------  5 alex alex 4096 2009-05-01 10:25 .gconf
drwx------  2 alex alex 4096 2009-05-01 19:18 .gconfd
drwx------  8 alex alex 4096 2009-05-01 10:08 .gnome2
drwx------  2 alex alex 4096 2009-05-01 09:57 .gnome2_private
drwx------  2 alex alex 4096 2009-05-01 09:57 .gnupg
drwxr-xr-x  2 alex alex 4096 2009-05-01 09:57 .gstreamer-0.10
-rw-r--r--  1 alex alex  104 2009-05-01 09:58 .gtk-bookmarks
d?????????  ? ?    ?       ?                ? .gvfs
-rw-------  1 alex alex  169 2009-05-01 09:57 .ICEauthority
drwx------  3 alex alex 4096 2009-05-01 10:12 .local
drwx------  4 alex alex 4096 2009-05-01 19:07 .mozilla
drwxr-xr-x  2 alex alex 4096 2009-05-01 09:57 Music
drwxr-xr-x  3 alex alex 4096 2009-05-01 09:57 .nautilus
drwxr-xr-x  2 alex alex 4096 2009-05-01 09:59 Pictures
-rw-r--r--  1 alex alex  675 2009-05-01 13:47 .profile
drwxr-xr-x  2 alex alex 4096 2009-05-01 09:57 Public
drwx------  2 alex alex 4096 2009-05-01 09:57 .pulse
-rw-------  1 alex alex  256 2009-05-01 09:57 .pulse-cookie
-rw-------  1 alex alex  218 2009-05-01 10:08 .recently-used.xbel
-rw-r--r--  1 alex alex    0 2009-05-01 10:00 .sudo_as_admin_successful
drwxr-xr-x  2 alex alex 4096 2009-05-01 09:57 Templates
drwx------  3 alex alex 4096 2009-05-01 09:59 .thumbnails
drwx------  2 alex alex 4096 2009-05-01 09:57 .update-notifier
drwxr-xr-x  2 alex alex 4096 2009-05-01 09:57 Videos
-rw-------  1 alex alex  122 2009-05-01 09:57 .Xauthority
-rw-r--r--  1 alex alex 5777 2009-05-01 19:19 .xsession-errors


How do you make the code?

---

### Post by taurus on 2009-05-01
I don't see any backup.tgz from the output!  Where did you put backup.tgz?

```
find / -name backup.tgz -print
```

---

### Post by ProgressionMurph on 2009-05-01
Places>My Computer> File System (root) as far as I can tell it has a "/"

---

### Post by ProgressionMurph on 2009-05-01
inside their there is a "root" folder.

---

### Post by taurus on 2009-05-01
You mean /root!

```
ls -la /root
```
p.s.  /root is not the same as /home/alex.

---

### Post by ProgressionMurph on 2009-05-01
root@alex-laptop:/home/alex# find / -name backup.tgz -print
/media/MY IPOD/backup.tgz
/home/alex/.local/share/Trash/files/backup.tgz
/backup.tgz

---

### Post by taurus on 2009-05-01
> **ProgressionMurph said:**
> root@alex-laptop:/home/alex# find / -name backup.tgz -print
/media/MY IPOD/backup.tgz
/home/alex/.local/share/Trash/files/backup.tgz
**[COLOR="Blue"]/backup.tgz[/COLOR]**

```
cd /
tar xvpfz backup.tgz **-C /**
```

Or you can omit the **-C /** at the end since you are already in /.

---

### Post by ProgressionMurph on 2009-05-01
HooHa!!! typed that into the terminal and it seems to be unpacking the backup!

---

### Post by ProgressionMurph on 2009-05-01
Hmm.. This is what I get..

tar: Skipping to next header

gzip: stdin: invalid compressed data--format violated
tar: Child returned status 1
tar: Error exit delayed from previous errors

by the end.

---

### Post by taurus on 2009-05-01
Sounds like there is something wrong with backup.tgz.

---

