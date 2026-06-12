---
title: "Acer 3680 slow boot when lid is closed"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by MaximusTG on 2007-10-05
Yesterday I bought an external monitor for use with my Acer 3680 (running Gutsy Beta). However, I now discovered that my laptop boots incredibly slow when the lid is closed.. I have the splash screen turned off, and when I boot with the lid closed it takes forever for all the [OK]'s to appear. If I slightly lift the lid (so the switch detecting if it is open or closed thinks its open) the [OK]'s appear much faster..

Any suggestions?

---

### Post by darrenrxm on 2007-10-05
I have the same laptop as you do. And the problem im having is that it won't come out of standby. Or at least the screen won't turn on. But everything seems to work fine on the old version of ubuntu. Oh yeah sound's not working for me either. But it is beta software so what do you expect.

---

### Post by cmnorton on 2007-10-05
My TravelMate 630 has to boot with the lid wide-open (or at least half-way), or it will not boot. BTW, bios is set to do nothing if the lid is closed.

---

### Post by ljonesj on 2007-10-05
ok weird i have the same laptop and my sound is deteced with the beta of 7.10 i know i have to add some volume controls to mine to get i to work but i have not tried the screen yet

---

### Post by MaximusTG on 2007-10-06
So you all have an acer 3680, and don't have the same problem?
I have BIOS version 1.3211, which do you have? There is a newer version available, but I don't want to take a risk flashing the bios, when it won't do any good.

I had another idea, since the problem is probably caused by the lid switch being closed during boot (some ACPI problem?) is it possible to just remove the lid switch entirely (in the configuration of course, not the actual switch :P ) or to always set it to on?

---

### Post by ljonesj on 2007-10-06
mines like 1.3505 i think

---

### Post by MaximusTG on 2007-10-06
Hmm, so it probably isn't bios related then. 
It is ACPI related however, if I turn off ACPI, the problem is gone (though then my wireless card doesn't turn on, and the battery meter doesn't work). It seems ACPI is pausing my harddrive during boot if the lid switch is pressed..

---

### Post by MaximusTG on 2007-10-07
After some extensive google searching, I found this:

[http://mindspill.net/computing/linux-notes/acpi/continuous-acpi-lid-events-and-100-cpu-usage.html](http://mindspill.net/computing/linux-notes/acpi/continuous-acpi-lid-events-and-100-cpu-usage.html)

I didn't have the 100% CPU usage problem, but the lid switch was generating continuous  events. Disabling all actions for the event didn't solve my boot problem. So I decided to try the tip to recompile the kernel without lid switch support. Booting that kernel, the lid switch isn't recognized anymore. But it still causes the problem.. 

So to summarize:

Laptop harddrive (or all activity for that matter) seems to pause when lid switch is pressed during boot

Acpi =off solves it, but is isn't a solution for me

removing lid switch support doesn't help.

---

