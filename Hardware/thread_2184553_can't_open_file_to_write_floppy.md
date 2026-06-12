---
title: "can't open file to write floppy"
date: 2013-10-29
forum: Hardware
---

### Post by jdb70 on 2013-10-29
I have been trying to write to a floppy in lubunut but when I try to (replace file) it comes up "Can't open file to write".  So what do I need to do?

---

### Post by Bashing-om on 2013-10-29
jdb70; Hi ! Welcome to the forum.

Maybe a security issue with the file in question ? .. 
a) Who owns that /directory/file ? as only the owner or sudo can access it unless permission is granted explicitly with the file permissions,
b) Can you write to the file if you have the elevated privileges of "sudo" ?

As a new user, do you need guidance in understanding the model ? 

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by Dennis N on 2013-10-29
Did you check the position of the write protect tab on the disk?

---

### Post by jdb70 on 2013-10-30
Yes I checked that.

---

### Post by jdb70 on 2013-10-30
I thought I replied to this but it didn't take.

The floppy disk is moved from a CNC machine to the computer and back.  This is the only way we have to transfer data from one to the other.  We can write or edit with the CNC machine but it is quicker to do it on the computer and transfer it to the CNC.  But some of the files are edited on the CNC so I don't know who the owner of the files would be.

I have set the user of the computer as the administrator.  I know that is not a good thing to do.  I would have thought that would give complete rights to writing.

I do need guidance on how to set sudo.  I have used Linux before but am very limited on command line.

---

### Post by jdb70 on 2013-10-30
I did a test:
I formatted a floppy and then created a file in leafpad and tried to save it on the new formatted floppy.  It came up with the same message "Can't open file to write floppy".  I also noticed that if I change anything in using the GUI it does not save it.  It looks like it does.  There is only one user for this computer so how do I make that user the power user or administrator?

---

### Post by Bashing-om on 2013-10-30
jdb70; Well,

Let's look and see if you are in the "floppy" group.
Post back the output of terminal code:
```

groups

```Which will show what devices you have access to.

[INDENT][INDENT]there is a reason, (??)
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-10-30
OK, groups gave me this:

root  adm  dialout  fax  cdrom  floppy  tape  sudo  audio  dip  video  plugdev  fuse  netdev  lpadmin  sambashare

---

### Post by Bashing-om on 2013-10-30
jdb70; Well, well.

That output says you have access to floppy !... So how is the floppy mounted ?
Insert a disk into the floppy drive and post back the output of;
Terminal code:
```

mount
ls -la /media
ls -la /media/<your-user-name>

```

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-10-30
This is the resaults

rich@Shop:~$ ls -la /media
total 16
drwxr-xr-x   4 root root 4096 Oct 30 09:50 .
drwxr-xr-x  22 root root 4096 Oct 28 13:50 ..
lrwxrwxrwx   1 root root    7 Oct 28 13:33 floppy -> floppy0
drwxr-xr-x   2 root root 4096 Oct 28 13:33 floppy0
drwxr-x---+  2 root root 4096 Oct 30 17:35 rich
rich@Shop:~$ ls -la /media/rich
total 8
drwxr-x---+ 2 root root 4096 Oct 30 17:35 .
drwxr-xr-x  4 root root 4096 Oct 30 09:50 ..

---

### Post by Bashing-om on 2013-10-30
jdb70;

I think I see it !
> 
drwxr-xr-x 2 root root 4096 Oct 28 13:33 floppy0

Says the directory is owned by "root" and only "root" has read and write access to it.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
You as "rich" -your normal user - may gain access by changing the ownership of that directory and it's contents by terminal command:
```

sudo chown -R rich:rich /media/floppy

```
Where "rich" is your normal login username.
see the manual pages for details:
```

man chown
man chmod
man chgrp

```

Can "you" now copy a file to the floppy and also copy from the floppy ?


[INDENT][INDENT]I see, said the blind man
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-10-31
I did what you instructed me to do and still no go.  I have formated with this drive so I know that it is working.  Should I try a different distro?

---

### Post by Bashing-om on 2013-10-31
jdb70; Surprised !

As to another distro, nope; all share the same kernel and as such that problem would have to be resolved in any distro that you install.

Let's see if the "chown" reverted back to root. Show :
```

ls -la /media

```
Then we will go back to poke'n see if this is hardware related, or a lack of communications.

[INDENT][INDENT]we keep try'n
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-10-31
Can you list out the exact steps / software / terminal commands you are using? it's a long time since I've used floppies under *nix but the "Can't open file to write floppy" message doesn't ring bells (*nix write errors are usually something terse like "Permission denied") so I wonder if it's a particular proprietary application that's misbehaving?

---

### Post by jdb70 on 2013-10-31
rich@Shop:~$ ls -la /media
total 16
drwxr-xr-x   4 root root 4096 Oct 30 09:50 .
drwxr-xr-x  22 root root 4096 Oct 28 13:50 ..
lrwxrwxrwx   1 rich rich    7 Oct 28 13:33 floppy -> floppy0
drwxr-xr-x   2 root root 4096 Oct 28 13:33 floppy0
drwxr-x---+  2 root root 4096 Oct 31 13:34 rich


