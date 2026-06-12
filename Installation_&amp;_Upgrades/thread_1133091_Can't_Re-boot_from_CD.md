---
title: "Can't Re-boot from CD"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by the_zuke on 2009-04-22
I tried to come in part way through a post and feel it is fairer if I start a new one. Sorry if I butted in somewhere else.

Problem:

I wiped out some multimedia files through synaptic packaging. When I rebooted the sytem I was unable to get back into my desktop. It went straight to a black screen in terminal mode, and it wanted to me to log in like I would in old DOS days - richard@desktop. I tried to reboot using the CD I burned, but it would not let me reinstall, or go to any type of setup menu. I even went into CMOS and changed the setting to go to CD. The disk reads on one of my other systems, but not on the one I am trying to configure.

Simply:
Can't get to the CD to reboot or reinstall or do anything
If anyone out there has an idea I would be very happy. This all started from my own stupidity and trying to solve a sound issue.
AND
The Cd I am using is the CD I correctly installed Ubuntu with in the first place. Went well, loved it, and then needed to muck about and mess it up when the sound wouldn't play. I thought I was just wiping out sound drivers I did not need. OOOOPS

---

### Post by kestrel1 on 2009-04-22
It is possible that your CD drives laser is dirty or the drive is faulty in some way. Can you swap it out for a known good drive?

---

### Post by the_zuke on 2009-04-22
I had a Back up CD, I tried shuting down all the alternatives in CMOS, and this time it worked; go figure; I have no idea; but it did not work the way I understood; I am just happy to have it back, but still having trouble with getting my sound up and running; won't do anything with Sb on an ASUS board. I am looking further. thanx a ton for responding nonetheless

---

### Post by kestrel1 on 2009-04-22
Lets try & sort tha sound then. What is the output of ```
lspci
```

---

