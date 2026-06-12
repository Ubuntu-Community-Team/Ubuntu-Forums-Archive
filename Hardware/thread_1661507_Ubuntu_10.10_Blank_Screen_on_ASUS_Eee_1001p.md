---
title: "Ubuntu 10.10 Blank Screen on ASUS Eee 1001p"
date: 2011-01-06
forum: Hardware
---

### Post by Hunterssong19114 on 2011-01-06
I recently installed Ubuntu 10.10 Desktop Edition solely on my Asus Eee PC 1001P. The installation went well and everything looked fine. But every time I try to boot it makes the start up sound, but the screen is just black.. It looks like it's off. So I tried plugging it into an external display and it worked perfectly. It appeared as though everything was running normally. I just can't get the laptop display to work. Can anyone help me out with this?

---

### Post by edcrumly on 2011-03-12
> **Hunterssong19114 said:**
> I recently installed Ubuntu 10.10 Desktop Edition solely on my Asus Eee PC 1001P. The installation went well and everything looked fine. But every time I try to boot it makes the start up sound, but the screen is just black.. It looks like it's off. So I tried plugging it into an external display and it worked perfectly. It appeared as though everything was running normally. I just can't get the laptop display to work. Can anyone help me out with this?

The Fn key with the brightness keys (Fn + F5 , F6) , should lighten things up. The problem is the acpi_osi needs to be added to your grub file. Well , that's one solution, and I've tried an acpi.sh script one, and adding various files  and then grub fix as well. Search the forum for "asus acpi brightness " ed

---

