---
title: "problem in update manager"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by prasad.bh1 on 2009-10-06
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.



Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

prasad@ubuntu:~$ ping gb.archive.ubuntu.com
PING gb.archive.ubuntu.com (194.169.254.10) 56(84) bytes of data.
64 bytes from ubuntu.datahop.net (194.169.254.10): icmp_seq=1 ttl=51 time=218 ms

prasad@ubuntu:~$ ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.45) 56(84) bytes of data.
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=1 ttl=49 time=313 ms

and when I tried to do it from terminal 

prasad@ubuntu:~$ sudo apt-get update

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

please help !

wr,
prasad

---

### Post by scragar on 2009-10-06
```
gksu gedit /etc/apt/sources.list
```
Comment out any lines begining with **cdrom://** using the **#**

Save and try the package manager again.

---

### Post by Korozu on 2009-10-06
Try different server,go to software source,choose other server and try again.


Korozu

---

