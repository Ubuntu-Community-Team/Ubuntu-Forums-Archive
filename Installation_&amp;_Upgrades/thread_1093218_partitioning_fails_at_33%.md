---
title: "partitioning fails at 33%"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by Glen Dahl on 2009-03-11
ubuntu-8.10-server-i386.iso to burn installer cd. It worked great on another installation and tests fine on this one.

Asus P5LD2 motherboard with 2gb ram

maxtor 250 gb 6L250R0 ide drive

4 - 500 gb Seagate ST3500630AS sata drives

I tried to set up the partitions / and swap on the maxtor intending to mount the others later for storage drives.

The formatting starts and freezes at 33%

Same thing happened with Debian 5.

Couldn't install xp on it either, just got a black screen.

Maxtor's maxblast utility formatted the drive (low level) and proclaimed it to be fine.

Wierd. Anybody seen this kind of thing before?

I have now tried every drive on it's own with the same result. I noticed some i/o error messages at the start of the install but I believe they involve the dvd drive. Could it be the problem?

---

### Post by samborambo on 2009-03-11
Probably dodgy SATA cables or an intermittent fault with the controller. Try using a PCI SATA controller and known-good cables.

---

### Post by Therion on 2009-03-11
Yeah, I have actually and it's the kind of thing that can drive a man insane.  Low level solution to try that has worked in the past...

Unplug all but the install drive.  DO the install BUT... When it comes time to reboot for the first time after the install completes?  That's when you strike! HA HA!  

You do a full shutdown instead, reconnect the "slave" drives and *then* you restart.

No promises, no guarantees, no money-back refunds; but it worked for me once.

You could also try pre-formatting the drive using a Gparted LiveCD.

---

### Post by Glen Dahl on 2009-03-13
Well I'm just gob-smacked. It was a bad stick of ram.

---

