---
title: "Root can't read users home folder"
date: 2008-08-25
forum: General Help
---

### Post by flick152 on 2008-08-25
This is a frustrating and bizarre little problem which I'll list the symptoms of.
[LIST]
[*]My home folder (/home/david) contents cannot be read by root in nautilus or any open file dialogs (either launched via sudo or logged in as root)
[*]Root can see files in other users homes in nautilus
[*]Root can read my home folder contents in a terminal
[*]Root can not see files owned by root in my home folder
[*]Root can see files owned by david with 600 permissions in other folders
[*]Root can see contents of subfolders like /home/david/.wine
[*]Root can create a folder or file but on refreshing nautilus it can no longer be read (The folder/file does still exist belonging to root)
[/LIST]
chmod 777 the folder had no effect

Any help would be greatly appriciated

---

### Post by prince_niceguy on 2008-08-25
Open a command line terminal and do a ls -la. If there is problem with the directory there would be ???? in front of the permission of the directory.

If that is the case, do a fsck /dev/sda[x] where x is the partition on which your home directories are mounted.

---

### Post by flick152 on 2008-08-30
Thanks outputs....

fsck:

```
ubuntu@ubuntu:~$ sudo fsck /dev/hda3 -V
fsck 1.40.8 (13-Mar-2008)
[/sbin/fsck.ext3 (1) -- /dev/hda3] fsck.ext3 /dev/hda3 
e2fsck 1.40.8 (13-Mar-2008)
/dev/hda3: clean, 228966/14429664 files, 11806819/28780447 blocks
```

ls -la:
(from live cd user 1000 is david 1001 is fred these permissions are the same as my installed ubuntu)
```

ubuntu@ubuntu:/media/hdd/home$ ls -la
total 20
drwxr-xr-x  5 root     root  4096 2008-08-25 09:53 .
drwxr-xr-x 22 root     root  4096 2008-08-25 21:43 ..
drwxrwxr-x 78     1000  1000 4096 2008-08-30 08:13 david
lrwxrwxrwx  1 root     root    44 2008-06-08 08:49 .directory -> /etc/kubuntu-default-settings/directory-home
drwxr-xr-x 29     1001 users 4096 2008-08-14 04:48 fred
drwxr-xr-x 11 www-data users 4096 2007-09-20 06:23 torrentflux

```

Still can't access david from root gui apps

---

### Post by drs305 on 2008-08-30
Graphical apps should be run with 'gksudo', so:
```
gksu nautilus /home/david
```
or
```
gksu nautilus /media/hdd/home$/david
```

You don't see anything?

---

### Post by flick152 on 2008-08-30
Nothing appears in nautilus or any other gui application (such as open file dialogs)

here's what terminal output shows it doesn't change if I navigate away and back to /home/david

```
david@Penfold:~$ gksu nautilus /home/david/

Initializing nautilus-share extension



** (nautilus:6983): WARNING **: Unable to add monitor: Operation not supported

SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS




```

/media/hdd/ was my hd mounted in live cd environment

---

### Post by flick152 on 2008-08-30
more clues

Logged into KDE dolphin has no issues reading /home/david
Back into gnome gksu dolphin can read /home/david

nautilus still can't read /home/david/ neither can open file dialogs

---

### Post by drs305 on 2008-08-30
My guess is that nautilus got messed up when run with sudo. Other than reinstalling nautilus I'll have to leave this one to others...

---

### Post by flick152 on 2008-08-30
Reinstalled nautilus. rebooted

still can't read /home/david

---

### Post by flick152 on 2009-02-10
Oddness gone.

I did a windows fix, wiped and reinstalled




(reinstalled ubuntu)

---

