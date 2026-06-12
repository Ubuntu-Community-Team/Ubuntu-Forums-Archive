---
title: "Help! Printer HP Laserjet 1018... recognized but not working!!??"
date: 2008-07-25
forum: General Help
---

### Post by heavycruz on 2008-07-25
When I connected the printer, everything looked perfect, the Ubuntu 8.04 recognized it as what it is... so no issues with the driver. But, when I ask it to print something, nothing happens... i mean, it sends the job to the printer, I have the icon of the printer on the top right for some seconds... and it says processing... and then the icon disappears... but the machine (laserjet) doesn't even reacted....

Then I tried [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)... those command lines... not helpful neither... I think that i just add the same driver again...
I need your help, please, help me... THANK YOU!!!

---

### Post by funkydan2 on 2008-07-27
Have you examined the logs in '/var/log/cups/'?

---

### Post by editrix on 2008-07-28
Are you in the printer group? Not sure how you do this in Gnome, but there should be something for Users and Groups. Make sure you're in there.

In fact, while you're there, add yourself to **all** the groups. It won't  hurt.

---

### Post by luiska on 2008-08-17
Hi

Same printer and same problem. Got the test printed just now. I typed 
 sudo hp-setup 
on the command line. Went through the questions and I printed the test page from the printer manager.

There seems to be a graphical front end too but it was rather straight forward.

Hope it helps.
Louis

---

### Post by edemark on 2008-08-18
Thanks it worked for me.

Great hint

---

### Post by mack27 on 2008-08-18
> **luiska said:**
> Hi

Same printer and same problem. Got the test printed just now. I typed 
 sudo hp-setup 
on the command line. Went through the questions and I printed the test page from the printer manager.

There seems to be a graphical front end too but it was rather straight forward.

Hope it helps.
Louis

Had exact same problem with HP LaserJet 1020 and it worked for me as well. Thanks !!!:)

---

