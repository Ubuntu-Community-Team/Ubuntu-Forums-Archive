---
title: "Beryl in my Sis Card?"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by artir on 2007-01-31
I have this SiS integrated graphic card: 
 Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

And i downloaded the last driver from the sis page. Is a file called sis_drv.o-410
I think i will be able to use 3D with that driver, so i want to use it. What i need to do?

---

### Post by Jeremy23 on 2007-02-01
As far as I know, no SiS video chipsets support decent, if any, 3D acceleration in Linux. It's not your fault, it's SiS' fault for not providing the technical specifications to the open-source community.

I think that driver would be unrelated to 3D acceleration. Even if it did work, SiS chipsets are so bad performance-wise it would most definately be not worth running Beryl on it.

I have a computer with a SiS chipset. In Windows XP, only Direct3D, not OpenGL, was supported. Under Linux, I had no hardware acceleration at all.

---

### Post by g8m on 2007-02-02
I have a sis card. Xorg is configured to use sis. If I enter glxinfo in a terminal, X crashes and I have to logon again....

ls /usr/lib/xorg/modules/drivers/sis_drv.so  --> this drivers comes default with edgy

and in /etc/X11/xorg.conf, section device, driver "sis"

---

### Post by Jeremy23 on 2007-02-02
> **g8m said:**
> I have a sis card. Xorg is configured to use sis. If I enter glxinfo in a terminal, X crashes and I have to logon again....

Erk, that's pretty nasty. :(
I had a similar problem when I was running the 9629 NVIDIA drivers with starting Quake III-based games where X would crash. However, Beryl and the lot still worked. Updating to version 9631 fixed it.

---

