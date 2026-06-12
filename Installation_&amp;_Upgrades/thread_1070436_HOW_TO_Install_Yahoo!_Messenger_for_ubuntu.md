---
title: "HOW TO: Install Yahoo! Messenger for ubuntu"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by royx117 on 2009-02-15
i download it from 
[http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb](http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb)


when i start sate up it show me this 

roxy@roxy-desktop:~/Desktop$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb 
[sudo] password for roxy: 
Selecting previously deselected package ymessenger.
(Reading database ... 117306 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

what should i do .........

---

### Post by tuskenraider on 2009-02-15
pidgin  

yahoo messenger with out the issues.


tusken

p.s do they even make a different IM program? i use pidgin on all my boxes. Ubuntu and windoze alike.

---

### Post by overlord.gaurav on 2009-02-15
You need to install libssl0.9.8:

```
sudo apt-get install libssl0.9.8 
```

But, you better use some other messenger client. The Yahoo messenger for Linux is pathetic and outdated.
You may want to try [GYachI]("http://gyachi.sourceforge.net/index.shtml"). It has most of the features of the Y! messenger for Windows.

---

### Post by PGHammer on 2009-02-15
> **overlord.gaurav said:**
> You need to install libssl0.9.8:

```
sudo apt-get install libssl0.9.8 
```

But, you better use some other messenger client. The Yahoo messenger for Linux is pathetic and outdated.
You may want to try [GYachI]("http://gyachi.sourceforge.net/index.shtml"). It has most of the features of the Y! messenger for Windows.

I actually PREFER Pidgin to most non-Windows/Mac Yahoo clients.  That was the case when operating entirely 32-bit, and that has merely been underscored now that I've crossed over to the 64-bit side.  If the Win64-version of Pidgin was as reliable, I'd switch in Vista64 as well.

---

