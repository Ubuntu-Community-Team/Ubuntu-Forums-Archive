---
title: "Memory (Ram) slot question"
date: 2014-12-06
forum: Hardware
---

### Post by michael-piziak on 2014-12-06
I received this reply from Crucial memory,

"Thank you for contacting us. Please know that the maximum memory is 8GB for your motherboard but if you are using a 32 bit OS then the limitation is 3-3.5 of memory, unless you have a 64 bit OS then 8GB would be the maximum used and seen."

I have 12.04 lts 64 bit, so that's good.

I currently have 3.8 gigs of ram in my system, as reported by system monitor.  Is there a way, other than opening the computer, to see how much ram is in which slots of my system.  For example, if I have 3.8 gigs of ram now and only 2 slots, I can buy one more 4 gig ram.  However, if I only have 2 slots and there are 2 gigs in each one, then I'll have to consider what I need to do to get to 8 gb ram.

---

### Post by QIII on 2014-12-06
Hello!

Depending on the level of detail provided by your BIOS/EFI, you may be able to go to you BIOS setting and find out how many slots there are, how many are filled and how much is in each slot.

If you can't get that,

```
sudo dmidecode -t memory
```

In the terminal will give you what you seek.

If not, you'll have to open the case.

Cheers!

---

### Post by michael-piziak on 2014-12-06
ok, What does this tell about my memory situation ?


```
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo dmidecode -t memory
[sudo] password for michael: 
# dmidecode 2.11
SMBIOS 2.5 present.


Handle 0x0032, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 4 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4


Handle 0x0033, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: Flash Memory
    Error Correction Type: None
    Maximum Capacity: 4 MB
    Error Information Handle: Not Provided
    Number Of Devices: 1


Handle 0x0034, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0032
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: 1
    Locator: XMM1
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 800 MHz
    Manufacturer: JEDEC ID:7F BA 00 00 00 00 00 00
    Serial Number: 00000000
    Asset Tag: Not Specified
    Part Number:  


Handle 0x0035, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0032
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: 1
    Locator: XMM2
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 800 MHz
    Manufacturer: JEDEC ID:AD 00 00 00 00 00 00 00
    Serial Number: B6E13062
    Asset Tag: Not Specified
    Part Number: HYMP112U64CP8-S6


Handle 0x0036, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0032
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: 2
    Locator: XMM3
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 800 MHz
    Manufacturer: JEDEC ID:7F BA 00 00 00 00 00 00
    Serial Number: 00000000
    Asset Tag: Not Specified
    Part Number:  


Handle 0x0037, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0032
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: 2
    Locator: XMM4
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 800 MHz
    Manufacturer: JEDEC ID:7F 7F 7F 7F 7F 51 00 00
    Serial Number: 20620515
    Asset Tag: Not Specified
    Part Number: 64T128020EU2.5B2


Handle 0x0039, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0033
    Error Information Handle: Not Provided
    Total Width: 2 bits
    Data Width: 2 bits
    Size: 4096 kB
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


michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$
```

---

### Post by QIII on 2014-12-06
OK.  

You have four slots filled with 1GB each.  So you can't just pop a couple more in.

I also see that it's DDR2.

So a couple of things.

First:  To get 8GB you would need 4 new modules of 2GB each.
Second:  DDR2 is getting harder to find and getting expensive.  You might have to look for decent deals on Amazon or ebay, but it will be more than a couple of bucks.

I won't tell you how to spend your money, but if it were me I wouldn't bother.  4GB of memory is more than enough for the vast majority of users.  Unless you plan to run a bunch of virtual machines, you want to run scientific software, or you are running in to high swap conditions, I'd recommend skipping the upgrade and spending the money on something else.

---

### Post by mörgæs on 2014-12-06
**sudo lshw -short -C memory** will make a more readable output.

Besides, I agree that 4 GB is enough for regular tasks. I doubt that there's much speed improvement by adding more.

---

### Post by michael-piziak on 2014-12-06
Thanks so much.

Marking this thread as solved.

---

