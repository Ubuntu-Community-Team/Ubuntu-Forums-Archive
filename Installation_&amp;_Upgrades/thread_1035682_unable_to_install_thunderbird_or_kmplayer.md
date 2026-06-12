---
title: "unable to install thunderbird or kmplayer"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by akrai on 2009-01-10
i am new to ubuntu and i am having a problem installing new softwares 
for eg. if i try to install thunderbird, i get the following error:
```

akrai@ubuntu:~$ sudo apt-get install thunderbird
[sudo] password for akrai: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
thunderbird is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                                                                                                      invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)
akrai@ubuntu:~$ 


```
can anybody tell me whats happening?
will be thankful!!

---

### Post by Partyboi2 on 2009-01-10
Looks like others have been having the same problem. See [[COLOR=Blue]here[/COLOR]]("http://joeb454.ubuntuforums.org/showthread.php?t=976149")
Try reinstalling the package
Open a terminal (Applications>Accessories>Terminal) and
```
sudo apt-get --reinstall install system-tools-backends
```
If that does not work then try compete removal of the package as mentioned in Post #14 of the above link.

---

### Post by gabore on 2009-02-08
how to install kmplayer to ubuntu?

just type to the terminal:

sudo apt-get install kmplayer

It will download some files so make sure the internet connection is ready.

---

