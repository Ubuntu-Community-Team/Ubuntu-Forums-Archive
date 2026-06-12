---
title: "passwd Problem"
date: 2008-11-02
forum: General Help
---

### Post by Chebyshev on 2008-11-02
I just upgraded to 8.10 2 days ago and it was working fine. Just now, I tried to get samba working properly again and something got screwy with my user account. Trying to change my password using passwd produces a segfault. If I boot into recovery mode, the same thing happens. I can make a new account and change its password just fine.

When I try to log on in gdm, it seems to crash and restart itself. If I try to log on from the console, it just doesn't log me on and re-presents the logon prompt with no information. The same thing happens if I try to log on as root (I made a root password in recovery mode). If I boot to recovery mode and su to my username, it works fine.

I tried deleting my user account and re-adding it, but passwd still fails for that account name.

Any ideas?

---

### Post by Chebyshev on 2008-11-02
After more fooling around, I've found the following:

A regular boot doesn't allow any user to log on, including root. The logon fails with no message and if using gdm, it crashes and restarts itself.

A recovery mode boot allows me to log on a root and su to whatever user I want. If I try to do anything using passwd on my original username, passwd segfaults, but it works on any other username, including root.

I'm completely mystified.

---

### Post by taurus on 2008-11-02
At the gdm login screen, press <Ctrl><Alt>F2 and see if you can log in with your username and password.

---

### Post by Chebyshev on 2008-11-02
I've tried that and the logon simply fails with no explanation and the prompt is re-presented. Like so:
```
Ubuntu 8.10 rocky tty1

rocky login: ed
password:

Ubuntu 8.10 rocky tty1

rocky login:
```

---

### Post by taurus on 2008-11-02
Boot into recovery mode from GRUB menu and post the outputs of these commands here.

```
grep ed /etc/passwd
df -h
```

---

### Post by Chebyshev on 2008-11-02
```

> grep ed /etc/passwd
ed:x:1001:1001:,,,:/home/ed:/bin/bash
> df -h
Filesystem   Size    Used  Avail  Use%  Mounted on
/dev/sda1    461G    47G   396G   11&   /
tmpfs        1013M   0     1013M  0%    /lib/init/rw
varrun       1013M   16K   1013M  1%    /var/run
varlock      1013M   0     1013M  0%    /var/lock
udev         1013M   2.7M  1010M  1%    /dev
tmpfs        1013M   0     1013M  0%    /dev/shm
lrm          1013M   2.0M  1011M  1%    /lib/modules/2.6.27-7-generic/volatile

```

---

### Post by taurus on 2008-11-02
What about

```
ls -la /home/ed
```
Don't include files/directories in the output here if you don't want people to see/know.

---

