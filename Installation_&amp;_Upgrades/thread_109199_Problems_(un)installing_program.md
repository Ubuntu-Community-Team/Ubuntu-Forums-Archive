---
title: "Problems (un)installing program"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by Dr. E on 2005-12-28
I have tried to install WordPerfect for Linux and ran into dependency problems, for this reason I tried to uninstall it by issuing the command:

dre@home:~/Desktop$ sudo apt-get remove wp-full_8.1-12_i386.deb
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package wp-full needs to be reinstalled, but I can't find an archive for it.

The package is on my desktop, but for some reason cannot be found.  I agree with the message that I need to reinstall it so I tried:

dre@home:~/Desktop$ sudo dpkg -i wp-full_8.1-12_i386.deb
(Reading database ... 76539 files and directories currently installed.)
Preparing to replace wp-full 8.1-12 (using wp-full_8.1-12_i386.deb) ...
Unpacking replacement wp-full ...
/var/lib/dpkg/info/wp-full.postrm: line 5: type1inst: command not found
/var/lib/dpkg/info/wp-full.postrm: line 5: /usr/X11R6/bin/mkfontdir: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 5: type1inst: command not found
/var/lib/dpkg/tmp.ci/postrm: line 5: /usr/X11R6/bin/mkfontdir: No such file or directory
dpkg: error processing wp-full_8.1-12_i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 5: type1inst: command not found
/var/lib/dpkg/tmp.ci/postrm: line 5: /usr/X11R6/bin/mkfontdir: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 wp-full_8.1-12_i386.deb

Any help would be greatly appreciated.

---