The steps I use is:
insert the floppy into drive
open Leafpad and create a doc
click on save and it opens a window "Save As"
I click on dirve "Floppy" and title the test
I click save
That is when it comes up with the message "Can't open file to write floppy"

---

### Post by Bashing-om on 2013-10-31
jdb70; Hey,

As reference, by output of a USB thumb drive:
> 
sysop@1304mini:~$ ls -la /media
total 12
drwxr-xr-x   3 root root 4096 May 19 13:30 .
drwxr-xr-x  23 root root 4096 Oct 26 23:14 ..
drwxr-x---+  3 root root 4096 Oct 31 12:31 sysop
sysop@1304mini:~$ ls -la /media/sysop
total 24
drwxr-x---+ 3 root  root   4096 Oct 31 12:31 .
drwxr-xr-x  3 root  root   4096 May 19 13:30 ..
[color=red]drwx------  8 sysop sysop 16384 Dec 31  1969 8023-774F[/color]
where "sysop" is my user name. The permission fields show only me (sysop) has access to this USB device.
Note in your output that "floppy0" is still owned by root, and not you.
So the question is, how is the floppy drive mounted ?

With a disk inserted into the floppy drive;
show:
```

ls -la /media/floppy0
ls -la /media/rich

```

Indications are so far still but a permission/access issue.

[INDENT][INDENT]gots to be a reason
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-10-31
rich@Shop:~$ ls -la /media/floppy0
total 8
drwxr-xr-x 2 root root 4096 Oct 28 13:33 .
drwxr-xr-x 4 root root 4096 Oct 30 09:50 ..
rich@Shop:~$ ls -la /media/rich
total 8
drwxr-x---+ 2 root root 4096 Oct 31 13:34 .
drwxr-xr-x  4 root root 4096 Oct 30 09:50 ..
rich@Shop:~$ ls -la /media/floppy0
total 8
drwxr-xr-x 2 root root 4096 Oct 28 13:33 .
drwxr-xr-x 4 root root 4096 Oct 30 09:50 ..
rich@Shop:~$ ls -la /media/rich
total 15
drwxr-x---+ 3 root root 4096 Oct 31 14:50 .
drwxr-xr-x  4 root root 4096 Oct 30 09:50 ..
drwxr-xr-x  2 root root 7168 Dec 31  1969 disk

The first two I just put the floppy in and in teminal put what you said to do.  The second two I opened file manager and clicked on the floppy drive to mount and then in terminal inputed again.

---

### Post by Bashing-om on 2013-10-31
jdb70; Well, well ....

Nowhere do I see that anyone but "root" has access rights.
So back to how is that floppy disk mounted ? 

I have no experience with a floppy drive, so we be hunting. Let's see if we can find the process that controls mounting the floppy.
Hopefully it is "udev".
With a floppy inserted and the floppy drive mounted from the file manager, what returns from:
```

mount
cat /etc/fstab
cat /etc/mtab
ls -la /dev/flopp*

```

sometimes I wonder
[INDENT][INDENT]other times, I just do not know
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-10-31
rich@Shop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=e15e0529-c9be-4ee7-877c-76cefd4c4b05 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7893b1b3-125d-4a2a-8da4-c82970a96146 none            swap    sw              0       0


rich@Shop:~$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
none /sys/fs/pstore pstore rw 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=rich 0 0
/dev/fd0 /media/rich/disk vfat rw,nosuid,nodev,uhelper=udisks2 0 0

rich@Shop:~$ ls -la /dev/floppy
ls: cannot access /dev/floppy: No such file or directory

---

### Post by Bashing-om on 2013-10-31
jdb70; A little farther along,

I have been looking about, and older docs have the floppy disk mounted from /etc/fstab. We may try that directly ..no harm in trying !
Maybe we can impart explicit mount directives in /etc/fstab ?
For now I really want to know how that floppy drive is mounted, as it is not mounted in /etc/fstab . See if this gives us a hint:
```

ls -la /dev/fd0

```
Some old docs direct to get around a bug in mounting the floppy device to:
```

udisks --mount /dev/fd0

```
See if that command will mount the floppy rather then from the file manager. See then if "you" have access.
To safely remove the device:
```

udisks --unmount /dev/fd0

```

[INDENT]looking for options
[/INDENT]

---

### Post by jdb70 on 2013-11-01
OK Bashing-om

I tried what you said and it did the same thing.  Now I also have problems in other places like the display setting.  If I change the display setting in the GUI it changes but even if I click on Save it says it saves but when I reboot it comes back to the original settings.  Would this be of the same problem.  I know one problem at a time.

---

### Post by Dennis N on 2013-11-01
jdb70 ---

Have you considered getting a USB-connected floppy disk drive? Mine works in 13.04 and 13.10, and they are inexpensive as well.

---

### Post by jdb70 on 2013-11-01
Well Dennis, that is a thought.  We did purchase a RS-232 cable to try and connect the computer to our CNC machine.  It will not be in until Monday but if I can't get that to work we need something to fall back on so we may try the USB-connected floppy disk drive.

