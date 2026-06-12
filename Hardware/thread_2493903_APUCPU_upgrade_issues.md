---
title: "APU/CPU upgrade issues"
date: 2023-12-28
forum: Hardware
---

### Post by him610 on 2023-12-28
System (Xubuntu 22.04.3) has operated with no problems since original build date (4+ years), 500GB NVME boot drive, 16GB (2 * 8GB)RAM.

What I wanted to accomplish was to remove AMD Ryzen 5 2600 along with Nvidia GK104 (Geforce GTX 760) from a homebuilt  AsRock B450m/ac MB and replace it with an AMD Ryzen 5 5600G (Integrated Graphics.) 

First time I have tried an APU/CPU upgrade; not as simple as I first thought.

Steps -
Performed a backup of all important data, etc.
Removed AMD APU Ryzen 5 2600 and GFX Nvidia GK104 (Geforce GTX 760) from B450m/ac
Installed AMD APU Ryzen 5 5600G and APU cooling fan.
Cleared CMOS jumper (CLRMOS1)
With only necessary power input, HDMI Video connected to B450m , and keyboard/mouse.
Applied power
Chassis fans and APU fan begin spinning.
Display flashes briefly, a few seconds later message appears on monitor," HDMI/MNL No signal"
After a few more seconds, fans spin down then the system attempts to reboot - same thing happens. 
After three repetitions, I removed power from system to seek advice.

Bios Version of B450M currently is P1.50. AsRock recommends BIOS version P2.60 for Cezanne APU (Ryzen 5 5600G).

? Should I have updated BIOS as preliminary procedure?
? Did I leave something out?

? Any suggestions?

@TheFu - Patiently awaiting your input since you do this sort of thing quite often.

Thanks in advance.

---

### Post by Yellow Pasque on 2023-12-28
> **him610 said:**
> Bios Version of B450M currently is P1.50. AsRock recommends BIOS version P2.60 for Cezanne APU (Ryzen 5 5600G).

? Should I have updated BIOS as preliminary procedure?

Yes, you should have updated the BIOS before you took the old CPU out. Support for Ryzen 5000 series was not added until BIOS version 2.30
Rookie mistake...

---

### Post by him610 on 2023-12-31
@Yellow Pasque - Thanks for the advice; the fix worked.

I had also contacted AsRock Support; here is what they sent.
> Dear Hugh M...,

Thank you for contacting ASRock.


B450M/ac supports R5 5600G since BIOS 2.30.

We recommend installing R5 2600 CPU to update the latest BIOS 8.01 for better compatibility.

Link: [https://www.asrock.com/MB/AMD/B450Mac/index.asp#BIOS](https://www.asrock.com/MB/AMD/B450Mac/index.asp#BIOS)

BIOS Download Link: [https://download.asrock.com/BIOS/AM4/B450Mac(8.01)ROM.zip](https://download.asrock.com/BIOS/AM4/B450Mac(8.01)ROM.zip)

Update Method: [https://www.asrock.com/support/BIOSIG.asp?cat=BIOS10](https://www.asrock.com/support/BIOSIG.asp?cat=BIOS10)


After completing the BIOS update, please swap the CPU to R5 5600G to use.


Thank you

Kindest regards,

ASRock TSD
I shall mark this as *Solved.*

---

