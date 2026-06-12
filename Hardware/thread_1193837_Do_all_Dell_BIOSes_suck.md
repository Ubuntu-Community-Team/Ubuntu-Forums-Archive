---
title: "Do all Dell BIOSes suck?"
date: 2009-06-22
forum: Hardware
---

### Post by matthanielcm on 2009-06-22
I am working on my Dell Dimension E521 and am getting quite frustrated with Dell. When I first plug in my computer, it turns on and reports a "Low Battery" (even though I've replaced it with a brand new one). So, I go into the BIOS to clear the logs. Well, when I go into the BIOS to do anything, when it reboots, the BIOS initial loader seems to get stuck at about less than 50%. When this happens, I have to pull out and push in the battery again (in which then I lose all the work I did on the BIOS). When I don't touch the BIOS, the computer seems to boot fine (with the "Low Battery" error of course, and another error stating the configuration isn't right). I've got the latest firmware that I know of, 1.1.11. Anybody know a way around these problems? Thanks.

---

### Post by tgalati4 on 2009-06-22
Did you actually measure the voltage of the new battery under load?  If 2.8 volts then it might trigger the alarm.  Measure in-place while booting.

You could have a mild motherboard short causing battery drain.  How old is the machine?  Cheap power supplies are a frequent Dell problem.  Melamine in the cat food syndrome.

---

### Post by AoSteve on 2009-06-22
Dell BIOS's are made to be all but fool-proof.  I'd test the battery like tgalati4 said.  It could be showing a low battery, because the battery isn't up to par.   I know I've bought mobo batteries that had been on the shelf long enough to lose the power to be capable of what the mobo wants.  Try a different battery that you know works, if possible.  I have like 3 batteries here that I know are good, so I have a source to use to check if my battery is dead or there is something else failing.

---

### Post by mantelo on 2009-06-30
I have the same system.

Check if you have any usb storage connected. I had trouble before until I disconnected my micro sd thumbdrive.


And yes, most Dell BIOS suck. You could always install "[coreboot]("http://www.coreboot.org/Welcome_to_coreboot")" (if you are brave enough)

---

