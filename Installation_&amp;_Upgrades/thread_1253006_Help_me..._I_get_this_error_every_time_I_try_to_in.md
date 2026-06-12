---
title: "Help me... I get this error every time I try to install all app in ubuntu"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by eumura on 2009-08-29
Setting up php5-cli (5.2.6.dfsg.1-3ubuntu4.2) ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/php for update_mode ()
dpkg: error processing php5-cli (--configure):
 subprocess post-installation script returned error exit status 2
Setting up php5-dev (5.2.6.dfsg.1-3ubuntu4.2) ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/php-config for update_mode ()
dpkg: error processing php5-dev (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 php5-cli
 php5-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please help me.. I can't install anything cause this error
My Os : Ubuntu Jaunty 64 bit 
AMD Athlon X2

---

### Post by eumura on 2009-08-29
I can't install anything and I can't remove too

---

### Post by Wiebelhaus on 2009-08-29
[From:]("http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/")


> After you get that error, try apt-get -f install to force an install of the files that didn't get loaded because of the error. Then try apt-get upgrade again, apt-get -f install back and forth until only the package that has the error is left.

---

