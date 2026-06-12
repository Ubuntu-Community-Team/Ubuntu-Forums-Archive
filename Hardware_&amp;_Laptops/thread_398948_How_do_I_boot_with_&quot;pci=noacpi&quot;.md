---
title: "How do I boot with &quot;pci=noacpi&quot;?"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by kundalinikat on 2007-04-01
Using Kubuntu Edgy with an Nvidia Geforce FxX 5200. Used the Envy script to install Nvidia drivers. 

I decided to stick with the old legacy because with the new legacy or the latest driver, my X session doesn't start and I get the message that I should use the "pci=noacpi" option. How do I do that? is it in xorg.conf, or grub, or what?

Thanks for your support.

---

### Post by kerry_s on 2007-04-01
Add it to the end of the grub boot line.

kdesu kwrite /boot/grub/menu.lst

Example:
kernel		/boot/vmlinuz-2.6.20-13-386 root=UUID=785d88e5-4a57-4d97-a852-85a73bcde479 ro vga=791 pci=noacpi 

You also might want to add it to the end of defoptions in case of kernel updates->
# defoptions=vga=791pci=noacpi

PS: yours won't look exactly like mine, i'm running a custom install, so i've deleted/added to my boot line. :)

---

### Post by kundalinikat on 2007-04-02
awesome, thanks!

---

