---
title: "Printer HP-LaserJet-1005 doesn't work"
date: 2008-08-13
forum: General Help
---

### Post by DrCoolSanta on 2008-08-13
I have the HP LJ 1005 printer. It gets recognised by ubuntu but does not print. I surfed google to only find that it needed to load a firmware befor starting to print. So I got ubuntu to load it automatically. Now the printer makes some noises and  blinks the lights (thats normal for it) and then it just does not print. If I check my dmesg, it tells me that I removed the printer. Please help, this printer does not work with Vista and my XP does not work any more.

EDIT: I was just working with the issue, and found out that it was hp-lip that was causing the issue. I was able to fix it, by removing hplip. Then my computer detected my printer not as hp:/ but usb:/. After this, I had to load the firmware manually and then I could print easilly.

---

### Post by bmac on 2008-08-13
Always best to use the Ubuntu pre-installed drivers prior to installing vendor drivers. At least that's been my experience. I always assume (bad mistake) that individuals posting and requesting printer installation assistance have already tried the Ubuntu pre-installed drivers.... 
Something for all of us take note of: "when assisting - don't assume anything"....

---

### Post by tigrez on 2008-12-16
I've the same bug, and I've resolved removing hplip and re-install the printer...

---

### Post by sunfire on 2009-03-24
I had same proplem that printer didn't do nothing. But it was recognised by Kubuntu 8.10.


Solved by:

"sudo hp-setup" and press enter untill install is done :)

---

### Post by sarum on 2009-08-09
I'm a bit late in adding to this; but for weeks I've searched the beginers' forum and other places, never thinking that the answer would be with the geeks, rather than us newbies(I'm of the long term elderly variety).
I'll remember this in future - each time my LaserJet leaps into action.
Thanks a million...............sarum

---

