---
title: "Brother MFC-665CW installation issue"
date: 2008-12-09
forum: Hardware
---

### Post by froggontherocks on 2008-12-09
When I go to install the cups wrapper for this printer that i downloaded from the companies website i get this also the package manager keeps telling me it's in a critical unstable state. How do i get this installed properly? I did try and run the update manager when it poped up and did the option for the partial upgrade and it asked if i wanted to remove it. I clicked yes and it won't remove it just says it needs to be reinstalled and can't find the package. I am running Ubuntu 8.10 also
 
chad@chad-desktop:~/Documents$ sudo dpkg  -i  --force-all  --force-architecture mfc665cwcupswrapper-1.0.1-1.i386.deb
Selecting previously deselected package mfc665cwcupswrapper.
(Reading database ... 117911 files and directories currently installed.)
Preparing to replace mfc665cwcupswrapper 1.0.1-1 (using mfc665cwcupswrapper-1.0.1-1.i386.deb) ...
/var/lib/dpkg/info/mfc665cwcupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
dpkg: error processing mfc665cwcupswrapper-1.0.1-1.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc665cwcupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
chmod: cannot access `/usr/local/Brother/Printer/mfc665cw/cupswrapper': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mfc665cwcupswrapper-1.0.1-1.i386.deb
chad@chad-desktop:~/Documents$ sudo dpkg  -i  --force-all  --force-architecture mfc665cwcupswrapper-1.0.1-1.i386.deb
(Reading database ... 117911 files and directories currently installed.)
Preparing to replace mfc665cwcupswrapper 1.0.1-1 (using mfc665cwcupswrapper-1.0.1-1.i386.deb) ...
/var/lib/dpkg/info/mfc665cwcupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
dpkg: error processing mfc665cwcupswrapper-1.0.1-1.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc665cwcupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
chmod: cannot access `/usr/local/Brother/Printer/mfc665cw/cupswrapper': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mfc665cwcupswrapper-1.0.1-1.i386.deb

I also thought I would copy this in it's what i got when trying the suggestion by the update manager.

chad@chad-desktop:~$ sudo apt-get install -f
[sudo] password for chad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc665cwcupswrapper needs to be reinstalled, but I can't find an archive for it.

---

