---
title: "Soundcard IRQ=0 with acpi=off"
date: 2010-04-06
forum: Hardware
---

### Post by unrealone on 2010-04-06
Hello,
I have a problem with an old ASUS laptop (I thing it's A3L) with XUNBUNTU 9.10.
Without boot parameter acpi=off, graphics freezes (graphics card is Intel 82852/855GM). I can still move mouse, but I can't do anything else. 

When I set acpi=off, IRQ 0 is assigned to a soundcard and dmseg writes a line "unable to grab IRQ 0". (IRQ 17 is assigned to a  soundcard in "without acpi=off boot"). The soundcard is Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03).

Does anybody know a way around this trap?

Thank you 
On.

---

### Post by unrealone on 2010-04-07
Thank you for your request
The system is new installed. I have two mouses (USB and integrated Touchpad). If I restart without USB mouse, graphics keeps freezing. 

After freeze I can logon by SSH, but dmesg writes nothing. Is there any other command to diagnose a freezing problem?

> **jobran said:**
> hello,
        i think you should format your system and reinstall the mouse driver than check it is work or not if it is not working than saw this to a hardware engineer.
thanks!!
________________
  [Bed   Pillow]("http://www.shopdownlite.com/pillowspillowforms-c-22.html")

---

