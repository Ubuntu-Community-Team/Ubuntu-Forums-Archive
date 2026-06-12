---
title: "lost keyboard function after 10.04 upgrade"
date: 2010-05-01
forum: Hardware
---

### Post by nuzzy on 2010-05-01
Hi,

I ran the upgrade from 9.10 to 10.04 and now my mouse works but my keyboard doesn't.  I have Ubuntu set up in VMware Fusion.  Any ideas on how to get it back?

---

### Post by bpb_21 on 2010-05-01
> **nuzzy said:**
> Hi,

I ran the upgrade from 9.10 to 10.04 and now my mouse works but my keyboard doesn't.  I have Ubuntu set up in VMware Fusion.  Any ideas on how to get it back?

No ideas but I've got the same problem.  I tried upgrading from a fully working 9.10 VMware installation as well as a fresh install from the 10.04 CD image, but both gave me the same result - no keyboard input on the login screen (X server).

---

### Post by mdturnerinoz on 2010-05-01
I ran in to the same thing; I reinstalled 10.4 under VMWARE 7 and mouse worked fine but keyboard would not work. I even tried variations of USB setting in the VMWARE Properties to no avail.
 
What DID work for me when I installed it the last time was I did not allow the auto VMware setup to go along (ie where it asks you for you name etc before installation starts (rahter than as you're installing)) I simply installed it selecting VMWare New setup for a 32-bit Linux (ie did not select Ubuntu); this avoids the auto-recognition of Ubuntu by WMWare (and thus the auto-installation of WMWare Tools before installation starts).
 
Once I booted into 10.4 all was well and I could use keyboard/mouse et al (really cool new interface too BTW).
 
Looks like the Cannonical Devs need to contact WMWare and see wazzup with this.
 
HTH
Marty

---

### Post by krzysz00 on 2010-05-23
same, but I'm not in VMWare. However, for me it's only with GNOME and only after some point in the login process.

---

