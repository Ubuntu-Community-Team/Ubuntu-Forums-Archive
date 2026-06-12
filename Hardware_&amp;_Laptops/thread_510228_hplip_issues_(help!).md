---
title: "hplip issues (help!)"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by wickstopher on 2007-07-26
Hey, there.  I've been trying to get printer functionality in Feisty working since I installed it on my machine several months ago.  I have an HP Deskjet 3845.  Back in Edgy, I was able to use the Foomatic GUI tool "Printers" in the Add/Remove list to get it working.  For some reason, this application doesn't work in Feisty for me.  When I launch it from the Applications menu, nothing happens.  When I use the command-line,   I get this message:

```
gksu -u root /usr/bin/foomatic-gui
(foomatic-gui:28265): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Unable to read printer database.

```

I have since tried using HPLIP with no success.  When I try to launch the HPLIP toolbox from the System>Preferences menu, nothing happens.  When I use the command line, I get this message:

```
 /usr/bin/hp-toolbox

HP Linux Imaging and Printing System (ver. 2.7.6)
HP Device Manager ver. 9.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
error: Unable to connect to HPLIP I/O (hpssd).

```

Also of interest, whenever I install a new software package (ANY software package, which seems strange to me...I first noticed it when installing the ubuntu-studio packages) from the command line, I get this message:
```
sudo apt-get install lynx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lynx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up hplip (1.7.3-0ubuntu1) ...
Creating/updating hplip user account...
 * Starting HP Linux Printing and Imaging System                                     [fail] 
invoke-rc.d: initscript hplip, action "start" failed.
dpkg: error processing hplip (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hplip
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Any help out there?  I'd really like to get my printer up and running...one less reason to boot up that rusty old XP partition.  Thanks!

---

### Post by wickstopher on 2007-07-26
Just for anyone who is looking, I finally broke down and did yet another install with the hplip auto-installer, and for some reason, despite all the error messages I received, and despite the fact that I've tried the same thing 3 times before, this time it works.  All of my problems have been solved.  I'm not sure how, because I went through the exact same process, but it worked.

---

