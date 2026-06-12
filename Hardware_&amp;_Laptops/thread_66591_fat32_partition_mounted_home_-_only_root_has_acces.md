---
title: "fat32 partition mounted /home - only root has access"
date: 2005-09-17
forum: Hardware &amp; Laptops
---

### Post by vladypus on 2005-09-17
Hi, I just installed ubuntu on my Dell Latitude C840 laptop. I am attempting to set up dual boot winXP and ubuntu. My laptop has a 40GB hd which I partitioned as follows:

7.5GB NTFS primary
24GB Ext3 primary   /
7GB Fat32 logical    /home
1.5GB Swap

During the installation I had problems creating users, and in the end only had a root account. I logged into recovery mode and attempted to use adduser to create an additional account. This failed:
chown 1001:1001 /home/username: Operation not permitted

I manually added a /home/username directory from the root. then adduser worked. 

When I tried to log into the desktop with that account, it gave me a message that said my session was under 10 seconds and gave the following error:
"Could not set mode 0700 on private per-user gnome configuration directory `/home/username/.gnome2_private/': Operation not permitted"

I logged back into recovery mode and attempted to chown the directory to the new useraccount and I got the same chown Operation not permitted error. 

I read on the forum ([http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)) about adding a line like: "/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0" to /etc/fstab.

When I looked at fstab, there was already a comparable line there (except instead of the iocharset stuff it said 'defaults'). I replaced it anyway but nothing changed.

So for some reason only root has access to the /home. Does anyone know why this might be, or how to fix it?

Also, is my partitioning scheme generally a bad idea? I wanted to have a fairly large space that both OSes could r/w.

---

### Post by tonym on 2005-09-18
Your problem is that FAT does not support different user names.  Thus anything trying to do a chown will fail  -  eg creating the home directory for a new user.  The followinf ref contrains some info on this but I'm sure you can find lots more via Google.

[http://electron.mit.edu/~gsteele/linuxfaq/](http://electron.mit.edu/~gsteele/linuxfaq/)

Regards

Tony

---

### Post by lol on 2005-09-18
Any user can read/write a FAT partition if you add umask=000 in the options when mounting the partition, but... DO NOT use a FAT32 partition for /home!!!!!!

No matter what (even if it could work), this isn't a good idea. But nothing prevents you to mount a FAT32 partition on a sub folder in your home, or to create a symlink to have an easy access to a shared drive.

---

### Post by vladypus on 2005-09-18
fixed, thanks alot. made the fat partition a subdirectory in /home

---

