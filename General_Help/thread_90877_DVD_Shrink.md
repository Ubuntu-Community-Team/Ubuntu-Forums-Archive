---
title: "DVD Shrink"
date: 2005-11-16
forum: General Help
---

### Post by Drifter on 2005-11-16
I followed manika's thread on how to install dvd shrink with wine.  Everything went ok, I have it installed and it will run, but when I select open disk my drives are not detected.  Anyone know what to do for this.

---

### Post by Drifter on 2005-11-16
Anyone have a how to I can read on this.

---

### Post by darknuala on 2005-11-16
mrbass.org has a great howto.

I used the newest version of wine to install, and that option finally works with the newest version of wine.  I'm a lot happier with it now.

---

### Post by Drifter on 2005-11-16
Thanks I will try mrbass later today.

---

### Post by jstrubberg on 2005-11-16
Did you run winecfg?

Run it (not as root, as you) and go to the drives  tab.  Click auto detect.  Close winecfg and try dvdshrink again.  Your drives should be there.

---

### Post by pickarooney on 2005-11-16
just as a matter of interest, what is the major advantage of DVDshrink over something like dvd::rip?

---

### Post by Drifter on 2005-11-16
I am at work now, I will try that when I get home.  As to the advantage of dvd shrik over rip, I have not idea if there is an advantage.  shrink will let u put a movie backup on a single disk by compression.

---

### Post by Original Brownster on 2005-11-16
Hi,
You could try xdvdshrink or lxdvdrip which are native to linux, both are good at shrinking a dvd9 to a dvd5 disk, the latter just finds the main feature and leaves out the extra 'features'.

I wrote a howto for lxdvdrip recently which you'll find on the ubuntu wiki.

---

### Post by Drifter on 2005-11-16
This is what I get in terminal when I start config for wine.


david@ubuntu5:~$ winecfg
err:winecfg:load_drives GetVolumeInformation() for 'F:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'F:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'F:\' failed, setting serial to 0

winecfg comes up and the drives are dectedted but they do not show up when I try to open a dvd in shrink.

---

### Post by darknuala on 2005-11-16
[QUOTE=pickarooney]just as a matter of interest, what is the major advantage of DVDshrink over something like dvd::rip?[/QUOTE]


DVDshrink just works.  It compresses down to 9to5 ratio.  I haven't ever been able to use dvd::rip for anything accept ripping to the hard drive.  i can use dvdbackup to do that.  dvd::rip is good if I wanted to convert it to a single file format, but I have no use for that.

I use dvdbackup to mirror the dvd image, and dvdshrink creates an .iso file around 4.4 gigs.

---

### Post by taygan on 2005-12-26
HOWTO make DVD Shrink detect your DVD drive details:

to detect your drive in DVDShrink you need to :

from terminal start WINECFG
click on DRIVES
click AUTOCONFIG if you haven't already (so it sees your drives)

** here's the KEY PART THAT FIXES THINGS **

click on your dvd drive letter (mine is G:)
click SHOW ADVANCED
change the Type: dropdown box to CD-ROM

and voila, your drive will be there.

---

### Post by Snocrash on 2005-12-26
Just wondering......

I use Cedega for gaming on my linux box and have had problems running wine and cedega on the same box. I was wondering if DVDShrink and DVDDecrypter run in Cedega or not??? Anyone try this yet?????


Thanks,

Sno

---

### Post by Sebby on 2005-12-26
[QUOTE=taygan]HOWTO make DVD Shrink detect your DVD drive details:

to detect your drive in DVDShrink you need to :

from terminal start WINECFG
click on DRIVES
click AUTOCONFIG if you haven't already (so it sees your drives)

** here's the KEY PART THAT FIXES THINGS **

click on your dvd drive letter (mine is G:)
click SHOW ADVANCED
change the Type: dropdown box to CD-ROM

and voila, your drive will be there.[/QUOTE]
Fantastic. I've wanted to get this working for ages. :D

---

