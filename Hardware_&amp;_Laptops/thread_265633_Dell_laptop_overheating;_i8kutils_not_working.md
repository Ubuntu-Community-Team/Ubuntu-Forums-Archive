---
title: "Dell laptop overheating; i8kutils not working"
date: 2006-09-26
forum: Hardware &amp; Laptops
---

### Post by lwr on 2006-09-26
My Inspiron 2500 is badly overheating. Most of the time the fans don't run, but when it gets really hot, one of the two fans kicks in. However, it's clearly not enough as my system just froze for ages. I've tried installing i8kutils, but I get the following message:
```
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed
  i8kutils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/31.4kB of archives.
After unpacking 135kB of additional disk space will be used.
dpkg-deb (subprocess): failed to exec tar: Permission denied
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/i8kutils_1.27_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/i8kutils_1.27_i386.deb
sh: /usr/bin/touch: Permission denied
E: Problem executing scripts DPkg::Post-Invoke 'if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi'
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm not sure if i8kutils will solve my problems anyway, as apparently it doesn't work well with my machine. Any suggestions anybody? Thanks for your help.

---

### Post by jlm3030 on 2007-03-12
I have a Inspiron 2500 also and ran OpenSuse for a long time but I had the same problem as you. My computer would over heat and cut off. Only one fan works. Unfortunately I8Kutils does not work with the inspiron 2500 it is actually stated in the read me file. When I switched over to Ubuntu 6.10 I have not had any problems with it cutting off but only one fan comes on.  I can tell you that the fans are controlled by the bios and not linux. Although Dell locks their bios so you can not edit it. Some things that seemed to help is running the computer at a lower CPU speed (don't know how in ubuntu) and cooling the laptop externally I did this with a towel covered icepack although they do sell laptop coolers.  I hope this can help a little I certainly feel your frustration and if you find anything else that helped please post it. Good Luck:)

---

