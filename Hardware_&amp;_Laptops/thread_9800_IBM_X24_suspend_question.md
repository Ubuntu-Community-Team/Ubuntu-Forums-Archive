---
title: "IBM X24 suspend question"
date: 2005-01-01
forum: Hardware &amp; Laptops
---

### Post by angrylittleman on 2005-01-01
I have an ibm X24 and an Ornioco gold pcmcia card which works pretty well with Ubuntu.  I am using APM with Kernel 686, as ACPI does not seem to work to well.  I can suspend my laptop, but when i bring it back, I get no sound or USB hotplug support (I sometimes use an mini usb mouse.  Restarting the laptop makes sound and USB hotplug support work fine.  I have to remove the Ornioco card before suspending or it will not work when the computer returns to an active state.

To get the laptop to suspend and turn on ACPI, I added "apm=on acpi=off nolapic" to my kernel options.  I added apm to /etc/modules.  shpchp and pciehp were added to /ect/hotplug/blacklist.

When I boot I get PCI: address space collision on region 7 of bridge 0000:00:1f.0 [1000:107f].  (I didn't get this with kernel-386, but after upgrading to kernel-686 and addding the same kernel options, it began showing up.)  Messing the IRQ settings does nothing.  

I would just like have the laptop suspend and have sound and USB work when it comes back.  Any suggestions, comments or anything?  
  
 :D

---

### Post by angrylittleman on 2005-01-04
Hm, anyone?  I am pretty sure that I need a script to restart my soundcard......Anyone help me out with that?

thanks.

ALM

---

