---
title: "[sudo apt-get install ...] is broken"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2009-05-29
I get this whenever I try to install anything.

> (Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `libjpeg62' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)


What is that?

---

### Post by rehilliard on 2009-05-29
found this:

[http://ubuntuforums.org/showthread.php?t=1154174](http://ubuntuforums.org/showthread.php?t=1154174)

---

### Post by Maheriano on 2009-05-29
Awesome, thanks. Got that fixed, now it's doing this:

> deemar@Chugger:/var/lib/dpkg$ sudo apt-get install libsdl1.2debian-pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libsdl1.2debian-alsa
The following NEW packages will be installed:
  libsdl1.2debian-pulseaudio
0 upgraded, 1 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B/208kB of archives.
After this operation, 4096B disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: libsdl1.2debian-alsa: dependency problems, but removing anyway as you request:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-4ubuntu3) | libsdl1.2debian-all (= 1.2.13-4ubuntu3) | libsdl1.2debian-esd (= 1.2.13-4ubuntu3) | libsdl1.2debian-oss (= 1.2.13-4ubuntu3) | libsdl1.2debian-nas (= 1.2.13-4ubuntu3) | libsdl1.2debian-pulseaudio (= 1.2.13-4ubuntu3); however:
  Package libsdl1.2debian-alsa is to be removed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `rhythmbox' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)


---

