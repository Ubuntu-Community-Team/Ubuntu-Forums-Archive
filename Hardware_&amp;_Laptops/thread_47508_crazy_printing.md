---
title: "crazy printing"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by kimes on 2005-07-08
I'm using HP Deskjet 3650.. and maybe cupsd something..

Everything seems to be fine.. but sometimes..
My printer doesn't response at all after doing some stuff with printer.
When It's hang up, what should I check?

I'm usually doing restart cupsd..
Am I doing right?

And if I cancel some jobs during printing.. It just stop.. without finishing the page printing.. so make me can not do the other jobs.. 
I have to turn off and printer again..
Any Ideas?

---

### Post by David Haas on 2005-07-09
Hi kimes--What PPD file did you install for the Deskjet 3650? I see that Ubuntu 5.04 has one for this printer. It's HP-DeskJet_3650-hpijs.ppd.gz
at /usr/share/cups/model/foomatic-ppds/HP. 
David

---

### Post by kimes on 2005-07-10
[QUOTE=David Haas]Hi kimes--What PPD file did you install for the Deskjet 3650? I see that Ubuntu 5.04 has one for this printer. It's HP-DeskJet_3650-hpijs.ppd.gz
at /usr/share/cups/model/foomatic-ppds/HP. 
David[/QUOTE]
 Ye.. I installed that one..
but still the problems exits.. Thanks anyway..

---

### Post by David Haas on 2005-07-11
kimes--Have a look at your error_log messages the next time the printer misbehaves. Go to /var/log/cups and in the cups directory do a less command (less error_log) to show the error_log messages. Clues may be here.
David

---

