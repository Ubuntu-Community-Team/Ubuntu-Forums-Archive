---
title: "RAM purchase question"
date: 2015-02-15
forum: Hardware
---

### Post by Teethdude on 2015-02-15
Hello. I want to purchase RAM for my server, but I'm not exactly sure if this will be compatible. 
Here's a snippet from sudo dmidecode | grep -A 15 Memory
```
Physical Memory Array    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: Multi-bit ECC
    Maximum Capacity: 65024 MB
    Error Information Handle: Not Provided
    Number Of Devices: 12


Handle 0x004B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x004A
    Error Information Handle: Not Provided
    Total Width: 72 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: 1
    Locator: DIMM 1
    Bank Locator: Bank 1
    Type: DDR2
    Type Detail: Synchronous
    Speed: 266 MHz
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified



```
The RAM in question is 2GB PC2-6400 DDR2-800MHz 240-Pin DIMM ECC Fully Buffered. Will there be any issues?

---

### Post by Yellow Pasque on 2015-02-15
The RAM you have now looks like DDR2-533 (pc2 4200), so the new module would only run at that speed. More information on the server (model or motherboard model) might be helpful.

---

### Post by weatherman2 on 2015-02-15
I have seen motherboards that cannot run both PC2-4200 and PC2-6400 RAM at same time.  It's possible it would slow the PC2-6400 RAM down to PC2-4200, but it may not work at all.  Better chance if you are only one step away (PC2-4200 and PC2-5300).  With server ECC RAM, I'd probably try to find another stick of PC2-4200 or just upgrade all the RAM to a higher speed, if you can make sure that speed of RAM is supported in your motherboard.

Please remember to TEST your RAM after you've installed it, with Memtest.  Just because your RAM will POST and even boot an OS doesn't mean it is compatible with the motherboard.  The RAM may sort of work but have many errors.  Perhaps ECC RAM would not let you get that far, though.

---

### Post by Teethdude on 2015-02-18
Ok. I'll likely purchase it. Even if i need to buy all nee ram, I will. I just want to know if it will work. If it doesn't, well I'll need to do better research.

---

### Post by tgalati4 on 2015-02-18
Ask the server manufacturer for qualified RAM sticks.  Understand that servers tend to have very specific voltage, timing, and front-side-bus speed requirements.  Add to that the tight specifications of the Southbridge chipset that runs the RAM.  Then you need to consider the BIOS and it's flexibility for adjusting CAS timing for mismatched RAM sticks.  I agree with weatherman2 and buy a complete set of matched RAM for the final, desired RAM amount.  Mixing RAM can cause subtle issues that don't become apparent until your system is stressed.

Regardless, run memtest for 30 complete cycles and use a vendor with a return policy if you do have problems.

---

### Post by mastablasta on 2015-02-19
also depending on your server type and usage you might want to look into ECC ram.

---

### Post by Teethdude on 2015-02-19
Thank you all. I will take this all into consideration.

---

