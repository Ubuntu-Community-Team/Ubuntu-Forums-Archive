---
title: "flashing BIOS with flashrom"
date: 2021-01-17
forum: Hardware
---

### Post by c@ssie on 2021-01-17
I' m trying to flash the BIOS on my ga-x79-ud3 motherboard using flashrom.  But when I issue the command ```
sudo flashrom --programmer internal 
``` I get multiple responses: ```
Found Macronix flash chip "MX25L6405" (8192 kB, SPI) mapped at physical address 0x00000000ff800000.
Found Macronix flash chip "MX25L6405D" (8192 kB, SPI) mapped at physical address 0x00000000ff800000.
Found Macronix flash chip "MX25L6406E/MX25L6408E" (8192 kB, SPI) mapped at physical address 0x00000000ff800000.
Found Macronix flash chip "MX25L6436E/MX25L6445E/MX25L6465E/MX25L6473E/MX25L6473F" (8192 kB, SPI) mapped at physical address 0x00000000ff800000.
Multiple flash chip definitions match the detected chip(s): "MX25L6405", "MX25L6405D", "MX25L6406E/MX25L6408E", "MX25L6436E/MX25L6445E/MX25L6465E/MX25L6473E/MX25L6473F"
Please specify which chip definition to use with the -c <chipname> option.

```
Which chip definition do I want to use?

---

