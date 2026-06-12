---
title: "Expresscard hardware refresh."
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by Killerah on 2007-06-22
Hey guys, I just got a new laptop and I've got an e-sata expresscard for my external hard drive which all works great! The only thing is that if I don't have it plugged in and turned on at boot up it doesn't work. So I figured there had to be a way to make my computer refresh it's expresscard drivers or something so that I don't have to reboot to get it to work. Does anyone know how I might be able to do this? That would be super helpful and life-changing.

Thanks
Nate

---

### Post by Killerah on 2007-06-27
Anybody know how to do this? Anybody? There's gotta be some way to restart certian devices without restarting my whole computer!

---

### Post by Drizzt321 on 2007-08-05
Well, it depends. Try loading the pciehp drivers (pci express hotplug), and if that doesn't work/won't load try the acpiphp drivers. My laptop, Inspiron e1505/6400 has a BIOS that doesn't implement the proper hooks to do PCI-Express hotplug the right way (_OSC method). The way XP does it, is basically watch the bus to see if it throws up a specific kind of error which signifies that a new card has been plugged in.

Now, Vista is a bit different. Supposedly it uses the _OSC method which is the proper way, but I suspect that they kept the old XP way of doing things as a backup since not all laptop venders, or even slightly older laptops, implement the correct way. Read the following whitepaper from MS for more information. Its actually quite good.

[http://www.microsoft.com/whdc/system/bus/pci/BIOS_HotPlugPCIe.mspx](http://www.microsoft.com/whdc/system/bus/pci/BIOS_HotPlugPCIe.mspx)

--Aaron

---

### Post by abrichr on 2007-09-28
I'm having the exact same problem.  I have a Compal HEL80 laptop.

It seems to me that it's the motherboard that's not detecting it when it's hotplugged, since if I plug it in while the boot process is only at Grub, Ubuntu still doesn't detect it.  If I boot up with the device plugged in before I power on, then I can see the external hard drive in /dev/disk/by-id.

 I wasn't able to find any information on how to restart pciehp or the other drivers.

Any ideas on this?

---