Even if we do get the RS-232 or the USB floppy drive I still would like to get some of the other problems worked out on this.

The problems I went through with Linux Mint and could not get it working correctly and now with Lubuntu.  I had heard several years ago that Linux will run on anything but the question is how well.

---

### Post by Bashing-om on 2013-11-01
jdb70; Morning !

Dennis knows his stuff, any advise he gives is worthy of consideration. Linux, ubuntu in particular, is one size fits all - but, sometimes the fit is not too well and we have to do a bit of tweaking. In this case we are looking at getting older hardware to integrate with newer software.
I am thinking we can do that integration of the floppy drive in /etc/fstab and come out smelling like a rose.. after "tweak'n" to set up the access and permissions as you prefer.

Permissions -> desk top; maybe a slight chance that permission issues with the desk top and the floppy drive are related. Have you been "sudo'n" where you should not have, and now permissions in your /home directory are changed ? lets look:
```

ls -la

```
And then we will come back to the consideration of mount points and adding the floppy drive to /etc/fstab.

[INDENT]ubuntu, where there is a will there is a way
[/INDENT]

---

### Post by jdb70 on 2013-11-01
rich@Shop:~$ ls -la
total 128
drwxr-xr-x 23 rich root 4096 Nov  1 08:08 .
drwxr-xr-x  3 root root 4096 Oct 28 13:48 ..
drwx------  3 rich root 4096 Oct 28 14:42 .adobe
-rw-------  1 rich root 1192 Nov  1 08:07 .bash_history
-rw-r--r--  1 rich root  220 Oct 28 13:48 .bash_logout
-rw-r--r--  1 rich root 3637 Oct 28 13:48 .bashrc
drwx------ 10 rich root 4096 Nov  1 08:08 .cache
drwx------ 22 rich root 4096 Oct 28 16:01 .config
drwxr-xr-x  2 rich root 4096 Oct 30 12:21 Desktop
-rw-r--r--  1 rich root   41 Oct 30 09:41 .dmrc
drwxr-xr-x  2 rich root 4096 Oct 30 12:11 DNC
drwxr-xr-x  2 rich root 4096 Oct 28 14:10 Documents
drwxr-xr-x  2 rich root 4096 Oct 30 12:10 Downloads
drwx------  3 rich root 4096 Nov  1 08:08 .gconf
-rw-r-----  1 rich root    0 Oct 28 14:16 .gksu.lock
drwxr--r--  2 rich root 4096 Oct 28 14:45 .hardinfo
drwx------  3 rich root 4096 Oct 28 15:49 .icons
drwx------  3 rich root 4096 Oct 28 15:49 .kde
drwxr-xr-x  3 rich root 4096 Oct 28 14:19 .local
drwx------  3 rich root 4096 Oct 28 14:42 .macromedia
drwx------  4 rich root 4096 Oct 28 14:14 .mozilla
drwxr-xr-x  2 rich root 4096 Oct 28 16:01 .mplayer
drwxr-xr-x  2 rich root 4096 Oct 28 14:10 Music
drwxr-xr-x  2 rich root 4096 Oct 28 14:10 Pictures
-rw-r--r--  1 rich root  675 Oct 28 13:48 .profile
drwxr-xr-x  2 rich root 4096 Oct 28 14:10 Public
drwxr-xr-x  2 rich root 4096 Oct 28 14:10 Templates
drwx------  4 rich root 4096 Oct 28 14:13 .thumbnails
drwxr-xr-x  2 rich root 4096 Oct 28 14:10 Videos
-rw-------  1 rich root   49 Nov  1 08:08 .Xauthority
-rw-r--r--  1 rich root   14 Apr 25  2013 .xscreensaver
-rw-------  1 rich root   73 Nov  1 08:08 .xsession-errors
-rw-------  1 rich root  134 Nov  1 08:07 .xsession-errors.old
rich@Shop:~$

---

### Post by Bashing-om on 2013-11-01
jdb70; UnGood !

