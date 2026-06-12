---
title: "Open Office Org ate my printer!"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by Mr*Wiggy on 2006-11-17
I finally got to grips with Open Office.Org and sent a document to my local printer (HP Deskjet 960C) The printer didn't respond, I tried all the obvious stuff, checked all the settings. restarted the printer - nothing! But the printer worked perfectly before this. I've printed out emails, pictures, web pages and even the 80 page Ubuntu user guide with no problem at all. Now it doesn't print anything with Ubuntu but works fine with XP.
What's gone wrong? :-? 

Eric

---

### Post by hardyn on 2006-11-17
I assume you have set it up in ubuntu? system > printing > add printer?

what printer?

you say you have printed with it before, under ubuntu, or under xp?

mo - info please...

---

### Post by Mr*Wiggy on 2006-11-17
> **hardyn said:**
> I assume you have set it up in ubuntu? system > printing > add printer?

Yes, But it's not detected automatically now. I had to set it up manually. It shows up in the printer dialog window and I set it to default. Print jobs are spooling and appear in the queue.

what printer?

HP Deskjet 960C - normally well supported in Ubuntu/Linux

you say you have printed with it before, under ubuntu, or under xp?

XP and Ubuntu.

mo - info please...

When I installed Ubuntu Edgy 6.10 the printer was automatically configured and worked perfectly until I tried OO.o.2. 

I did install some updates yesterday - I think it was Xwindow stuff. Is there a log for this?, if so I'll check it out.

TIA

Eric

---

### Post by Mr*Wiggy on 2006-11-18
OK! I fixed it now.  After going through Synaptic and playing with various packages associated with the printing system.  I discover that HPLIP needs QT3 which was removed sometime recently - don't know why.  Anyway I reinstall QT3 and every thing's fine now. :mrgreen: 

Eric

---

