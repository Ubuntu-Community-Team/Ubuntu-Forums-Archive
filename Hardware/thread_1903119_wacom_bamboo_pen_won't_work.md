---
title: "wacom bamboo pen won't work"
date: 2012-01-01
forum: Hardware
---

### Post by kinsago on 2012-01-01
Hi all.

I have a Wacom Bamboo Pen (CTL-470K) which is refusing to work.

So far I have tried numerous tutorials, downloads, PPAs and have even changed distros (gone from 11.10, 11.04, 10.04) to try to get it working and so far no luck.

I'm not getting any errors when compiling new modules, it just simply won't work!!!

Please please please can anyone help me as I've run out of ideas.

Many thanks

---

### Post by Favux on 2012-01-01
Hi kinsago,

Since the Wacom Bamboo Connect Pen (CTL-470K) is new as of October 2011 it is not yet in the kernel.  Chris Bagwell has submitted support for the third generation BambooPTs to the 3.3 kernel.  He backported those patches to the 2.6.38 kernel and later in input-wacom-0.12.0.  So to get it working you need at least Natty and at least input-wacom-0.12.0.  The reason for the 2.6.38 kernel limitation is that is the first kernel to have the mt.h (multi-touch header).

Follow the instructions in part I. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Also if you used a PPA that has a dkms implementation of wacom.ko (the usb kernel driver) that needs to be removed.  That's because the non-working dkms wacom.ko from the PPA will overwrite any new working wacom.ko you compile.  So remove the PPA's packages through Synaptic or whatever.  The exception is Lekensteyn's PPA for Natty and Oneiric cited in the Note before part I.  That does use input-wacom-0.12.0.

---

### Post by kinsago on 2012-01-02
Thanks, worked a treat :)

---

