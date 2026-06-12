---
title: "Brother printer drivers - differences?"
date: 2015-01-21
forum: Hardware
---

### Post by superian on 2015-01-21
I've just switched from using a 32bit version of a Ubuntu flavour to the 64bit* one and this means installing a couple of drivers for the new setup. 

My printer is a Brother HL2250DN and the drivers are at [http://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=hl2250dn_eu_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=hl2250dn_eu_as&os=128)

The ones I've used for ages, and which the 'driver install tool' installs**, are the first two: LPR and CUPSwrapper, both from 2010.

There's also another pair: Generic LPR and Generic CUPSwrapper, both from 2014. The latter leads to brgenml1cupswrapper-3.1.0-1.i386.deb, for example. 

**What I can't find anywhere is any indication as to what the difference is!** Is there any advantage to using the later ones?

 * [SIZE=1]A quick note of gratitude to Debian for how easy that is while retaining data and settings if you have a separate /home partition![/SIZE]

** [SIZE=1]Including making sure that the 32bit libraries are there, via lib32stdc++ ...[/SIZE]

---

### Post by Li_Wu on 2015-09-17
the model specific stuff that brother offers is best. Usually the brother download site offers only a single installer for any particular model. (except when  .deb / .rpm choice must be made manually)

DRIVER INSTALL TOOL offered by brother's download site then detects the right choices for you. usually works nicely.

---

