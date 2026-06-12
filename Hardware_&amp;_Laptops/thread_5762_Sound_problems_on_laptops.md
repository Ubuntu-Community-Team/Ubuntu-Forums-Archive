---
title: "Sound problems on laptops"
date: 2004-11-22
forum: Hardware &amp; Laptops
---

### Post by Toadstool on 2004-11-22
Ubuntu is a really good distribution but the sound hardly works with it on my laptop   ](*,) 

When I first installed Ubuntu, the sound did not work at all, so I had to google a little and I found that it could be due to problems with acpi. I therefore put "pci=noacpi" in my grub config file to disable it. With this done, I restarted my computer : sound card detected but when Gnome starts the beginning sound loops endlessly until I mute the sound with th volume control panel.

Any idea ?

---

### Post by spirospr on 2004-11-25
Did you test the option of "acpi_irq_isa=7" . I use this during boot up and everything works fine. Maybe you should give it a try.

---