This will take a bit of cogitation as to how to "properly" resolve the permissions. I am aware of some horror stories resulting from thoughtless procedures to restore those permissions.
For your reference, my output:
> 
sysop@1304mini:~$ ls -la
total 1032
drwxr-xr-x 22 sysop sysop   4096 Nov  1 10:46 .
drwxr-xr-x  4 root  root    4096 May 19 11:04 ..
drwx------  2 sysop sysop   4096 Oct 22 19:02 .aptitude
-rw-------  1 sysop sysop  48288 Nov  1 00:40 .bash_history
-rw-r--r--  1 sysop sysop    309 Jul  8 20:55 .bash_logout
-rw-r--r--  1 sysop sysop    220 May 19 11:04 .bash_logout~
-rw-r--r--  1 sysop sysop    220 Jul  8 20:50 .bash_logout-orig
-rw-r--r--  1 sysop sysop   3637 May 19 11:04 .bashrc
drwx------ 20 sysop sysop   4096 Nov  1 10:46 .cache
-rwxr-xr-x  1 sysop sysop  12010 Oct 10 18:31 cli_cmds
-rwxr-xr-x  1 sysop sysop  11771 Sep 10 12:04 cli_cmds~
drwxrwxr-x 16 sysop sysop   4096 Jul 13 14:00 .config
-rw-rw-r--  1 sysop sysop   6070 Aug  6 13:50 cron-rotatelogs
-rw-rw-r--  1 sysop sysop   5242 Aug  3 22:04 cron-rotatelogs~
drwx------  3 sysop sysop   4096 May 19 11:27 .dbus
drwxr-xr-x  2 sysop sysop   4096 May 19 11:27 Desktop
-rw-rw-r--  1 sysop sysop    192 Sep  1 20:49 device.map
drwxr-xr-x  2 sysop sysop   4096 May 19 11:27 Documents
drwxr-xr-x  2 sysop sysop   4096 Oct  7 15:33 Downloads
-rw-rw-r--  1 sysop sysop   1560 Nov  1 10:50 errors-boot.txt
drwx------  4 sysop sysop   4096 Oct 31 12:54 .gconf
-rw-r-----  1 sysop sysop      0 Sep 29 18:46 .gksu.lock
drwx------  3 sysop sysop   4096 May 19 22:57 .gnome2
drwx------  2 sysop sysop   4096 Sep  4 14:23 .gnupg
drwxrwxr-x  2 sysop sysop   4096 Aug 22 13:48 grubing
drwx------  2 sysop sysop   4096 May 19 11:27 .gvfs
-rw-------  1 sysop sysop  14018 Nov  1 10:46 .ICEauthority
-rw-------  1 sysop sysop    108 Oct  2 11:52 .lesshst
-rw-rw-r--  1 sysop sysop      0 Jul  5 00:39 libpeerconnection.log
-rw-rw-r--  1 sysop sysop  28396 Oct 11  2012 libudev0_175-0ubuntu13_amd64.deb
drwxrwxr-x  3 sysop sysop   4096 May 19 11:27 .local
-rw-rw-r--  1 sysop sysop  20880 May 26 19:44 mkconfig-output
drwxr-xr-x  2 sysop sysop   4096 May 19 11:27 Music
drwxr-xr-x  2 sysop sysop   4096 May 19 11:27 Pictures
drwx------  3 sysop sysop   4096 May 19 18:12 .pki
-rw-r--r--  1 sysop sysop    675 May 19 11:04 .profile
drwxr-xr-x  2 sysop sysop   4096 May 19 11:27 Public
-rw-rw-r--  1 sysop sysop   3434 Jun 16 23:40 stat.txt
-rw-rw-r--  1 sysop sysop   2780 Jun 15 23:55 stat.txt~
-rwxr-xr-x  1 sysop sysop   7451 Sep  6 17:54 sys-info
-rw-r--r--  1 sysop sysop   9793 Aug 17 16:27 system-processes
-rw-r--r--  1 sysop sysop   9648 Jun 12 12:09 system-processes~
drwxr-xr-x  2 sysop sysop   4096 May 19 11:27 Templates
drwxrwxr-x  3 sysop sysop   4096 May 22 11:38 .thumbnails
drwxr-xr-x  2 sysop sysop   4096 May 19 11:27 Videos
-rw-rw-r--  1 sysop sysop    463 Jul 29 00:35 www-explore
-rw-rw-r--  1 sysop sysop    462 Jul 28 19:51 www-explore~
-rwxr-xr-x  1 sysop sysop   9312 Aug 20 00:54 wwwoftused
-rwxr-xr-x  1 sysop sysop   9260 Aug 17 14:59 wwwoftused~
-rw-------  1 sysop sysop    103 Jul 10 18:37 .Xauthority
-rw-rw-r--  1 sysop sysop      0 May 20 11:29 .Xauthority-old
-rw-rw-r--  1 sysop sysop   2074 May 23 15:47 Xauthority.sh
-rw-rw-r--  1 sysop sysop   1587 May 23 12:14 Xauthority.sh~
-rw-rw-r--  1 sysop sysop   4661 May 24 00:03 xauth_stuff
-rw-rw-r--  1 sysop sysop   4661 May 23 23:39 xauth_stuff~
-rw-r--r--  1 sysop sysop 191008 Nov  1 00:40 xcopy
-rw-r--r--  1 sysop sysop 190954 Oct 31 15:30 xcopy~
-rw-r--r--  1 sysop sysop 182163 Oct  3 18:35 xcopy-safe
-rw-rw-r--  1 sysop sysop  18433 Oct 10 14:52 xfce4_cli
-rw-rw-r--  1 sysop sysop  18109 Oct  7 14:37 xfce4_cli~
-rw-rw-r--  1 sysop sysop  14735 Oct  3 16:16 xfer.txt
-rw-rw-r--  1 sysop sysop  14515 Oct  1 15:19 xfer.txt~
-rwxrwxr-x  1 sysop sysop    221 Jul  6 14:17 .xinitrc
-rwxrwxr-x  1 sysop sysop    209 Jul  6 14:09 .xinitrc~
-rwxrwxr-x  1 sysop sysop    140 May 24 19:44 .xinitrc-bac
-rwxrwxr-x  1 sysop sysop    186 Jul  6 14:06 .xinitrc-good
-rw-rw-r--  1 sysop sysop   7661 Jul  5 23:02 .xscreensaver
-rw-------  1 sysop sysop    537 May 22 19:20 .xsession-errors
sysop@1304mini:~$ 

