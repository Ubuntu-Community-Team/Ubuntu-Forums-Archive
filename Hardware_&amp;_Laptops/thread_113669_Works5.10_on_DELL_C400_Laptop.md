---
title: "Works:5.10 on DELL C400 Laptop"
date: 2006-01-06
forum: Hardware &amp; Laptops
---

### Post by celem on 2006-01-06
My DELL C400 laptop works well with 5.10. I haven't found anything that doesn't work. I even got a cheap wiifi PCMCIA card working with ndiswrapper. It took two tries. The first time I used the XP driver that came with the card. It slowed the laptop to a crawl. Then I used the (10ec:8180) driver referenced by the Ubuntu Wiki on ndiswrapper and it works great.

---

### Post by Kannisto on 2006-01-08
Works great with mine too. Few things still bother: suspend only works with "standby" option, after hibernate avi videos hang the system (at least with totem-xine). This is a real showstopper on the road. And few glitches when switching terminals and in returning from suspend/hibernate. 
I'm using kernel parametres nolapic and acpi_irq_isa=7(had option vga=771, but that kills dri support or something, glxgears around 250 with that normally about 550)

Please writeout the tweaks you used to get this thing working perfectly.

---

