---
title: "Asus p8h67-m pro memory cache l3 disabled"
date: 2011-08-07
forum: Hardware
---

### Post by fernoppix on 2011-08-07
I've recently bought this mainboard with an intel  i5 2500, everything  works but when I check the hardware I see that  memory cache L3 is  disabled. I have an Ubuntu 11.04 and I test it with  lshw and dmidecode  commands. This is the output of dmidecode:
Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1-Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 256 KB
    Maximum Size: 256 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2-Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 1024 KB
    Maximum Size: 1024 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L3-Cache
    Configuration: Disabled, Not Socketed, Level 3
    Operational Mode: Unknown
    Location: Internal
    Installed Size: 6144 KB
    Maximum Size: 6144 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: Other


I've  contacted with the store when I've bought the mainboard and they  say me  that's a Linux problem , not hardware. They say me that I try to   install a Windows for check the system. I think Linux it isn't the   problem because I've tryed with other distros, memtest86... without   solution. I don't find any options in BIOS for enabling/disabling memory   cache.

Thanks and sorry for my english

---

### Post by headvampyre@hotmail.co.uk on 2011-08-07
Hi, I've spent quite a while looking on Google about this, and there's nothing. Have you checked the BIOS? If not, don't worry too much about L3, from what Iv'e heard, L2 is much faster anyway. Oh, and what architecture is Ubuntu running under? I don't think 32-bit OS's support L3 caches.

---

### Post by fernoppix on 2011-08-07
I find in BIOS any options about enable/disable cacbe but it hasn't. I'm running an Ubuntu 11.04 64bit version. The solution it isn't forget the problem, because it would be how as use an old CPU with old parameters i.e. only L1 and L2 cache.

---

