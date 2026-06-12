---
title: "I need The PCI Device Of My Laptop"
date: 2008-06-10
forum: Hardware
---

### Post by Uchiha_madara on 2008-06-10
Hi Every one ,   I'm new remember here
I transfer all my Works, My businesses and my Projects from Microsoft Windows to Ubuntu, I have worked with Ubuntu7.10 Gusty
:guitar::popcorn:
now I'm Working with Ubuntu Hardy and i need The Configuration
of the PCI Device That make the Laptop reads the Sound card and the  
Modem ....................... 
My Laptop is Toshiba Satellite L30-115

Please Help me:confused:

---

### Post by NikoC on 2008-06-10
Hmmz not really sure if I completely understand your problem, but typing the following in a terminal gets you a list of all pci devices:

lspci



Cheers.

---

### Post by Uchiha_madara on 2008-06-11
..... I need The Drivers

of My Laptop 

.......

toshiba satellite L30-115

i'll try your suggestion thanks

---

### Post by stchman on 2008-06-11
> **Uchiha_madara said:**
> Hi Every one ,   I'm new remember here
I transfer all my Works, My businesses and my Projects from Microsoft Windows to Ubuntu, I have worked with Ubuntu7.10 Gusty
:guitar::popcorn:
now I'm Working with Ubuntu Hardy and i need The Configuration
of the PCI Device That make the Laptop reads the Sound card and the  
Modem ....................... 
My Laptop is Toshiba Satellite L30-115

Please Help me:confused:

Yes

```
lspci
```

will be the command to list the devices that are on the PCI bus.

I will warn you that Linux has compatibility problems with winmodems in laptops.  I have never used a modem under Linux so I cannot comment on anything other than I have heard.

---

