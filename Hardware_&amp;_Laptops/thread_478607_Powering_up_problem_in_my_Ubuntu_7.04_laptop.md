---
title: "Powering up problem in my Ubuntu 7.04 laptop"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by sra136 on 2007-06-19
I recently noticed that my laptop does not "power" back up when the ac charger is not connected to the laptop.  You just hear the fans turning on.  However, when I connect the AC charger, it powers up and normally resumes from Hibernate/Shutdown.  Anyone know why?

---

### Post by CrispyFried on 2007-06-19
do you get the BIOS or GRUB screen?  

if not, might be you lost a cell in the battery and theres not enough voltage to run. 

if you do and its just ubuntu that doesnt load it might be a configuration file got whacked.

---

### Post by sra136 on 2007-06-20
Nothing turns on.  None of the LED's.  Only the fans turn on.  When I plug in the AC charger, then it turns on.  It could be the lost cell.  Ubuntu does  show the laptop battery at 41% capacity (poor).  Is there a fix, recalibrate or something.

---

### Post by teryan2006 on 2007-06-20
Sounds more like a hardware issue than an OS or software issue. Probably faulty battery pack.

---

### Post by CrispyFried on 2007-06-20
sounds like the battery is toast. when its running on ac and you pull the plug does it drop dead right away (boot to memtest, not ubuntu,  to try this initially)?

if it does run for a while, boot to ubuntu on ac and look in the battery icon under power history -> voltage history and see if it drops when switching to battery.

there is no way to fix it aside from replacing the battery (if it is a dead cell).

---

### Post by sra136 on 2007-06-20
Its working now.  The battery was not properly placed in.  However, the capacitance is only 41% according to Ubuntu.  Is there anyway to increase that, because batteries do degrade over time.

---