note all files are owned by me - sysop - and all files are in my own group, less one system file (..) Be aware I am the sole user of this box.
Full  disclosure  and WarningS:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

We will have to get this situation controlled, prior to returning to the floppy disk. And when this is addressed, that may resolve the situation with the floppy disk. Hey - it could happen !

[INDENT][INDENT]think thrice, execute once
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-01
Thank you Bashing-om for your help on this

---

### Post by Bashing-om on 2013-11-01
jdb70; Not a problem. I do like puzzles.

I am actively considering a procedure. I am looking at that procedure from differing angles trying to see if there is some faults before offering my advise.
I have looked at 3 installs and all directories and files, less the one noted, are owned by  <username> and group <username>; within that /home directory.
I continue in consideration and when I am sure of a complete thought through process, I will advise it.

In the meantime I have some chores I must get done. Then I will return.

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-01
Bashing-om, this is a new install and if I need to reinstall that would be fine.

---

### Post by Bashing-om on 2013-11-01
jdb70; 

Well, I did look at what I had in mind, not good enough to insure a stable system - future wise; Recursively changing the group back to "rich" in your /home directory, not a good thing as there are files that do belong to "root" in some of the sub directories. Unless one has access to another install of the same version to compare ownership and permissions, I do not recommend a wholesale "chgrp".

Others may have better advise, if time is not a consideration one may wait and see what advise is offered. On the other hand a (RE-)install is but a matter of a few minutes.
If the problem is still extent, we can take it back up again.

I do wish I had a better solution, but in all honesty, I do not think a better one exist.

[INDENT][INDENT]the final solution ??
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-04
Thank you Bashing-om,  I just reinstalled and it did the same thing.  I will wait and see what advise is offered.

Again thanks for your help.

---

### Post by Bashing-om on 2013-11-04
jdb70; Yikes.

This surely does pique my interest.
OK, permissions: does "ls -la" show "root" as the group in your home directory ?
Else if "rich" is both the owner and the group .. ya want to try and mount that floppy drive explicitly from /etc/fstab ?
Mounting from /etc/fstab gives one direct control on access and permissions.

I will also be quite happy to entertain others thoughts on this situation and what could cause it.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-05
ls -la shows "rich rich" now.  So how do you want me to mount this floppy? Do you want me to just use the file manager?

---

### Post by Bashing-om on 2013-11-05
jdb70; Hey.

We can deal with it as the ownership/permissions look good.

Let's just go ahead and mount from "/etc/fstab"
```

sudo mkdir /media/floppy0
sudo cp /etc/fstab /etc/fstab-orig

```
Fire up the text editor, loading the fstab file:
```

gksudo gedit /etc/fstab

```
and paste this line at the bottom of the file:
```

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Also good practice to always comment why a change was made to a file.

and let's see what then happens when you try and access the floppy drive.

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-05
This is the resaults

rich@Shop:~$ sudo mkdir /media/floppy0
[sudo] password for rich: 
mkdir: cannot create directory &#8216;/media/floppy0&#8217;: File exists
rich@Shop:~$ sudo cp /etc/fstab /etc/fstab-orig
rich@Shop:~$ gksudo gedit /etc/fstab
rich@Shop:~$ 

no test editor or file come up.

---

### Post by jdb70 on 2013-11-05
This is the resaults

rich@Shop:~$ sudo mkdir /media/floppy0
[sudo] password for rich: 
mkdir: cannot create directory ‘/media/floppy0’: File exists
rich@Shop:~$ sudo cp /etc/fstab /etc/fstab-orig
rich@Shop:~$ gksudo gedit /etc/fstab
rich@Shop:~$ 

no test editor or file come up.

---

### Post by Bashing-om on 2013-11-05
jdb70; OK,

Tell me again what version of 'buntu are you using ? Maybe "gedit" is not the default text editor ?

[INDENT][INDENT]the right tool for the right job
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-05
it is Lubuntu "Light Ubuntu"

---

### Post by Bashing-om on 2013-11-05
jdb70; Yeah ,

That would explain it, default text editor is PcpacFM (sp??). Let me boot into my Lububtu install and see what it is going to take to activate that file manager in administrative mode.

[INDENT][INDENT]I'll be back
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-11-05
... Leafpad maybe... ?

---

### Post by Bashing-om on 2013-11-05
jdb70; I am back.

My Lubuntu has PCManFM as the file manager.

Admin mode;
Navigate to /etc and in to tool bar -> tools -> Open Current Folder as Root;
select the fstab file and copy as formerly directed, save the file.

```

mount -a

