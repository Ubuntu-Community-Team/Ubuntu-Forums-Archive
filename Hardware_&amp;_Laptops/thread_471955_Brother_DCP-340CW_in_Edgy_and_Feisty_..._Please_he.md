---
title: "Brother DCP-340CW in Edgy and Feisty ... Please help!!!"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by applecookie on 2007-06-12
Hi Folks.

I've tried to get my Brother Multifunction Printer to work under Edgy (or in future under Feisty), but I did not get the clue, how to make him print.

I got the original drivers from the brother linux website and tried the How - To's

[http://ubuntuforums.org/showthread.php?t=302960](http://ubuntuforums.org/showthread.php?t=302960)

and 

[http://ubuntuforums.org/showthread.php?t=423461&highlight=340CW](http://ubuntuforums.org/showthread.php?t=423461&highlight=340CW)

and 

[http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)

and 

[http://doc.ubuntu-fr.org/materiel/brother_dcp-340cw](http://doc.ubuntu-fr.org/materiel/brother_dcp-340cw)


No way!!!

I got him scan but no printing at all! In Fact it produces no .PPD - File, which I can use!

Can somebody please help me????

Regards

Frank

---

### Post by Cuppa-Chino on 2007-06-17
bump yes please somebody provide some help I am facing similar issue

[mfc 240c feisty 64 thread]("http://ubuntuforums.org/showpost.php?p=2731712&postcount=9")

and I am clueless!

latest error:
```
 sudo dpkg --install --force-architecture mfc240ccupswrapper-1.0.0-9.i386.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 134591 files and directories currently installed.)
Preparing to replace mfc240ccupswrapper 1.0.0-9 (using mfc240ccupswrapper-1.0.0-9.i386.deb) ...
/var/lib/dpkg/info/mfc240ccupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: Permission denied
dpkg: warning - old pre-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: Permission denied
dpkg: error processing mfc240ccupswrapper-1.0.0-9.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 126
/var/lib/dpkg/info/mfc240ccupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: Permission denied
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 126
Errors were encountered while processing:
 mfc240ccupswrapper-1.0.0-9.i386.deb

```

---

