---
title: "new install, can NOT update"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by binskipy2u on 2009-04-23
I added all repos, from software sources....etc..
and i picked all i wanted to install..and i get this error after download..

****************
debconf: DbDriver "templatedb": could not open /var/cache/debconf/templates.dat
dpkg: unrecoverable fatal error, aborting:
 failed to open diversions file: Stale NFS file handle
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: unrecoverable fatal error, aborting:
 failed to open diversions file: Stale NFS file handle


ive rebooted, picked one package at a time, just inc ase
and same error..

thanks

---

### Post by binskipy2u on 2009-04-24
im bumping myself..dont want to reinstall if this is something simple i could fix or if anyone else had the same issue and "fixed" it so to speak
thanks

---

### Post by Cerny on 2009-04-26
Yah, I'm encountering the same issue on my machine after I did an upgrade. Here is the error I'm getting. 

```

chris@Dreamy:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gstreamer0.10-plugins-bad liblucene2-java
The following packages will be upgraded:
  bluetooth bluez bluez-alsa bluez-cups bluez-gstreamer bluez-utils consolekit
  gnome-system-tools libbluetooth3 libck-connector0 libgweather-common
  libgweather1 libpam-ck-connector notification-daemon pidgin-libnotify wine
16 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/12.4MB of archives.
After this operation, 336kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `libnspr4-0d-dbg': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

I've tried this multiple ways using the update manager or the terminal and I end up with the same error either way.

---