``` to check for errors, if any the system will advise at this point, no output is a good thing !

Now can you access that floppy drive ?

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-05
What you asked me to copy to the bottom of fstab was already there

---

### Post by Bashing-om on 2013-11-05
jdb70;

Well, that is different anyway from the 1st install that you had .. that line was not then present.
Is that current line exactly as what I had intended to be pasted ?
Back to 1st base;
Is the floppy drive enabled in bios ?, In my bios it must be enabled in 2 places, check yours.
2nd base:
```

ls -la /media/floppy0

```
3rd base:
```

cat /etc/modules

```
All good in bios - then let's see what results if we mount the floppy from terminal:
```

mount /dev/fd0

``` Note we are not specifying a file type, the fstab entry "should" take care of that.

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-05
OK, I don't know how but it saved a file on the floppy. WOW!!  But when I rebooted it came up with the same "Can't open file to write floppy".

---

### Post by jdb70 on 2013-11-05
OK, I rebooted and did the following and it worked.

rich@Shop:~$ mount -a
mount: only root can do that
rich@Shop:~$ sudo mount -a
[sudo] password for rich: 
[mntent]: warning: no final newline at the end of /etc/fstab
rich@Shop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rich@Shop:~$ mount /dev/fd0
[mntent]: warning: no final newline at the end of /etc/fstab
rich@Shop:~$ 

So the question to you is how do I get this to do it without having to go through all the steps?

---

### Post by Bashing-om on 2013-11-05
jdb70; Hey !

It is doable !

Let's take the system's advisory and repair /etc/fstab !

Add that new line (in our case a carriage return) to the final line in that file.
save the file
and 
```

sudo mount -a

```

do you now have access to the floppy drive ?

[INDENT][INDENT]light at the end of the tunnel
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-05
Sorry what line

---

### Post by Bashing-om on 2013-11-05
jdb70; well:
> 
rich@Shop:~$ mount /dev/fd0
[mntent]: warning: no final newline at the end of /etc/fstab

So once more edit the file /etc/fstab
and that last line place the cursor after the final character and do a "return" to place that newline as required.

And have the permissions changed on the mount point  for floppy0 ?
```

ls -la /media/floppy0

```
Then for the change to take affect without having to reboot:
```

sudo mount -a

```
no errors now ?

OK, now go ahead a reboot and see if you are able to access the floppy drive (??)
NO ?? Well then let's edit another file and add the floppy drive to the list.
Upon your advise of the above results we will consider editing   the /etc/modules file.

[INDENT][INDENT]gotta be a reason[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-06
OK, that didn't work.

rich@Shop:~$ ls -la /media/floppy0
total 8
drwxrwxr-x 2 root root 4096 Nov  4 10:49 .
drwxr-xr-x 3 root root 4096 Oct 16 18:51 ..
rich@Shop:~$ sudo mount -a
[sudo] password for rich: 
[mntent]: line 13 in /etc/fstab is bad
rich@Shop:~$

---

### Post by Bashing-om on 2013-11-06
jdb70; Shheessh !

Ok show me what we are working with.
Post back the output of terminal code:
```

cat -n /etc/fstab

```

will see what we can do to finger this out. (now are we not glad there was a backup of that file made, before we did the edits !)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-06
rich@Shop:~$ cat -n /etc/fstab
     1    # /etc/fstab: static file system information.
     2    #
     3    # Use 'blkid' to print the universally unique identifier for a
     4    # device; this may be used with UUID= as a more robust way to name devices
     5    # that works even if disks are added and removed. See fstab(5).
     6    #
     7    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
     8    # / was on /dev/sda1 during installation
     9    UUID=7ec6dffc-4200-449d-9820-bdcc1592b518 /               ext4    errors=remount-ro 0       1
    10    # swap was on /dev/sda5 during installation
    11    UUID=cefb93de-6e72-4f29-9144-64cebadbd65d none            swap    sw              0       0
    12    /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
    13    mount /dev/fd0
rich@Shop:~$

---

### Post by Bashing-om on 2013-11-06
jdb70; Hey;

Ok, I see said the blind man.

That line 13 is for sure invalid ! The "fstab" file is a control file and must follow a particular format, 
> 
13 mount /dev/fd0

is a bash terminal command.

Fire up the text editor - open file as Root-  once more, and carefully remove that line. Exercise care that the invisible new line control  is not removed from line 12. Save the file.

Now let's see where things stand:
```

sudo mount -a

```
No errors reported, then:

Try to copy a test file from your system as an ext4 filetype to the floppy drive, whose disk is also formatted "ext4". Test is good ?
Then try and copy that file to a different disk formatted as either fat16/32 or NTFS /// Now what results ? Tying to see if?where the mount is failing.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-07
I fomated a floppy with ext4 and tryed to save a doc and this is what came up as a 

Could not mount Floppy Disk

Error mounting system-managed device /dev/fd0: Command-line `mount "/media/floppy0"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/fd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Did I format wrong?  I used "Disk Manager"

---

### Post by jdb70 on 2013-11-07
WOW, I might just try to go back to windows.

---

