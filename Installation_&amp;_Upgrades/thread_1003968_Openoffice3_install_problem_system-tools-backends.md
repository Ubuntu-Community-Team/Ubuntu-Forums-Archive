---
title: "Openoffice3 install problem: system-tools-backends??"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by frncz on 2008-12-06
Hello

Whichever method I sue to try to install openoffice 3 on my Intrepid  AMD system, I get the following error message, which I don't know how to deal with:

dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)

This is at the end of applying the method offered by fooman, even after applying the 'Edit' at the end of the message.

Can someone help please

Thanks

Mike

---

### Post by inobe on 2008-12-06
what tutorial did you follow ?


have you tried this one

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

you will be opted to remove the old version, that is your choice.

edit: if you are running intrepid 64 bit, you can snatch the tar.gz from here

[ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz/](ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz/)

---

### Post by frncz on 2009-01-11
This turns out to be a documented bug. Following the instructions in the bug report the problem was soved.

Many thanks

Mike

---

