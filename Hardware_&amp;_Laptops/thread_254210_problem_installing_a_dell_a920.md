---
title: "problem installing a dell a920"
date: 2006-09-09
forum: Hardware &amp; Laptops
---

### Post by underworld288 on 2006-09-09
ok I got the driver from the lexmark site (a lexmark z600 driver) then I extracted the files but when I go to run the "z600cups-1.0-1.gz.sh" files I get this...

Verifying archive integrity...OK
Uncompressing Lexmark Printer Drivertrap: usage: trap [-lp] [arg signal_spec ...]

I don't get it, can someone help me?

thanks

---

### Post by underworld288 on 2006-09-10
ok i've got the .deb files but now when I try to install it it gives me this

(Reading database ... 86946 files and directories currently installed.)
Preparing to replace z600cups 1.0-2 (using z600cups.deb) ...
Unpacking replacement z600cups ...
/var/lib/dpkg/info/z600cups.postrm: line 2: /etc/init.d/cups: is a directory
dpkg: warning - old post-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 2: /etc/init.d/cups: is a directory
dpkg: error processing z600cups.deb (--install):
 subprocess new post-removal script returned error exit status 126
/var/lib/dpkg/tmp.ci/postrm: line 2: /etc/init.d/cups: is a directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 z600cups.deb

anybody know what I should do, I know I already have it installed but Ubuntu says I need to reinstall the driver. 

thanks

---

