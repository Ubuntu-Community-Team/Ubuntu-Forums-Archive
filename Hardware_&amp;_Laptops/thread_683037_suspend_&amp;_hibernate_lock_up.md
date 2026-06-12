---
title: "suspend &amp; hibernate lock up"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by phoenix5002 on 2008-01-30
I **can** suspend and hibernate my laptop, however when I try to wake it up it doesn't work.  The screen turns on but it stays black, and I can hear the fans spinning and the lights go on, but I never see my desktop again, I have to restart improperly to use it again.  This is very annoying because I don't want to leave my comp on all day but I don't want to shut it down every time either.  Any ideas?

---

### Post by windowskilla on 2008-01-30
Ive got the same problem, with a Toshiba Satellite P105-S6014 laptop its terribly annoying.

---

### Post by Ryan Yo on 2008-01-30
I've got the same problem as well. Huge turn off from Linux for me.

---

### Post by phoenix5002 on 2008-01-30
It seems like a lot of people are having this problem with ubuntu right now.  I hope they sort it out or I might have to switch to a different distribution

---

### Post by kegobeer on 2008-01-30
This is a well known problem with Ubuntu when running ATI/nVidia drivers and using compiz.  If you use the default video drivers and don't enable compiz, can you hibernate?  Also, have you checked out any of the possible fixes (Google for ubuntu gutsy hibernate)?

---

### Post by phoenix5002 on 2008-01-31
I tried not using compiz and hibernate worked however my mouse stopped working on resume, I only had the touchpad.
Suspend still didn't work

---

### Post by chlee on 2008-02-01
same problem.. ATI drivers here. anyway, with fresh install as well after update (without compiz installed yet) my machine refuses to wake. i installed ubuntu a few days ago so i havent worked on this problem yet. major annoyance..

just installed compiz and no change in the sleeping habits.

btw, im using a compaq presario v2000, ati, gutsy, etc..

on a side note, also installed start-up manager and my boot time decreased considerably.. so at this moment i am reduced to shutdown to roam around town.. or.. something to consider, use power management to change the setting for the "when laptop lid is closed". mine "does nothing" when the lid is closed, but of course it all depends on your battery life. yucky. another work around would be to have the machine shut down at a higher level of battery life and thusly saving you enough power to boot and work. that idea seems kinda weird to me because it may force you to shutdown right after boot. hmmm...

:lolflag:

---

### Post by z-itou16 on 2008-02-02
hi guys

i had this same prob just until a couple of minutes ago since i managed to work it now. here is a guide [http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html](http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html)

something i will like to add is while you are editing the hal-system-power-suspend-linux and hal-system-power-hibernate-linux make sure to add the #!/bin/sh
/sbin/s2ram –force and #!/bin/sh
/sbin/s2disk at the begging of the script. 

thanks and good luck

---

### Post by stream303 on 2008-02-02
I'm half-way there.  Hibernate works perfectly with Gutsy on my Hp tx1410us tablet - but I had to add
[B]
doscsi[/B]

to my kernel parameter options for boot.  (or in /boot/grub/menu.lst)

Still no sleep, but at least I can set the thing to hibernate and wake up properly.

---

### Post by z-itou16 on 2008-02-02
hi. i am glad it work at least hibernate. well i am happy for me since i use hibernate the most, i dont really care about susp but still it is ideal to both work.

not sure but i will try to find something more to see if that can help

peace

---

