---
title: "Install of Breezy (both 32 and 64 bit dies) at gs-common package"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by mossholderm on 2005-12-22
Hi everyone...

    Has anyone else run into problems getting Breezy to install on K8 hardware, where the base-config (the part of the install that happens after the reboot), dies trying to install gs-common?

   For me, this is occurring with both the 32bit and 64 bit installation CDs, across several attempts.  I noticed in the kern.log from the 64bit install the following errors:

```
Dec 21 23:50:24 localhost kernel: [  666.560849] defoma-font[24311] general protection rip:2aaaab20f700 rsp:7fffffc52528 error:0
Dec 21 23:50:34 localhost kernel: [  674.857987] frontend[24312] general protection rip:2aaaab20f700 rsp:7ffffff4b0e8 error:0
Dec 21 23:53:54 localhost kernel: [  788.983871] apt-config[24560] general protection rip:2aaaab24d295 rsp:7fffffaf56b0 error:0
Dec 22 00:17:04 localhost kernel: [ 1560.355985] sh[24840] general protection rip:2aaaaae3c295 rsp:7fffffdb75e0 error:0
```

I'm using a Foxconn 755A01-6ELRS motherboard, Sempron 64 3100+ CPU, 1GB memory.

Also of note, the system DOES run Breezy fine, post install, since I can run the system diskless (network boot) without issues. I'm beating on it pretty heavily ( it is a MythTV backend with an ivtv encoder card, as well as a MythTV front end doing HDTV playback), and the system has been stable for several days. This testing was performed with a 32bit OS.

Help?

---

### Post by mossholderm on 2005-12-23
Here's an update. Hoary 64 bit installed with no problems. Upgrading causes the big boom again, however.

     Thanks,

            --Matt

---

