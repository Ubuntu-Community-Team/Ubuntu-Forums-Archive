---
title: "RAM not fully detected"
date: 2014-12-15
forum: Hardware
---

### Post by roachteo on 2014-12-15
Hi,
I've a Dell Inspiron with 6gb of RAM.
It's correctly installed and it works on Windows8.
I installed Ubuntu 14.04 64bit and only 4.4gb are detected.
I cannot in any way detect the other two.

I have no idea of the reason..anyone can help me?
Someone in the same situation or had a similar problem?

Thanks!

Here's the output of dmidecode -t memory:
```
SMBIOS 2.7 present.

Handle 0x0005, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2


Handle 0x0006, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0005
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: System Board Memory
    Bank Locator: Not Specified
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1600 MHz
    Manufacturer: Hynix/Hyundai
    Serial Number: 00000000
    Asset Tag: 9876543210
    Part Number: HMT851S6AMR6R-PB  
    Rank: Unknown
    Configured Clock Speed: 1600 MHz


Handle 0x0007, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0005
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: None
    Locator: System Board Memory
    Bank Locator: Not Specified
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1600 MHz
    Manufacturer: Hynix/Hyundai
    Serial Number: 00000000
    Asset Tag: 9876543210
    Part Number: HMT425S6AFR6A-PB  
    Rank: Unknown
    Configured Clock Speed: 1600 MHz
```

---

### Post by lukeiamyourfather on 2014-12-15
Looks to me like all 6 GB are detected. What makes you think not all of the memory has been detected?

---

### Post by roachteo on 2014-12-15
System settings shows me only 4.4gb. Also free -m shows 4497 as total.
Or MemTotal tell me 4605924 kB..

---

### Post by MartyBuntu on 2014-12-15
Memory reserved for graphics.

This is a laptop, right?

---

### Post by houstonbofh on 2014-12-15
What are you using for video?  Could it be stealing a gig and a half of memory?

---

### Post by roachteo on 2014-12-15
Yes. It's a Dell laptop.
I have an Intel integrated graphic card.
Is there a way to decide how much RAM reserve? I don't use games or video-editing programs.. 512mb is more than sufficient..

---

### Post by lukeiamyourfather on 2014-12-15
There's usually an option in the BIOS/UEFI for how much memory to dedicate to graphics.

---

### Post by roachteo on 2014-12-16
It seems that nothing in BIOS to do that. But no problem. I'll keep as is. Thanks all!

---

### Post by Yellow Pasque on 2014-12-16
> **lukeiamyourfather said:**
> There's usually an option in the BIOS/UEFI for how much memory to dedicate to graphics.

Intel has allocated VRAM dynamically for a while (i.e. no switch it BIOS because it's allocated as needed). I can't remember if AMD does the same, but I wouldn't doubt it.

---

