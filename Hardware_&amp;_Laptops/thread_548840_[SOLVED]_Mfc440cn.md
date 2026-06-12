---
title: "[SOLVED] Mfc440cn"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by talikarng on 2007-09-11
Hello,
I am trying to install a brother MFC440CN on my laptop which is running kubuntu 7.04 (I am using kde-core instead of kubuntu-desktop). I have successfully installed the lpd deb file and cupsys.
I got the printer to run on kubuntu-desktop but now that I have gone back to kde-core this is the error message I get when i try to install the cups wrapper:

brendan@brendan-laptop:~/Desktop$ sudo dpkg -i --force-overwrite mfc440cncupswrapper-1.0.0-10.i386.deb
Selecting previously deselected package mfc440cncupswrapper.
(Reading database ... 50099 files and directories currently installed.)
Preparing to replace mfc440cncupswrapper 1.0.0-10 (using mfc440cncupswrapper-1.0.0-10.i386.deb) ...
/var/lib/dpkg/info/mfc440cncupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc440cn/cupswrapper/cupswrappermfc440cn: Permission denied
dpkg: warning - old pre-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/local/Brother/Printer/mfc440cn/cupswrapper/cupswrappermfc440cn: Permission denied
dpkg: error processing mfc440cncupswrapper-1.0.0-10.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 126
/var/lib/dpkg/info/mfc440cncupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc440cn/cupswrapper/cupswrappermfc440cn: Permission denied
cp: cannot stat `/usr/share/cups/model/brmfc440cn.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mfc440cncupswrapper-1.0.0-10.i386.deb

Any suggestions?
Thanks.

---

### Post by talikarng on 2007-09-12
Solved!

All I did was delete any reference to mfc440cncupswrapper in /var/lib/dpkg/info and run "sudo aptitude remove mfc440cncupswrapper".

Then after going through the installation process again everything worked.

---

