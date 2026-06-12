---
title: "DRDY ERR and LVM"
date: 2010-03-27
forum: Hardware
---

### Post by Mikey-D on 2010-03-27
Hey all, I'm getting close to full-blown panic mode here, and could really use some help.

I haven't actually USED my desktop system in a few months now, other than to turn it on and ssh/scp to it.  One day, I found I could no longer actually do anything on it.  Commands executed on that machine (scp copies to/from, and various other commands run through ssh) stopped working.  When I went to restarted it, the monitor wouldn't display anything.  Replaced the video card, and now I get the pleasure of seeing a bunch of DRDY ERR messages on start up.

I can boot from a live cd, and I can mount MOST of my drives without any trouble.  The main system drive, however, gives me errors when I try to boot it (the above DRDY ERR messages; I can try to get a copy of them up here if need be).

For some reason, way back when I first set up this system, I decided to go with an LVM.

I REALLY need to get data (my thesis) off this drive (or I lose several months worth of work; this was my backup copy, and my laptop just kicked the bucket).

e2fsck gives me "Bad magic number in super-block while trying to open /dev/sda1", as does dumpe2fs.

suggestions?  Please??

---

### Post by Mikey-D on 2010-03-29
Have to bump this...Anyone?  Suggestions?  Somewhere to look??

---

