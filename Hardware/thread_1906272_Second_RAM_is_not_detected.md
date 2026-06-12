---
title: "Second RAM is not detected"
date: 2012-01-08
forum: Hardware
---

### Post by Shikatsu on 2012-01-08
Greetings EveryOne :D

I just installed ubuntu 11.04 and it's my first experience with Linux so please be patient with me.

I got two separate RAM plugged in my desktop pc, previously i was on windows xp and it detected +1.8g of RAM now when checking System Settings->System Info, i can see only 741.1 mb of memory.

What can i do to get ubuntu to detect all of the available memory? (if you need any additional info please ask)

Thank You In Advance :D

---

### Post by MoreOrLess on 2012-01-08
Check what these commands output:
```
sudo dmidecode -t memory
free -m
```

---

### Post by Shikatsu on 2012-01-09
Thank you MoreOrLess for your reply :)

I'll check it out when i get home from work.

---

### Post by Shikatsu on 2012-01-09
This is what i got:

```

sudo dmidecode -t memory

# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0027, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 4 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x0028, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: Flash Memory
    Error Correction Type: None
    Maximum Capacity: 512 kB
    Error Information Handle: Not Provided
    Number Of Devices: 1

Handle 0x0029, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0027
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: Not Specified
    Type: DDR
    Type Detail: Synchronous
    Speed: 400 MHz (2.5 ns)
    Manufacturer: JEDEC ID:C1 00 00 00 00 00 00 00
    Serial Number: 108C0302
    Asset Tag: Not Specified
    Part Number: 64D64300HU5B

Handle 0x002A, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0027
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 256 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM2
    Bank Locator: Not Specified
    Type: DDR
    Type Detail: Synchronous
    Speed: 400 MHz (2.5 ns)
    Manufacturer: JEDEC ID:CE 00 00 00 00 00 00 00
    Serial Number: BBEF04F3
    Asset Tag: Not Specified
    Part Number: M3 68L3223FTN-CCC

Handle 0x002B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0027
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM3
    Bank Locator: Not Specified
    Type: DDR
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: JEDEC ID:
    Serial Number:  
    Asset Tag: Not Specified
    Part Number:  

Handle 0x002C, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0027
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM4
    Bank Locator: Not Specified
    Type: DDR
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: JEDEC ID:
    Serial Number:  
    Asset Tag: Not Specified
    Part Number:  

Handle 0x002E, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0028
    Error Information Handle: Not Provided
    Total Width: 4 bits
    Data Width: 4 bits
    Size: 512 kB
    Form Factor: Chip
    Set: None
    Locator: SYSTEM ROM
    Bank Locator: Not Specified
    Type: Flash
    Type Detail: Non-Volatile
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

``````

free -m

             total       used       free     shared    buffers     cached
Mem:           741        700         40          0          0        150
-/+ buffers/cache:        548        192
Swap:            0          0          0

```

Note: as you can see i don't have a Swap partition because before installing ubuntu my hard drive is 80G, partitioned to two parts one for my system and the other for my personal data. 
when i was installing ubuntu i couldn't divide my system partition because when i tried to create a new one the wizard was telling me something like your whole hard drive will be formated which i can not do.
so i decided to install ubuntu and then use an utility from the repository to divide my hard drive for the Swap without compromising my data on the other partition and then reinstall ubuntu.

Thank You In Advance :D

---

### Post by MoreOrLess on 2012-01-09
You only have 768MB of RAM. I'm not sure why XP detected 1.8GB or why you're asking this. :?

---

### Post by Shikatsu on 2012-01-10
> **MoreOrLess said:**
> You only have 768MB of RAM. I'm not sure why XP detected 1.8GB or why you're asking this. :?

Because i have two separated RAMs, when i was on XP it really detected 1..8G if you don't believe i will reinstall XP and take a screen shot of my task manager for your ;)

And because i need my extra RAM for extra performance.

Thank You For Trying To Help ;)

---

### Post by varunendra on 2012-01-11
> **Shikatsu said:**
> Because i have two separated RAMs, when i was on XP it really detected 1..8G if you don't believe i will reinstall XP and take a screen shot of my task manager for your ;)
You do have TWO Ram modules:
> **Shikatsu said:**
> ....
Memory Device
....
     Size: [COLOR=Red]**512 MB**[/COLOR]
    Form Factor: DIMM
    Set: None
    Locator: **DIMM1**
    ....
    ....
Handle 0x002A, DMI type 17, 27 bytes
Memory Device
    ....
    ....
    Size: [COLOR=Red]**256 MB**[/COLOR]
    Form Factor: DIMM
    Set: None
    Locator: **DIMM2**
....
....
Evidently, they are of 512MB + 256MB (=768MB) sizes. Has someone changed the modules without your knowledge? :shock:
And you don't need to install XP to verify that. Just go into your BIOS and look for current system info. Any OS, including XP, will see only what BIOS sees.

Also, with this amount of RAM, if you want 'extra-performance', you may have to consider Xubuntu.

---

