---
title: "Disc boot issues"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by Javok on 2008-12-28
Several weeks ago, I tried to put Ubuntu 8.10 on my desktop computer. I put in the boot disc, but no matter which option I chose, whether to install Ubuntu, boot from disc, check disc from errors and so on, the same thing would happen; it would show the Ubuntu splash screen for a while and then dump me into Busy Box. I'm not that experienced with Linux, so I don't know what to do aboout this or how to use Busy Box. When I try using the disc on my laptop, however, it works perfectly. My desktop uses two separate 160 GB SATA drives that aren't using RAID. One has Vista on it, and the other I bought to put Ubuntu on.

---

### Post by caljohnsmith on 2008-12-31
Sometimes you can circumvent booting problems like that by adding certain kernel boot options when you boot the Live CD; when you boot the Live CD and get the main menu, press "F6", and then try adding at the end of the kernel line the following:
```
acpi=off
```
Then select the "try Ubuntu without making changes" option again, and if that doesn't work to boot Ubuntu, you could try adding all of the following options:
```
noapic nolapic pci=noacpi irqpoll ide=nodma nopcmcia pci=nomsi
```
I think some of them may be redundant, but I don't remember offhand, so it shouldn't hurt to just add them all. Let me know if that gets you any further booting, or what exactly happens.

---

### Post by Javok on 2009-01-07
Thank you for the suggestion, but trying all of them just did the same thing of showing the ubuntu loading screen, and then BusyBox. 
 Can you suggest something else that might persuade my apparently Ubuntu-resistant to boot?

---

### Post by MacQ32 on 2009-01-08
Well, I'm a noob myself but I finally successfully installed ubuntu 8.10.  I was getting all kinds of partition errors and could not get around them.  Then I installed via alternate CD in Text Mode and it worked with no problems at all.  Again, dont really know what I'm talking about but I avoided the errors I was seeing this way.  Good luck!

---

