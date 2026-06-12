---
title: "How to mount windows volumes on LIVE Ubuntu 6.06 LTS ?"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by sco1984 on 2006-07-27
I have IBM® ThinkPad R50e which is Centrino 1.5 . 256 MB ram,
 40 GB and 855 motherboard. I received 5 CD pack from Ubuntu.
 I run it as a LIVE Cd. After booting it shows all volumes present on my hard disk drives including 1 volume which contains
installed Mandriva 2006 and rest 2 volumes which are Windows
 volumes. When i click on them to open, it shows me error that
failed to mount volume. Anybody know how to mount those volumes
 through LIVE cd of UBUNTU 6.06 LTS ?

 Regard's,
Amey. :KS

---

### Post by ajgreeny on 2006-07-27
usually in Ubuntu you mount an NTFS windowsXP partition (assuming you don't mount it at bootup) with the command:-
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

I can see no good reason why it shouldn't work in the Live CD version, though you may not need sudo, as I think everything is as root in the live version.

To mount your Mandriva 2006 you will need a command like this:-
sudo mount /dev/hdb1       /media/storage/ -t ext3
though you will probably want or need to change the partition identity, and give a different name to the mount point (/media/storage in my example).  Best of luck, and welcome to Ubuntu!

---

### Post by sco1984 on 2006-07-27
Thank you for the quick reply. One more query is, from where
 i can get access to "Terminal" or to "console" ? in mandriva,
 it gives a sperate program which contains "Konsole" and other
 program's. I doubt if Ubuntu made LIVE CD contains very limited.
 :?:

---

### Post by ajgreeny on 2006-07-27
Konsole is just the KDE version of gnome-terminal; it doesn't matter which you use as either will do the same job and both are just terminal programs.

---

### Post by Atomic Dog on 2006-07-27
I believe this will do it:

Make sure /media/windows directoty exists.  If not then create it by typing:
sudo mkdir /media/windows

Then type:
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

---

