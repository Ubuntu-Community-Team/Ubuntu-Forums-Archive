---
title: "Exim4 error"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by Fertech on 2009-01-18
i can't seem to install Exim4. i get this error.```
fertech@fertech-desktop:~$ sudo apt-get install exim4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bsd-mailx exim4-base exim4-config exim4-daemon-light mailx
Suggested packages:
  eximon4 exim4-doc-html exim4-doc-info libmail-spf-query-perl swaks
The following NEW packages will be installed:
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light mailx
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
fertech@fertech-desktop:~$ 

```

---

### Post by Fertech on 2009-01-18
```
fertech@fertech-desktop:~$ sudo rm /var/cache/apt/archives/lock
fertech@fertech-desktop:~$ sudo apt-get install exim4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bsd-mailx exim4-base exim4-config exim4-daemon-light mailx
Suggested packages:
  eximon4 exim4-doc-html exim4-doc-info libmail-spf-query-perl swaks
The following NEW packages will be installed:
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light mailx
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 1895kB of archives.
After this operation, 4076kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com intrepid/main exim4-config 4.69-5ubuntu2 [312kB]
Get:2 http://us.archive.ubuntu.com intrepid/main exim4-base 4.69-5ubuntu2 [984kB]
Get:3 http://us.archive.ubuntu.com intrepid/main exim4-daemon-light 4.69-5ubuntu2 [425kB]                                                                   
Get:4 http://us.archive.ubuntu.com intrepid/main exim4 4.69-5ubuntu2 [6354B]                                                                                
Get:5 http://us.archive.ubuntu.com intrepid/main bsd-mailx 8.1.2-0.20071201cvs-3 [159kB]                                                                    
Get:6 http://us.archive.ubuntu.com intrepid/main mailx 1:20071201-3 [8296B]                                                                                 
Fetched 1895kB in 11s (166kB/s)                                                                                                                             
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously deselected package exim4-config.
(Reading database ... 118898 files and directories currently installed.)
Unpacking exim4-config (from .../exim4-config_4.69-5ubuntu2_all.deb) ...
Selecting previously deselected package exim4-base.
Unpacking exim4-base (from .../exim4-base_4.69-5ubuntu2_i386.deb) ...
Selecting previously deselected package exim4-daemon-light.
Unpacking exim4-daemon-light (from .../exim4-daemon-light_4.69-5ubuntu2_i386.deb) ...
Selecting previously deselected package exim4.
Unpacking exim4 (from .../exim4_4.69-5ubuntu2_all.deb) ...
Selecting previously deselected package bsd-mailx.
Unpacking bsd-mailx (from .../bsd-mailx_8.1.2-0.20071201cvs-3_i386.deb) ...
Selecting previously deselected package mailx.
Unpacking mailx (from .../mailx_1%3a20071201-3_all.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 4 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up exim4-config (4.69-5ubuntu2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing exim4-config (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of exim4-base:
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:
  Package exim4-config is not configured yet.
  Package exim4-config-2 is not installed.
  Package exim4-config which provides exim4-config-2 is not configured yet.
dpkg: error processing exim4-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4-daemon-light:
 exim4-daemon-light depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
dpkg: error processing exim4-daemon-light (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4:
 exim4 depends on exim4-base (>= 4.69); however:
  Package exim4-base is not configured yet.
 exim4 depends on exim4-daemon-light | exim4-daemon-heavy | exim4-daemon-custom; however:
  Package exim4-daemon-light is not configured yet.
  Package exim4-daemon-heavy is not instalNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                    No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                 No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                                                                                                              led.
  Package exim4-daemon-custom is not installed.
dpkg: error processing exim4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on exim4 | mail-transport-agent; however:
  Package exim4 is not configured yet.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on bsd-mailx; however:
  Package bsd-mailx is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exim4-config
 exim4-base
 exim4-daemon-light
 exim4
 bsd-mailx
 mailx
E: Sub-process /usr/bin/dpkg returned an error code (1)
fertech@fertech-desktop:~$ sudo dpkg-reconfigure exim4-config
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
fertech@fertech-desktop:~$ 


```

---

### Post by Partyboi2 on 2009-01-18
Try rebooting  then try to install exim4 again.

---

### Post by albinootje on 2009-01-18
> **Fertech said:**
> i can't seem to install Exim4. i get this error.
-- cut --
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)


If you want to use "apt-get" then you need to shutdown add/remove or Synaptic package manager, or.. wait till the update-manager has updated the repositories.

---

### Post by Fertech on 2009-01-19
thank you rebooting my machine solved my problem.
```
fertech@fertech-desktop:~$ sudo apt-get install exim4
[sudo] password for fertech: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
exim4 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up exim4-config (4.69-5ubuntu2) ...
Adding system-user for exim (v4)

Setting up exim4-base (4.69-5ubuntu2) ...

Setting up exim4-daemon-light (4.69-5ubuntu2) ...
 * Starting MTA                                                          [ OK ] 

Setting up exim4 (4.69-5ubuntu2) ...

Setting up bsd-mailx (8.1.2-0.20071201cvs-3) ...

Setting up mailx (1:20071201-3) ...
Setting up pwgen (2.06-1) ...
fertech@fertech-desktop:~$ 


```

---

### Post by albinootje on 2009-01-19
> **Fertech said:**
> thank you rebooting my machine solved my problem.
```
fertech@fertech-desktop:~$ sudo apt-get install exim4
-- cut --
Setting up mailx (1:20071201-3) ...
Setting up pwgen (2.06-1) ...
fertech@fertech-desktop:~$ 


```

Good for you! :)

But I hope you understand now why you got that error, and why rebooting helped.
Rebooting, when not really needed, is in my opinion a MS-Windows solution, which keeps the end user "uninformed" and therefore also dependent and uncertain about what really happened.

---