### Post by jdb70 on 2013-11-07
Bashing-om,

I thank you for your help and patients on this and I still would like to get this working but it is frustrating.

Would it be best to do remote desktop or is that not a safe thing to do?

---

### Post by Bashing-om on 2013-11-07
jdb70; Morning .

I am here to help. All that is frustrating is a lack of knowledge - on both of our parts -. I have not even touched a floppy disk in more years than I care to think about. Learning how a depreciated piece of hardware is to be mounted is interesting; and we know it can be done.

We can mount that drive manually from the command line, and "automount" is in place in "/etc/fstab. It should now work.

What can you do to insure and verify a known good ext4 formatted floppy disk ?

And, back to making sure the operation is a success from terminal. mount and copy. Then isolate why the operation can not be completed auto-mounting !

I have advised earlier that we may have to edit another file to incorporate the floppy drive, presently I do not know if that will be required.

Until such time as you have a known good medium, I do not know how further to proceed.

[INDENT][INDENT]ubuntu, all in knowing how
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-07
I connected another floppy drive up to the computer the try that but it does the same thing.

---

### Post by Bashing-om on 2013-11-07
jdb70;

Good thinking on your part, but, what I was unclear about was the actual floppy disk. 
We need at this point to have a known good formatted ext4 floppy disk. As mounting the floppy drive is uncertain, then any formatting to a floppy disk in that disk drive is equally uncertain.
To format the floppy disk, one must first mount that disk drive. In reducing to simplest terms I want to use ubuntu's native file system ext4 to isolate this problem.

Proposed procedure :
With a known good floppy disk inserted into the floppy drive;
Does the system recognize the disk ?
```

ls -la /media/floppy0

```
not recognized (??) then ->
mount from the command line ->
Terminal code:
```

mount /dev/fd0

```
NO ?
Terminal code:
```

udisks --mount /dev/fd0

```
If at this last point the disk drive mounts and the floppy disk is accessible, then I know to edit a particular file, reboot and see if then /etc/fstab - that has the proper formatting and options - will automount that floppy drive when a floppy disk is inserted - like we want it to do.

Else; going to resort to the log files in an attempt to see what is going on. Reading files, though interesting, is a time consuming affair !

[INDENT][INDENT]we will keep on 'till we get it right
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-08
I have tried a couple of floppies formatting ext4 but non of them would read back.  How do I use the command line to format, maybe that will work.

---

### Post by Bashing-om on 2013-11-08
jdb70; Good Morning,

Are you trying to format a floppy disk from the same situation in that we do not know that the disk drive is properly mounted ?

Prior to formatting we must be 100% certain that the floppy drive is mounted.

What returns from terminal command;
```

lsmod | grep -i floppy

``` With a floppy disk inserted into the floppy drive. If a positive result then to format from the command line:
```

sudo mkfs.ext4 /dev/fd0

```
Will format the disk to ubunt's ext4 filesystem format.

In my researching this sloppyation, I have seen indications that the tools to cope with floppy disk may have to be installed in versions 12.04 and later .. now, not real sure about what I do not know. We will struggle through this and find out.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-08
OK I think I am giving up on this.  I don't have any permisstion to do anything on this system. Can't mount floppy correctly, can't save display and can't use serial ports.  As a new install and the only one on this system I sould have all rights.

---

### Post by jdb70 on 2013-11-08
rich@Shop:~$ lsmod | grep -i floppy
floppy                 55378  0 
rich@Shop:~$ sudo mkfs.ext4 /dev/fd0
[sudo] password for rich: 
mke2fs 1.42.8 (20-Jun-2013)

Filesystem too small for a journal
Warning: could not erase sector 2: Attempt to write block to filesystem resulted in short write
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
Stride=0 blocks, Stripe width=0 blocks
184 inodes, 1440 blocks
72 blocks (5.00%) reserved for the super user
First data block=1
Maximum filesystem blocks=1572864
1 block group
8192 blocks per group, 8192 fragments per group
184 inodes per group

Allocating group tables: done                            
Warning: could not read block 0: Attempt to read block from filesystem resulted in short read
Warning: could not erase sector 0: Attempt to write block to filesystem resulted in short write
Writing inode tables: done                            
Writing superblocks and filesystem accounting information:    
rich@Shop:~$

---

### Post by jdb70 on 2013-11-08
Can you tell me how to set my resolution of the monitor and keep it to what I set it to.  Lubuntu has a "Monitor Settings" that I can change it but when I save it it doesn't take.  When I restart it goes back to default.

---

### Post by Bashing-om on 2013-11-08
jdb70; Hey.

Mount floppy: How bout this for a thought, the ext4 file system was developed after the demise of 5 1/4 inch floppy disks, maybe that is what the errors are telling us, that ext4 can not in real actuality set up on that old hardware.
Let's try to format with the file system prevalent in the day.
```

mke2fs /dev/fd0

```

