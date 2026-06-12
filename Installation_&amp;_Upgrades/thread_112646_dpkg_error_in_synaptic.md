---
title: "dpkg error in synaptic"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by ubunthu on 2006-01-04
[edit]
I thought this forum might be the right one for questions on dpkg. The number of views suggests that maybe this isn't the right place after all. Anyway, problem solved perhaps. Seems to have been a partial install of a specific pkg (blt) for which another one (blt-demo) is suggested but apparently really a dep. Just a guess. I don't know why the lock file on /var/lib/apt/lists doesn't disappear when synaptic exits -- I guess that's just the way it normally works, but there are no broken pkgs, and the error message no longer appears when synaptic is run, as it did before. Here's the terminal trace. 

```
user@user:~$ sudo apt-get install blt
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  blt-demo
The following NEW packages will be installed:
  blt
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2050kB of archives.
After unpacking 5046kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com breezy/main blt 2.4z-3ubuntu1 [2050kB]
Fetched 2050kB in 10s (187kB/s)

Preconfiguring packages ...
Selecting previously deselected package blt.
(Reading database ... 66317 files and directories currently installed.)
Unpacking blt (from .../blt_2.4z-3ubuntu1_i386.deb) ...
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry
<= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

user@user:~$ sudo apt-get remove blt Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  blt
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 5046kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 66401 files and directories currently installed.)
Removing blt ...
user@user:~$ sudo dpkg --configure -a
user@user:~$

```
[/edit]

I'm having exactly the same problem described here:

[INDENT][http://www.ubuntuforums.org/showthread.php?t=11373&highlight=process_queue](http://www.ubuntuforums.org/showthread.php?t=11373&highlight=process_queue)[/INDENT]

and apparently resolved quit a while ago:

[INDENT][https://bugzilla.ubuntu.com/show_bug.cgi?id=4760](https://bugzilla.ubuntu.com/show_bug.cgi?id=4760)[/INDENT]

The error is happening repeatedly with installation of different packages but began with the one below. Synaptic quits following the error message. Suggestions welcome.

install apmd + powermgmt-base

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a'
to correct the problem. 

dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry 
<= 4' failed.
Aborted

user@user:~$ sudo dpkg --configure -a
Password:
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry
<= 4' failed.
Aborted

user@user:~$ sudo apt-get remove powermgmt-base
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  apmd libapm1 powermgmt-base
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 487kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 66367 files and directories currently installed.)
Removing apmd ...
Removing libapm1 ...
Removing powermgmt-base ...
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry
<= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
user@user:~$
```

---

