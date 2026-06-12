---
title: "Can't Print using the Canon MP560"
date: 2012-01-30
forum: Hardware
---

### Post by mclizardman on 2012-01-30
My printer is being difficult to say the least. When I go to add a printer, it doesn't show up unless I go into the windows printer via samba. When I find it, I can't select it. It is shared on the network, and I am in the network. I've tried to install the drivers for it, but I'm using 64 bit Ubuntu, so i have to force architecture. However, I get a lot of errors, and am forced to do a partial upgrade to resolve them. Here's what I get:
```

dpkg: error processing –force-architecture (--install):
 cannot access archive: No such file or directory
Selecting previously deselected package cnijfilter-common:i386.
(Reading database ... 154765 files and directories currently installed.)
Unpacking cnijfilter-common:i386 (from .../cnijfilter-common_3.20-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 –force-architecture
 cnijfilter-common:i386

```    

How can I fix my printer? Thanks!

---

### Post by alfefried on 2012-02-01
> 
No more fooling around with making any files.

This site shows you how to do the ppa route and install what you need no matter x86 or x64.

[http://www.ubuntubuzz.com/2011/06/do...er-driver.html]("http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html")


This worked fine for me, after hours, but yet !

The 228 Mo took a bit of time to download, but no more  worries after that.

Ubuntu 11.10 64
works in wifi

THAAAAANKS !

---

### Post by mclizardman on 2012-02-04
> **alfefried said:**
> This worked fine for me, after hours, but yet !

The 228 Mo took a bit of time to download, but no more  worries after that.

Ubuntu 11.10 64
works in wifi

THAAAAANKS !


Thanks a lot for the help, my printer works fine now!

---

### Post by mörgæs on 2012-02-04
Moved to the hardware forum.

---

