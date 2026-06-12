---
title: "CD/DVD not working after upgrading to 8.10"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by Krister Johansson on 2008-12-31
Hi 
After upgrading from 8.04 to 8.10 my cd/dvd-player wont work. Message when trying to play a cd or dvd:

*DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. *

...including these suggestions of causes:

*the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.*

Is this a common failure? Easy to fix? 

I&#7743; using HP laptop Pavilion ze4414. CD-unit: TSSTcorp cd/dvdw sn-w082b

---

### Post by sblanzio on 2008-12-31
same problem trying to automount with gnome a plugged Luks encrypted disk that correctly works when mounted via console.

found this
[https://bugs.launchpad.net/bugs/288584](https://bugs.launchpad.net/bugs/288584)

---

