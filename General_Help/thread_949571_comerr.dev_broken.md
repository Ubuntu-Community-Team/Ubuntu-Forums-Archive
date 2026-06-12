---
title: "comerr.dev broken"
date: 2008-10-16
forum: General Help
---

### Post by Kalidor on 2008-10-16
I tried downloading it from many different locations and installing it thru synaptic, apt-get, aptitude but it only results in

joubert@joubert:~$ sudo aptitude install comerr-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  comerr-dev ...
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main comerr-dev 2.1-1.40.8-2ubuntu2 [41.6kB]
Fetched 41.6kB in 0s (62.0kB/s) 
(Reading database ... 293888 files and directories currently installed.)
Selecting previously deselected package comerr-dev.
(Reading database ... 291967 files and directories currently installed.)
Unpacking comerr-dev (from .../comerr-dev_2.1-1.40.8-2ubuntu2_amd64.deb) ...
Setting up comerr-dev (2.1-1.40.8-2ubuntu2) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing comerr-dev (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 comerr-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up comerr-dev (2.1-1.40.8-2ubuntu2) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing comerr-dev (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 comerr-dev
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
joubert@joubert:~$ 


I need to know how to make this package work cause i need it to install Kile. I also tried to install it thru gdebi after downloading it from my browser but it's the same.
Of course I know how to solve this error that's displayed here. My problem is that after I fix dpkg the next attempt at installing comerr-dev still fails.

---

### Post by gmjs on 2008-10-31
I have the same problem.  I was installing the QT4 development libraries to compile LyX.  It failed due to comerr-dev not installing correctly and now, after trying to purge it from the system, dpkg errors every time it runs regarding this package.

Ideally, I'd like to know how to install this package.  Failing that (Intrepid has been a lousy release for me) can I remove the error about this package without reinstalling?

Thanks,

Graham

---

