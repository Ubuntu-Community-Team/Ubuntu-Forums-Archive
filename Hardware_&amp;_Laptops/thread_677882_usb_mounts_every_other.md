---
title: "usb mounts every other"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by scales on 2008-01-25
hey all i just installed gutsy on my asus eee and i am noticing that my usb drive only mounts every second time i plug it in.  example, i plug it in, it flashes, then nothing.  i unplug and re-plug and it works.  suggestions?

EDIT: it is a usb flash drive (stick)

---

### Post by Daelyn on 2008-01-25
Most likley the external HDD standby that causes it.

Ubuntu doesn't wait long enough for the external hdd to spin up and be fully accessible, it starts scanning before that happens.

What you can do is switch the external HDD mains supply on/off and wait for five seconds before connecting it. By then, the external HDD will be spun up and ready to be accessed.

Or, plug it in, remove it once it starts spinning and then plug it in again 3 seconds later.


But, I suppose there is another fix somewhere. 
Maybe someone knows how to increase the time ubuntu waits for the drive to settle/spin up?

---

### Post by scales on 2008-01-25
humm, not likely it is spin startup, it is  flash usb drive....any other thoughts?

---

### Post by oldsoundguy on 2008-01-25
try a POWERED enclosure.  Don't rely on the on board USB to power it up!

---

### Post by scales on 2008-01-25
i will just assume you missed my post, i am dealing with a usb flash stick....

---

### Post by oldsoundguy on 2008-01-25
No, I did not miss your post .. I use external USB hard drives.  So, to me, PLUGGING in a drive means plugging in a REAL drive .. something like 250gb.
And the "spin up" comment is also for that type of drive.  A FLASH drive does not spin  up.
Check your connection .. make sure it is solid and not loosy goosy. I have a front mounted USB on one of my computers that is LOOSE and because of that, grounding is an issue and it does not work all of the time. (have to take the whole box apart to be able to get to it and that includes REMOVING the motherboard, so I don't USE it except in an emergency!)

---

### Post by scales on 2008-01-26
no that definately isnt the problem, i have a new laptop and the usb port works fine when windows is running.  it is definately something with ubuntu....

---

### Post by oldsoundguy on 2008-01-26
for grins, try plugging it in BEFORE you turn the laptop on and boot up.  Just SOMETIMES that works better .. unknown reason why.  I have USB items in XP on a couple of machines that just disappear and sometime that works for them.

---

### Post by scales on 2008-01-26
ok well i can try that but i still would like to fix the problem.  i shouldnt have to turn off my laptop to plug a usb device in.  any setting or value i can look at?

---

### Post by scales on 2008-01-28
anyone?

---