As to your problems with permissions, In ubuntu, how may viruses, trojan horses or worms have you experienced ? .. None ! Reason, the structure of the linux file system and it's requirements to authenticate. Also the requirement to "sudo" for system administration is a good thing for a number of reasons. Primarily it makes one consider what they are doing at the system level that might truly cause damage. Within your home directory elevated privileges are not needed, and in fact using them can and will cause problems. Apply elevated privileges on a need-to-know (do) basis ... sudo = Super User DO. 
And yes linux is not Windows, and does take a different mindset and a willingness to learn. There is a learning curve when one progresses beyond the point and click stage. And agreed, linux is not for everybody and there are those applications in Windows that are not replicated in ubuntu.. But if the need and/or demand is there .. that application will be available (someday).

Resolution, That one is not in my field of knowledge or interest, open an additional thread to get others attention who can assist you in that matter. Forum policy is one problem, one thread as support for the way the forum functions.
 

[INDENT][INDENT]try try and try again, sometimes
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-11
Hi Bashing-om,

I have changed things up.  I have now formated and installed Ubuntu 12.04 LS hopping that it would solve the probelm but now it that says it can not mount the floppy drive and permission can not be determined on the floppy drive.

But the display settings on this one works!

---

### Post by jdb70 on 2013-11-11
OK doing some checking and found that if in terminal if I put in

udisk --mount /dev/fd0 it mounts good and I can write to it but the probelm is in order to refresh I have to unmount and then go back into terminal and put this back in again to mount again.

Do you know what I can do to fix this?

---

### Post by Bashing-om on 2013-11-11
jdb70; Hi !

To be honest, as I have no means of testing we are at a disadvantage.

From our prior experience it seems that 5 1/4 inch floppy disk can not be formatted to ext4 (journal issues in that floppy disk can not support it (??)).
And that leads me to suspect that the mount option in /etc/fstab "auto"  may not apply. This does cause me concern in that perhaps each time a different formatted disk is to be used the mount will fail. Nor am I pleased if the "filetype' must be explicitly set in /etc/fstab. If that turns out the case, may as well mount that floppy drive from the command line each time... not at all what you desire of ubuntu. 

I have one other thing to try, leaving the mounting directive as is in /etc/fstab -> edit the file  /etc/modules.
add to the end of the list in that file:
```

floppy

```

also a lot depends on how you are connecting the disk drive to the machine:
> 
 Note that these utilities do not work for USB floppy drives, because
 these do not allow direct access to the floppy controller.

see:
```

apt-cache show fdutils

```

And in this new install, let's make sure "you" are in the floppy group:
```

groups

```

If after the edit to /etc/modules, there remains the issue.. it is back to the drawing board. I have complete confidence in ubuntu, I fully believe that there is a way if I can just get an understanding of how the system sees a floppy disk drive I will find a way to implement auto mounting from the /etc/fstab file.

I admit that presently I just do not know, and finding documentation on obsolete technology is a challenge. So long as you are hanging in there and working to a solution, so am I !

[INDENT][INDENT]ubuntu, there is a way
[/INDENT][/INDENT]

---

### Post by jdb70 on 2013-11-12
Hi Bashing-om,

It might be a typo or not thinking but it is not a the 5-1/2 but the 3-1/4 floppy.  5-1/2 is very old school.  We did have one of the, what are they 8" floppy or something like that but I don't know what happened to that.

I tried what you said to add "floppy" and then I rebooted and nothing happened.  that didn't work.

It's we can live with having to manualy mount the floppy in terminal but if there is a way to make a batch file that we can just click on an icon and it mounts it then that would be good also.

We have connected our CNC to the computer via serial and using "serial port terminal" we can move files back and forth so we maybe good.

Thank you very much for all your help and your time on this.  Do I need to mark this thread as something?

---

### Post by Bashing-om on 2013-11-12
jdb70; Hey ! That is all good news to me .

Yeah 3 1/4 standards are much better, ->

If you are satisfied with your current means to transfer data, then and only then you mark this thread as solved - 1st post -> thread tools.

Else I am more than willing to keep on at this until you are able to mount that 3 1/4 inch disk drive by auto mounting.

As a thought, if the disk drive is not a permanent attachment, might consider commenting out the fd0 line in /etc/fstab, and see if the file manager nautilus will pick it up and mount it with a right click on the drive icon. In this case as the drive is mounted manually - so to speak - that drive must be unmounted after use.
> 
in case you were not aware of this, you need to use floppies slightly differently in Linux. When you drag and drop files to the floppy file manager window, they may not be written immediately, but remain in cache memory. Therefore, before you physically remove the disc, right-click on the desktop icon (or in nautilus) to unmount it. Pending writes will then be made after which you can safely remove the disc.


Failure to properly (un-)mount a drive can and does cause all kinds of problems.


There is a lot to learn about this operating system, and I welcome any opportunity to increase my knowledge. Here again, I do not know how and what means the system would utilize to mount that disk drive under these conditions. I also am somewhat surprised that none others have chimed in on this thread with  advisements and guidance . Makes me wonder how unique of a situation this is.

Once more -> where there is a will there is a way 
[INDENT][INDENT][INDENT]it's all in knowing how
[/INDENT][/INDENT][/INDENT]

---

