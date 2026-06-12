---
title: "Cannot install or remove DKMS"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by DHV Challenger on 2009-02-22
Finally managed to break my Ubuntu. During the latest update, Virtualbox did not update correctly. Logs seemed to point at DKMS.  Tried to remove and reinstall DKMS. Now I've broken my video driver, Virtualbox, and DKMS. I have tried

```
sudo dpkg -P --force-all dkms
sudo dpkg -i --force-all dkms
```

I still get:

```
doug@Server1:~$ sudo apt-get -f install
sudo: unable to resolve host Server1
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 55.5kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com intrepid/main dkms 2.0.20.4-0ubuntu2 [55.5kB]
Fetched 55.5kB in 1s (40.6kB/s)
(Reading database ... 199884 files and directories currently installed.)
Preparing to replace dkms 2.0.20.4-0ubuntu2 (using .../dkms_2.0.20.4-0ubuntu2_all.deb) ...
/etc/init.d/dkms_autoinstaller: 8: Syntax error: "(" unexpected
invoke-rc.d: initscript dkms_autoinstaller, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/dkms_autoinstaller: 8: Syntax error: "(" unexpected
invoke-rc.d: initscript dkms_autoinstaller, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/dkms_2.0.20.4-0ubuntu2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
/etc/init.d/dkms_autoinstaller: 8: Syntax error: "(" unexpected
invoke-rc.d: initscript dkms_autoinstaller, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/dkms_2.0.20.4-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
doug@Server1:~$ 

```

Any and all help is appreciated!

---

### Post by DHV Challenger on 2009-02-23
Found this info:

[HTML]http://liquidweather.net/howto/index.php?id=59[/HTML]

Tried what it said.

```
sudo rm -f /bin/sh
sudo ln -s /bin/bash /bin/sh
```

This allowed dkms install to continue.

```
sudo apt-get -f install
```

It threw an error, but works:D

---

### Post by lightenup on 2009-03-22
Thank you! The above recommendation fixed my upgrade issue with dkms:


/etc/init.d$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  dkms
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/55.5kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package dkms.
(Reading database ... 126970 files and directories currently installed.)
Preparing to replace dkms 2.0.20.4-0ubuntu2 (using .../dkms_2.0.20.4-0ubuntu2.1_all.deb) ...
/etc/init.d/dkms_autoinstaller: 8: Syntax error: "(" unexpected
invoke-rc.d: initscript dkms_autoinstaller, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/dkms_autoinstaller: 8: Syntax error: "(" unexpected
invoke-rc.d: initscript dkms_autoinstaller, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/dkms_2.0.20.4-0ubuntu2.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
/etc/init.d/dkms_autoinstaller: 8: Syntax error: "(" unexpected
invoke-rc.d: initscript dkms_autoinstaller, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/dkms_2.0.20.4-0ubuntu2.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
/etc/init.d$

---

