---
title: "Pidgin stops working on second login"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by harry2006 on 2009-08-12
hello folks, 
i've been facing some weird problems with pidgin off late. right after i create/add a new account it works fine, then once I logout/quit and try to login again the bottom status bar says "waiting for network connections" and then its stuck. it never goes beyond that phase. Now if i remove that account and re-add the same it works fine..but then after loging out if i try to login again..the same problem. Is someone facing some similar issues? btw i'm using ubuntu 9.4-32bit on dell 1555 with the latest kernel[2.6.28-14-generic ]. thank you very much.

---

### Post by khc on 2009-08-13
your network connection is not recognized by network manager, fix that and it will be fine

---

### Post by harry2006 on 2009-08-13
Yes, you're right. I'm using EVDO modem for connecting to the internet. Earlier my EVDO device was auto-detected as AMB(auto mobile broadband) after I modified the a file used for auto-detecting my modem(i got this clue from googling, don't remember the name of the file, btw). But I guess after I upgraded my kernel it stopped working and I've to resort back to the old method of using "wvdial" and yes this is not getting detected by my network manager...but everything works fine..
how do I make pidgin use the existing internet connection, rather that making it use the so called standard networks as detected by network manager? Thank you very much.

---

