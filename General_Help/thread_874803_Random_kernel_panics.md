---
title: "Random kernel panics"
date: 2008-07-30
forum: General Help
---

### Post by cbonner on 2008-07-30
I have a system with an MSI MS-7366 motherboard, 2GB RAM and 2x 250GB SATA drives.

I currently have Ubuntu server installed, but it seems to crash quite randomly with kernel panics. Usually 'Kernel panic - not syncing', see screenshots.

[IMG]http://mail.kingrichardschool.net/kp1.jpg[/IMG]

[IMG]http://mail.kingrichardschool.net/kp2.jpg[/IMG]

I have tried the following to resolve the problem, but no success...

Memtest (10 passes, fine)
Change HDD's
Upgrading
Reseating memory
Kernel options such as, nosmp, noapic, noacpi
Other distros

Sometime it will crash straight away, or go for days before crashing.

Does anyone know why this might be happening?

Thanks.

---

### Post by jward3010 on 2008-08-19
What Ubuntu server are you running, I assume its 8.04.

---

### Post by cbonner on 2008-08-27
Yeah sorry, Ubuntu Server 8.04.1

---

### Post by Crafty Kisses on 2008-08-27
If you're using a Mac or something to that nature then defective or incompatible RAM are the most frequent causes of kernel panics. Despite being a highly-reliable product, RAM can fail.

---

### Post by bl00dninja on 2008-09-04
I have a similar issue, my kernel crashes when i try to put the machine in hibernate mode. If I click the option to put the machine is hibernate mode i get the same error

EIP [<C02BC946>] tcf-destroy+0x6/0x20 SS:ESP 0068:f5085e7c

Kernel panic - not syncing Fatal exception in interrupt

Please advice if there are any special updates or patches out there cuz my machine is uptodate.

Thanks

---

### Post by cbonner on 2008-09-10
Have had XP running on it for a while, but it also does it too. Must be a memory problem or something.

Thanks for the advice.

---

