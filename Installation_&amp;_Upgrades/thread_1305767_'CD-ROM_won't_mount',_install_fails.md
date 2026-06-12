---
title: "'CD-ROM won't mount', install fails"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by tehowe on 2009-10-30
Hello;

On attempt to install or run a live session from the new Karmic ISO, the process grinds to a halt after about a minute and the screen just goes black. Hitting CTRL-ALT-DEL reveals a message that it wasn't able to find a workable session, something along those lines.

Trying Ubuntu Studio is a bit more informative, as it simply says that it can't mount the CD-ROM (which in this case is no CD-ROM but a 'HL-DT-ST DVD-RAM GSA-H22L' according to the Windows properties. That's an LG drive)

One other thing - on rebooting and going back into XP, all the icons on my desktop were shuffled over to the left side of the screen, as though the screen resizing that the Ubuntu install routine was doing had affected my XP desktop. That can't be right.

Any ideas? I'd really been looking forward to moving to 9.10, as you can imagine. I can't even try a live session! :(

---

### Post by tehowe on 2009-10-30
[This, btw, is on a single boot XP system. I had to scrub my dual-boot system and reformat to wait for karmic because of a separate problem a month ago.]

---

### Post by PeggySue on 2009-10-30
I had a similar problem upgrading to 9.10.

I burnt second CD from the downloaded iso.  This at least started up but the data integrity test flagged 1 error.  Burnt another CD - still 1 error.
Downloaded the iso again, burnt a CD from that and bingo all is well.  From now on no CD gets loaded without an md5sum check!

First impressions of 9.10 are good.  Somehow feels nicer!

Sorry can't give a more definitive answer and I will be interested to see what folk say about the windows icons.

---

### Post by Stochastic on 2009-10-30
Yes, always do an md5sum check before attempting any installs or upgrades.  My first guess is that it's an md5sum issue causing your failed CD-ROM mount.

---

### Post by tehowe on 2009-10-30
The ironic thing is, it needs to mount in order to do that too.

It happens right after the 'starting PC-card services' routine, then it tries to mount the CD and fails.

---

