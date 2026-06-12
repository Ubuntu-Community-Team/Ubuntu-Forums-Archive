---
title: "Intrepid with Samba/Swat version mismatch"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by RangerHal on 2009-02-09
I am trying to install SWAT with my Samba version 2:3.2.3-1ubuntu3.5~ppa1 on my Intrepid system.  The Synaptic Package Manager has SWAT at version 2:3.2.3-1ubuntu3.4.

When I try to install using Synaptic, after marking for installation I get the following error message: "swat:  Depends: samba (=2:3.2.3-1ubuntu3.4) but 2:3.2.3-1ubuntu3.5~ppa1 is to be installed."

I have tried apt-get with similar results.  How can I fix this?

---

### Post by Partyboi2 on 2009-02-09
Have you tried searching and highlighting samba in Synaptic then going to Package>Force Version, then see if you can change the samba version to (=2:3.2.3-1ubuntu3.4)

---

### Post by RangerHal on 2009-02-10
If I try to force the version of "Samba" I do not get an "apply" button.  If I then also force the version of "samba-common" there are dependency removals including "smbclient" and "smbfs".  I suppose I could mark Samba for complete removal and start again.  But ...

I don't want to lose this sort-of working Samba.  Do you know of another tool beside SWAT for configuring Samba? 

Thanks.

---

