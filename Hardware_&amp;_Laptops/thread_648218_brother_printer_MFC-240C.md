---
title: "brother printer MFC-240C"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by evaristegalois on 2007-12-23
I just bought a brother MFC-240C and followed the instructions on 

[http://ubuntuforums.org/showthread.php?t=486675](http://ubuntuforums.org/showthread.php?t=486675)

Here are the error messages that I get if I try to install 


sudo dpkg -i mfc240ccupswrapper-1.0.0-10.i386.deb

(Reading database ... 131291 files and directories currently installed.)
Preparing to replace mfc240ccupswrapper 1.0.0-10 (using mfc240ccupswrapper-1.0.0-10.i386.deb) ...
/var/lib/dpkg/info/mfc240ccupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
dpkg: error processing mfc240ccupswrapper-1.0.0-10.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc240ccupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
cp: cannot stat `/usr/share/cups/model/brmfc240c.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mfc240ccupswrapper-1.0.0-10.i386.deb

I did install mfc240clpr-1.0.0-9.i386.deb first and there was no problem. Now I can't even start Synaptic any more and get rid of this package.

The salient line seems to be 

cp: cannot stat `/usr/share/cups/model/brmfc240c.ppd': No such file or directory

because that's the one I got when I first tried this installation and which messed everything up. There is another post on

[http://www.mepislovers.org/forums/showthread.php?p=77128](http://www.mepislovers.org/forums/showthread.php?p=77128)

of someone whose Synaptic was also totally messed up by this.

Any help?

---

### Post by evets on 2007-12-25
[[COLOR="red"]Try the methods listed in this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=140920") . I had the same issue, and they fixed it for me.

Good luck.

---

