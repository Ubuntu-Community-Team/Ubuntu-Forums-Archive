---
title: "Palm Pilot: How to do a full restore/backup?"
date: 2004-12-11
forum: Hardware &amp; Laptops
---

### Post by AndyGates on 2004-12-11
I've got an ageing Palm M105 and I'm syncing to J-Pilot ('cos it's lighter than Evolution, I can't see my To Dos in Evolution, and I prefer Thunderbird as a mail client).

Alas, my batteries are low.  And because this is an old workhorse Palm that's been carried around in my bike panniers, it's a bit beaten up and usually loses all settings and data when I change the batteries.

Reading the J-Pilot documentation, it says that if I try to sync to a blank Palm, it'll wipe my data, as it will take the blank device as the master record.  D'oh!  So I (rather urgently) need some way of taking a full backup and restore of my Palm which I can do on either side of the battery change.

Something like:

     palm_magic_happy_app --backup --all
     palm_magic_happy_app --restore --all

    .... would be fantastic.  Does such a thing exist?

---

### Post by AndyGates on 2004-12-11
Aha, found it.  The pilot-link package has pilot-xfer which looks like it does the job.

**pilot-xfer --port *portname* --backup *directory*** backs it up and **pilot-xfer --port *portname* --restore *directory*** restores it.  I couldn't ask for anything more.

(And of course its **sudo apt-get install pilot-link** to get it.  Yay!)

---

### Post by AndyGates on 2004-12-11
Ha! Batteries died halfway through.  However, J-Pilot does have backup and restore powers too, at least in v0.99.7.  I'm off for a beer...

---

### Post by 7serii7219 on 2007-05-15
> **AndyGates said:**
> Aha, found it.  The pilot-link package has pilot-xfer which looks like it does the job.

**pilot-xfer --port *portname* --backup *directory*** backs it up and **pilot-xfer --port *portname* --restore *directory*** restores it.  I couldn't ask for anything more.

(And of course its **sudo apt-get install pilot-link** to get it.  Yay!)


[demonstrate physics magnets Debt Consolidation bread](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

