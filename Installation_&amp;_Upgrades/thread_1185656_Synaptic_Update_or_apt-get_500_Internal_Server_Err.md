---
title: "Synaptic Update or apt-get 500 Internal Server Error"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by vanhorng on 2009-06-12
First i need to mention that I am trying to get through a proxy to do my updates, and really haven't had much luck.   I have finally gotten past authentication errors and now i still have these internal server errors.   I have manually navigated to the Ubuntu sites that hold these packages and downloaded the files.   However, that gets pretty difficult as you deal with dependencies.   

Next, i have tried the main repository and the US repository, but they both have the same '500 internal server error' response.   I believe at one point i have tried the "apt-get cache clean" type of command as well as the "apt-get update" commands with no luck.   Does anyone have any suggestions?  I know there are a bunch of threads on this topic, but i have yet to come across a solution that works for me.  

Using Synaptic Package Manager or apt-get from the command line I get errors like the following:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main html2text 1.3.2a-3build2
  500 Internal Server Error
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main intltool-debian 0.35.0+20060710.1
  500 Internal Server Error
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main po-debconf 1.0.10
  500 Internal Server Error
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main debhelper 6.0.4ubuntu1
  500 Internal Server Error
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/html2text/html2text_1.3.2a-3build2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/html2text/html2text_1.3.2a-3build2_i386.deb)  500 Internal Server Error
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/intltool-debian/intltool-debian_0.35.0+20060710.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/intltool-debian/intltool-debian_0.35.0+20060710.1_all.deb)  500 Internal Server Error
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_1.0.10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_1.0.10_all.deb)  500 Internal Server Error
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_6.0.4ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_6.0.4ubuntu1_all.deb)  500 Internal Server Error


Thanks, 
Gerry

---

### Post by zvacet on 2009-06-13
I just tried links you provided and they are working fine.Can you browse the net?

---

### Post by vanhorng on 2009-06-16
Yeah, i can browse the net just fine through Firefox.

---

