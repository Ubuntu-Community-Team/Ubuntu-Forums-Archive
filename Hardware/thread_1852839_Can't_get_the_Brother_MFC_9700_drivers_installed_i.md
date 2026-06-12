---
title: "Can't get the Brother MFC 9700 drivers installed in Ubuntu 11.04 !"
date: 2011-10-01
forum: Hardware
---

### Post by dchen on 2011-10-01
Downloaded and followed the Brother site's instruction tried to install the MFC 9700 drivers (lpr and cupswraooer) without any success!  Below is the command results :

           sudo dpkg -i --force-all mfc9700lpr-1.1.2-1.i386.deb
           dpkg: warning: overriding problem because --force enabled:
           package architecture (i386) does not match system (amd64)
           Selecting previously deselected package mfc9700lpr:i386.
           (Reading database ... 187587 files and directories currently installed.)
           Preparing to replace mfc9700lpr:i386 1.1.2-1 (using mfc9700lpr-1.1.2-1.i386.deb) ...
           Unpacking replacement mfc9700lpr:i386 ...
           Replaced by files in installed package brother-lpr-drivers-laser1 ...
           /var/lib/dpkg/info/mfc9700lpr.postrm: 3: /etc/init.d/lpd: not found
           dpkg: warning: subprocess old post-removal script returned error exit status 127
           dpkg - trying script from the new package instead ...
           /var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
           dpkg: error processing mfc9700lpr-1.1.2-1.i386.deb (--install):
           subprocess new post-removal script returned error exit status 127
           /var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
           dpkg: error while cleaning up:
           subprocess new post-removal script returned error exit status 127
           Errors were encountered while processing:
           mfc9700lpr-1.1.2-1.i386.deb

I then mkdir the /etc/init.d/lpd directory, did the install again, got the permission denied error:

           sudo mkdir /etc/init.d/lpd
           dchen@server:~/Downloads$ sudo dpkg -i --force-all mfc9700lpr-1.1.2-1.i386.deb
           dpkg: warning: overriding problem because --force enabled:
           package architecture (i386) does not match system (amd64)
           (Reading database ... 187587 files and directories currently installed.)
           Preparing to replace mfc9700lpr:i386 1.1.2-1 (using mfc9700lpr-1.1.2-1.i386.deb) ...
           Unpacking replacement mfc9700lpr:i386 ...
           Replaced by files in installed package brother-lpr-drivers-laser1 ...
           /var/lib/dpkg/info/mfc9700lpr.postrm: 3: /etc/init.d/lpd: Permission denied
           dpkg: warning: subprocess old post-removal script returned error exit status 126
           dpkg - trying script from the new package instead ...
           /var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: Permission denied
           dpkg: error processing mfc9700lpr-1.1.2-1.i386.deb (--install):
           subprocess new post-removal script returned error exit status 126
           /var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: Permission denied
           dpkg: error while cleaning up:
           subprocess new post-removal script returned error exit status 126
           Errors were encountered while processing:
            mfc9700lpr-1.1.2-1.i386.deb

Any help will be appreciated!

---

