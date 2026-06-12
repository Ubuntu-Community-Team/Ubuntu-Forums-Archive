---
title: "Advises for Asus P4P800 (Deluxe)"
date: 2005-02-22
forum: Hardware &amp; Laptops
---

### Post by gasparov on 2005-02-22
Hi,
   as with Debian and Mandrake there are no major problems with this mobo,however a few thinks must be done...
I'm a warty user and my firmware is 1019, problems with front panel usb/firewire have been reported so upgrade to that firware if you feel too...
Installation goes smooth, use "linux acpi=ht apm=power_off" to start installation, I don't know if it doesn't work without the "acpi=" and "apm=" but I had problems booting linux without the first option and shutting down it without  the second option happend to the kernel...I installed ubuntu on a sata 160gig hard disk and the boot sector is in the last 20 gigs and still boots...cool
Considering onboard periph. :
- ethernet ok, mine got configured smooth with dhcp (router here)
- audio: recognized as AnalodDevices 1985 as it should be, for 5.1 I suggest downloading gnome-alsamixer and avoid using Volume Control,didn't work for me,be carefull that surround is not muted....
-usb: take off "Legacy Support" from bios, with legacy support usb plugs seems unwired/death ,wiithout legacy everything works ok.One problem is that grub doesn't read my wireless usb keyboard and i need a "backup keyboard" under my desk....
-firewire:seems ok
-I don't use the via controller,just have sata....it works for sure cause you can download drivers from viarena,but i don't know during installation...

Ubuntu seems cool :grin:

---