### Post by Chebyshev on 2008-11-02
```
total 540
drwxr-xr-x 65 ed   ed     4096 Nov  2 18:47 .
drwxr-xr-x  3 root root   4096 Nov  2 19:21 ..
-rw-------  1 ed   ed     1576 Nov  2 09:57 .ICEauthority
drwx------  3 ed   ed     4096 Apr 26  2008 .adobe
drwxr-xr-x  4 ed   ed     4096 Aug 29 17:11 .audacity-data
drwxr-xr-x  2 ed   ed     4096 Aug 29 17:11 .audacity1.3-eddie
-rw-------  1 ed   ed     7294 Nov  2 18:49 .bash_history
-rw-r--r--  1 ed   ed      220 Apr 26  2008 .bash_logout
-rw-r--r--  1 ed   ed     2928 Apr 26  2008 .bashrc
drwx------  2 ed   ed     4096 Jul 29 20:55 .bogofilter
drwxr-xr-x  6 ed   ed     4096 Aug 29 18:46 .cache
drwx------  3 ed   ed     4096 Apr 26  2008 .compiz
drwxr-xr-x 18 ed   ed     4096 Nov  2 17:51 .config
-rw-------  1 ed   ed        0 Jul 15 16:49 .cvspass
drwxr-xr-x  3 ed   ed     4096 Oct  8 20:57 .cxchromium
drwx------  3 ed   ed     4096 Jul 15 17:39 .dbus
-rw-------  1 ed   ed       26 Nov  2 09:57 .dmrc
drwxr-xr-x  3 ed   ed     4096 Jul 15 17:39 .e
drwxr-xr-x  4 ed   ed     4096 Jul 15 16:53 .e17_cvs
drwxr-x---  2 ed   ed     4096 Aug  6 23:15 .easytag
drwxr-xr-x  4 ed   ed     4096 Apr 27  2008 .emerald
-rw-------  1 ed   ed       16 Apr 26  2008 .esd_auth
drwxr-xr-x  8 ed   ed     4096 Oct 31 20:30 .evolution
drwxr-xr-x  7 ed   ed     4096 Nov  2 18:13 .exaile
drwxr-xr-x  5 ed   ed     4096 Jul 30 17:14 .fluxbox
drwxr-xr-x  2 ed   ed     4096 Aug 13 19:42 .fontconfig
drwxr-xr-x  2 ed   ed     4096 Aug 13 19:42 .fonts
drwx------  6 ed   ed     4096 Nov  2 09:57 .gconf
drwx------  2 ed   ed     4096 Nov  2 18:13 .gconfd
drwx------  3 ed   ed     4096 Apr 27  2008 .gftp
drwxr-xr-x 22 ed   ed     4096 Oct 13 06:46 .gimp-2.4
drwx------ 18 ed   ed     4096 Nov  2 18:05 .gnome2
drwx------  2 ed   ed     4096 Apr 26  2008 .gnome2_private
drwx------  2 ed   ed     4096 Oct 30 23:44 .gnupg
drwxr-xr-x  2 ed   ed     4096 Oct 31 20:32 .gstreamer-0.10
-rw-r--r--  1 ed   ed      136 Nov  2 10:11 .gtk-bookmarks
drwx------  2 ed   ed     4096 Apr 26  2008 .gvfs
drwxr-xr-x  4 ed   ed     4096 Apr 27  2008 .icons
drwxr-xr-x  3 ed   ed     4096 Apr 26  2008 .local
drwx------  3 ed   ed     4096 Apr 26  2008 .macromedia
drwx------  3 ed   ed     4096 Apr 26  2008 .metacity
drwx------  4 ed   ed     4096 Apr 26  2008 .mozilla
drwxr-xr-x  3 ed   ed     4096 Nov  2 09:55 .nautilus
drwx------  3 ed   ed     4096 Oct 23 06:39 .openoffice.org2
-rw-r--r--  1 ed   ed      586 Apr 26  2008 .profile
drwxr-xr-x  2 ed   ed     4096 Apr 27  2008 .pulse
-rw-------  1 ed   ed      256 Apr 26  2008 .pulse-cookie
drwx------  6 ed   ed     4096 Oct 31 17:33 .purple
drwxr-xr-x  3 ed   ed     4096 Jul 23 17:25 .quodlibet
-rw-------  1 ed   ed     9438 Oct 22 23:06 .recently-used
-rw-------  1 ed   ed    78445 Nov  2 18:13 .recently-used.xbel
drwxr-xr-x  2 ed   ed     4096 May 15 17:24 .rubyripper
-rw-------  1 ed   ed       22 Sep 15 17:00 .sqlite_history
drwx------  2 ed   ed     4096 May 14 06:30 .ssh
-rw-r--r--  1 ed   ed        0 Apr 26  2008 .sudo_as_admin_successful
drwxr-xr-x 31 ed   ed     4096 Nov  2 09:59 .themes
drwx------  5 ed   ed     4096 Jun 22 21:35 .thumbnails
drwx------  3 ed   ed     4096 Sep 17 18:29 .tilda
drwxr-xr-x  5 ed   ed     4096 May  6 07:38 .transmission
drwx------  2 ed   ed     4096 Apr 27  2008 .tsclient
drwxr-xr-x  2 ed   ed     4096 Oct 31 17:25 .update-manager-core
drwx------  2 ed   ed     4096 Jun 18 18:59 .update-notifier
drwxr-xr-x  2 ed   ed     4096 Nov  2 09:58 .wapi
-rw-r--r--  1 ed   ed        4 Oct 13 17:32 .windows-label
drwxr-xr-x  4 ed   ed     4096 Oct 31 21:08 .wine
drwx------  3 ed   ed     4096 May 12 22:03 .xchat2
-rw-r--r--  1 ed   ed   132428 Nov  2 18:13 .xsession-errors
drwxr-xr-x  2 ed   ed     4096 Oct 31 23:07 Desktop
drwxr-xr-x  8 ed   ed     4096 Oct  8 20:57 Documents
drwxr-xr-x  3 ed   ed     4096 Aug  8 16:47 Images
drwxr-xr-x  5 ed   ed     4096 Oct 31 06:46 Music
drwxr-xr-x  4 ed   ed     4096 Aug  8 22:23 Pictures
drwxr-xr-x  2 ed   ed     4096 Apr 26  2008 Public
drwxr-xr-x  3 ed   ed     4096 Oct 31 18:16 Share
drwxr-xr-x  2 ed   ed     4096 Apr 26  2008 Templates
drwxr-xr-x  2 ed   ed     4096 Sep 23 16:59 Videos
drwxr-xr-x  4 ed   ed     4096 Aug  8 16:47 public_html

```

But I can't imagine that has much to do with the problem since I can make a brand new account and it won't work.

---

### Post by xavirp on 2008-11-05
> **Chebyshev said:**
> I've tried that and the logon simply fails with no explanation and the prompt is re-presented. Like so:
```
Ubuntu 8.10 rocky tty1

rocky login: ed
password:

Ubuntu 8.10 rocky tty1

rocky login:
```

Exactly the same problem here. I use Intrepid amd_64. Yesterday I've logged in and only installed nvidia driver through envy-ng. I've restarted and been working all the day. When I turn on the computer this morning I was not able to log in.
Anyone has a solution?

Thank you.

---

### Post by xavirp on 2008-11-06
Ok, the following worked for me. The package that seems to cause the problem is libpam_smbpass, after try to login and see dmesg. I only did:

```
apt-get remove libpam-smbpass
```

Now it seems that all works fine.

---

