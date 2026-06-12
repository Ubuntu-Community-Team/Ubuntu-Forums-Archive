---
title: "Sudden Speed Problems, likely hardware overheating"
date: 2013-09-10
forum: Hardware
---

### Post by vincent-p on 2013-09-10
Hello,
my laptop suddenly got very slow without any system changes made for a long time.
It is running Ubuntu 12.04 on it (the only OS I use) and it is so slow that it often cannot load web pages before timing out.
I checked the CPU load and memory and they are normal so I concluded: it's probably the hardware

I used the software **Psensor** to check for the hardware temperatures and the result is scaring:
[http://imageshack.us/photo/my-images/199/yfx.png/](http://imageshack.us/photo/my-images/199/yfx.png/)

The temperature of 3 "temp1" sensors are > 70°C, a fourth sensor says 6280°C, which cannot be true.

1) For what exactly do those sensors stand for? Is it dangerous to use the computer one more time to get transfer some files for backup?
2) Should I do something to repair it myself? The laptop still has warranty and I do not want to lose it.

Please help!

---

### Post by tgalati4 on 2013-09-10
You would have to do some research as to where exactly the sensors are located, but typically one is inside the CPU, one on the motherboard under the CPU, one near the power circuitry, one on the graphics chip.

What is the make and model of the laptop so I can avoid buying it.

Sometimes laptops are assembled with too much heat paste which interferes with heat transfer, sometimes too little, sometimes it drys out after several years.  More likely is the heat sink has loosened up. Have you dropped the laptop?  A loose heatsink won't take the heat away so the chip just sizzles.

I would take the hard disk out and put it in a USB enclosure and back up the data to a Linux desktop machine.

Running your machine, even for a few minutes can cause heat stress which will delaminate the motherboard, making it less reliable than the operating system that you don't use.

Wipe your data from the machine after backing it up, and send it in for service.  You don't have many options at this point.

---

### Post by mörgæs on 2013-09-11
If it were old I would take the fan and heat sink apart and clean it from dust, but as it is still is under guarantee it's better to send it back to the shop.

---

