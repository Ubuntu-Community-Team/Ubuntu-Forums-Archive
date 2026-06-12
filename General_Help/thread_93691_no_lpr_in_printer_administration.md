---
title: "no lpr in printer administration?"
date: 2005-11-22
forum: General Help
---

### Post by dguido on 2005-11-22
I need to set up my lpr printer in cups and the printer admin wont let me choose lpr.  All ive got are ipp, smb, lpd, and hp jetdirect for network printers.  I tried going to the cups localhost admin ([http://localhost:631](http://localhost:631)) and none of my user names (including root) authenticate with it. The specific entry I need to add is lpr://192.168.1.99/ML-1750 .  Can someone help?

---

### Post by soulestream on 2005-11-22
root logins are turned off by default. 

google - ubuntu root cups 

you should find about 1000 tutorials about setting up root logins in cups.


soule

---

### Post by tim15856 on 2005-11-22
IIRC, the hp jetdirect port sets up an LPR port.

---

