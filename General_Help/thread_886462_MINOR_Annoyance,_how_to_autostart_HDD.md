---
title: "MINOR Annoyance, how to autostart HDD?"
date: 2008-08-11
forum: General Help
---

### Post by davidw89 on 2008-08-11
What i mean by "autostart" my 3 other internal hard drive (NTFS) is that unless i manually open my 3 internal hard drive by going to Places --> Computer and then clicking on the hard drive and browsing inside which will place a copy of it on the desktop. How do i "automatically" do this when i start? How do i put a short cut to these drives on the desktop?

If you don't understand what i am trying to say let me know. Basically i find it annoying that programs like XBMC can't access your videos/movies unless you've unless the hard drive after you booted up. This is annoying and it should be like Windows XP where you can access it straight away.

---

### Post by hyper_ch on 2008-08-11
add them to your fstab

besides Windows is not Linux ;)

---

### Post by davidw89 on 2008-08-12
fstab?

---

### Post by Tim Sharitt on 2008-08-12
Take a look at this tutorial: [http://psychocats.net/ubuntu/mountwindows]("http://psychocats.net/ubuntu/mountwindows").

---

### Post by linux_tech on 2008-08-12
in terminal type:
gconf-editor
Go to /apps/nautilus/desktop/volumes_visible
Make sure box is checked for volumes visible 

fstab is a file that contains your drive configuration info
sudo cat /etc/fstab
Links- 
[http://thetechnut.wordpress.com/2008/06/18/automounting-ntfs-drives-in-ubuntu-804/](http://thetechnut.wordpress.com/2008/06/18/automounting-ntfs-drives-in-ubuntu-804/)
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

To mount a share permanently:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

If you want to write to ntfs-
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
[http://www.howtoforge.com/ntfs_3g_pclinuxos](http://www.howtoforge.com/ntfs_3g_pclinuxos)

---

