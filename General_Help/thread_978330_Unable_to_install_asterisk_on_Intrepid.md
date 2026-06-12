---
title: "Unable to install asterisk on Intrepid"
date: 2008-11-11
forum: General Help
---

### Post by BenFranske on 2008-11-11
I'm having a problem which popped up as a broken asterisk package during a messy upgrade to Intrepid. I have backups of my important asterisk files so I decided to try and resolve the problem by removing and reinstalling the asterisk package but the package managers refuse to do it giving me errors along the lines of:

asterisk: Depends: libct3 (>= 0.63-1) but it is not installable

It seems that libct3 is no more and is replaced by freetds-common but this is not suggested by the package manager and I haven't found a way to force asterisk to install. Is there a known problem installing asterisk on Intrepid? Any solutions? This is on a server with no GUI so everything is being done from the command line.

Thanks!

---

### Post by soro2005 on 2008-11-11
Are you sure you have the "universe" sections enabled and pointed to intrepid in your /etc/apt/sources.list? B/c from what I see, the asterisk package does not longer have that dependency ([http://packages.ubuntu.com/intrepid/asterisk](http://packages.ubuntu.com/intrepid/asterisk)).

---

### Post by BenFranske on 2008-11-11
Thanks, I somehow missed switching the multiverse/universe repositories to intrepid.

---

