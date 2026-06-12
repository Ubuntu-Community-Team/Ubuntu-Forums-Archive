---
title: "Black Screen after 8.10 Upgrade"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by Armando Penblade on 2008-12-16
I just upgraded my PC from 8.04 to 8.10, and am now getting a black screen after Ubuntu loads (but before the login screen).  I would tell you if I can hear login sounds, but Ubuntu still doesn't support my sound card, so I can't hear anything at all.

I have read the other thread on this matter.  The two main solutions (Remove compiz and tell the xorg.conf file to display out to the "DPF" to avoid it outputting video to the VGA port instead of the DVI port) have not fixed the problem.

One user in the other thread continuously posts about "manually installing the ATI drivers the 'ubuntu way'," and links to this page: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually)

I would do that, except that I *can't* download the stupid drivers because I *can't* get into Ubuntu, and even if I could get them into a flash drive, I have no way of accessing the flsh drive because I *can't get into Ubuntu.*  I have no idea how he expects me to install drivers that require a download when I have no visuals whatsoever.

Does anyone have some other solution to the black screen of death problem so that I can see if I can get anything else to work in the system.

---

### Post by moron on 2008-12-16
In my case, most of the time I can get around this problem by doing CTRL-ALT-F1 to select a terminal window and the CTRL-ALT-F7 to get back to KDM / GDM.  Trick is catching it before this happens (which is sporadic in my case).

Still is driving me up the wall though (I feel your pain).

Cheers

---

