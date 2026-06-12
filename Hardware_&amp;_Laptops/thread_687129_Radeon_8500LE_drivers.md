---
title: "Radeon 8500LE drivers"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by DATODD on 2008-02-04
I just installed Ubuntu 6.06LTS from a DVD a few days ago.  Video was originally fine, 1024 x 768.   Now when I boot to desktop, I only get 640 x 480 resolution.  No other option available.  I downloaded a Radeon driver from Blogulate.com   ati-driver-installer-8-01-x86.x86_64.run, but I can't get it to install.  After downloading file, I click on run.  But it comes up with an error.  Cou;ld not open .....   The package might be corrupted or you are not allowed to open the file.  Check the permissions of the file.  I logged in as root user.  Also, I downloaded the same file from another site with the same results.  Any help would be appreciated.  I'm new to linux.   gdebi 0.1.4ubuntu13 is the package installer being used.

---

### Post by Yellow Pasque on 2008-02-04
The new Catalyst drivers only work with Radeon 9500 or later (it's a good idea to read release notes before trying to install things).
The included open-source radeon driver should work great. Please post your /etc/X11/xorg.conf file.

---

### Post by lakerssuperman on 2008-02-16
I recently installed gutsy on an old computer with a radeon 8500le.  I got it to work with the vesa driver but when i try to switch to the ati (opensource) driver and reboot it gets past the initial boot but then the screen switches off and does not come back on.  Am I missing a specific setting that needs to be in place for this card to work?  Any help is greatly appreciated.

---

### Post by Yellow Pasque on 2008-02-17
lakerssuperman: maybe this link will help you:
[http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon)

---

