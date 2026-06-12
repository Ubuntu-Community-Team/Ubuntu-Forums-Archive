---
title: "Brother driver mfc4800lpr broke Package Manager."
date: 2009-02-10
forum: Hardware
---

### Post by brookie on 2009-02-10
Hello,

Please help me fix my ubuntu intrepid 8.10 package manager. 

I recently tried to install a driver from brother for my old mfc4800, needless to say I upgraded to a new printer since then but my package manager is now broken and I cannot uninstall/reinstall this driver to fix it.

I found previous threads on this here and tried various things but cannot solve this problem yet. 

[http://ubuntuforums.org/showthread.php?t=92922](http://ubuntuforums.org/showthread.php?t=92922) 
[http://lists.debian.org/debian-user/2005/04/msg01317.html](http://lists.debian.org/debian-user/2005/04/msg01317.html) 

Here's what I get when I try to remove it:
user@computer:~/Desktop$ sudo apt-get remove --purge mfc4800lpr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.


Here's what I get when I try to re-install it:
user@computer:~/Desktop$ sudo dpkg -i mfc4800lpr-1.1.2-1.i386.deb
Selecting previously deselected package mfc4800lpr.
(Reading database ... 126789 files and directories currently installed.)
Preparing to replace mfc4800lpr 1.1.2-1 (using mfc4800lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc4800lpr ...
/var/lib/dpkg/info/mfc4800lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc4800lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc4800lpr-1.1.2-1.i386.deb

I can still use my pc, but I can no longer get updates because package manager errors out on this package and I have a big red circle on the task bar: An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. 
The error message was: 'Unknown Error:'<type 'exceptions.SystemmError'. (E:The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.)'This usually means that your installed packages have unmet dependencies.

I would greatly appreciate any help on this as I am new to ubuntu. 

Thanks in advance, 
Brookie


btw, I got the brother deb driver here:
[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-4800](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-4800) 

and I followed these instructions here: 
[http://solutions.brother.com/linux/en_us/instruction_prn3.html](http://solutions.brother.com/linux/en_us/instruction_prn3.html)

---

### Post by brookie on 2009-02-10
bump, 
any help please on this mfc4800lpr mess? 
i'm pretty good at reinstalls but this should be fixable. 
hopefully optmistic, 
brookie :)

---

### Post by brookie on 2009-02-10
i found this link and got PackageManager unstuck but don't know if it completely solved my problem? 

[http://www.ubuntugeek.com/package-installation-error-and-solution.html](http://www.ubuntugeek.com/package-installation-error-and-solution.html) 

1. i deleted all the mfc4800lpr files from /var/lib/dpkg/info

user@computer:/var/lib/dpkg/info$ ls -l | grep mfc
-rw-r--r-- 1 root root      0 2004-02-03 02:09 mfc4800lpr.conffiles
-rw-r--r-- 1 root root      0 2009-02-10 12:06 mfc4800lpr.list
-rwxr-xr-x 1 root root    125 2009-02-10 10:37 mfc4800lpr.postinst
-rwxr-xr-x 1 root root     71 2009-02-10 10:48 mfc4800lpr.postrm
-rwxr-xr-x 1 root root     87 2004-02-03 02:09 mfc4800lpr.prerm
user@computer:/var/lib/dpkg/info$ sudo rm mfc4800lpr*

2. then i ran this

user@computer:/var/lib/dpkg/info$ sudo dpkg --remove --force-depends --force-remove-reinstreq mfc4800lpr
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `mfc4800lpr' missing, assuming package has no files currently installed.
126788 files and directories currently installed.)
Removing mfc4800lpr ...
user@computer:/var/lib/dpkg/info$ 

*** looks like this solved the problem. hope this may be of help to someone else. :) ***

---

### Post by kdog_1914 on 2009-04-15
> **brookie said:**
> i found this link and got PackageManager unstuck but don't know if it completely solved my problem? 

[http://www.ubuntugeek.com/package-installation-error-and-solution.html](http://www.ubuntugeek.com/package-installation-error-and-solution.html) 

1. i deleted all the mfc4800lpr files from /var/lib/dpkg/info

user@computer:/var/lib/dpkg/info$ ls -l | grep mfc
-rw-r--r-- 1 root root      0 2004-02-03 02:09 mfc4800lpr.conffiles
-rw-r--r-- 1 root root      0 2009-02-10 12:06 mfc4800lpr.list
-rwxr-xr-x 1 root root    125 2009-02-10 10:37 mfc4800lpr.postinst
-rwxr-xr-x 1 root root     71 2009-02-10 10:48 mfc4800lpr.postrm
-rwxr-xr-x 1 root root     87 2004-02-03 02:09 mfc4800lpr.prerm
user@computer:/var/lib/dpkg/info$ sudo rm mfc4800lpr*

2. then i ran this

user@computer:/var/lib/dpkg/info$ sudo dpkg --remove --force-depends --force-remove-reinstreq mfc4800lpr
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `mfc4800lpr' missing, assuming package has no files currently installed.
126788 files and directories currently installed.)
Removing mfc4800lpr ...
user@computer:/var/lib/dpkg/info$ 

*** looks like this solved the problem. hope this may be of help to someone else. :) ***


This worked perfectly!  Thank you!

---

### Post by undrline on 2011-08-21
Thanks, this helped me solve the "mfc4800lpr: subprocess installed pre-removal script returned error exit status 127" error in Lucid 10.04.

---

