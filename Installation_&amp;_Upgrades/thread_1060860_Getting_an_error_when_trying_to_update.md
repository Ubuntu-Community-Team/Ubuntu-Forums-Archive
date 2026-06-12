---
title: "Getting an error when trying to update"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by darthen on 2009-02-05
When I try to update manually then I get this message and I don't know how t solve this problem

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by oldos2er on 2009-02-05
Open a terminal and run
```
sudo dpkg --configure -a
```

---

### Post by darthen on 2009-02-07
thx problem solved

---

### Post by madverb on 2009-02-07
HAHAHAHAHHAHAHA Gold!

---

### Post by sixstringmonk on 2009-02-09
I have this same problem. When running sudo dpkg --configure -a I get:

```
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

```

---

### Post by sixstringmonk on 2009-02-09
More info

```
[username]:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
27 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: error processing libldap-2.4-2 (--configure):
 package libldap-2.4-2 is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: error processing vim-common (--configure):
 package vim-common is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: error processing ufw (--configure):
 package ufw is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: error processing acpi-support (--configure):
 package acpi-support is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: error processing ghostscript (--configure):
 package ghostscript is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: error processing gnome-power-manager (--configure):
 package gnome-power-manager is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: error processing libxine1-bin (--configure):
 package libxine1-bin is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: error processing nautilus (--configure):
 package nautilus isNo apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
           not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: error processing poppler-utils (--configure):
 package poppler-utils is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: error processing pulseaudio (--configure):
 package pulseaudio is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: error processing pulseaudio-esound-compat (--configure):
 package pulseaudio-esound-compat is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: error processing pulseaudio-utils (--configure):
 package pulseaudio-utils is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: error processing xserver-xorg-video-intel (--configure):
 package xserver-xorg-video-intel is not ready for configuration
 cannot configure (current status `triggers-awaited')
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          No apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

---

### Post by sixstringmonk on 2009-02-09
It seems to have resolved itself after a few reboots. :)

---

### Post by sixstringmonk on 2009-02-10
Nope... It's back. :(

---

