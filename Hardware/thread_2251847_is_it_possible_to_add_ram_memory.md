---
title: "is it possible to add ram memory?"
date: 2014-11-07
forum: Hardware
---

### Post by marchello_lippi2 on 2014-11-07
Hi all, 

I've got dell inspiron 15 3000 series, it works fine, I just would like to know is it possible to add ram memory? 

$ sudo dmidecode --type memory
# dmidecode 2.12
SMBIOS 2.8 present.

Handle 0x002E, DMI type 16, 23 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 2 GB
        Error Information Handle: Not Provided
        Number Of Devices: 1

Handle 0x0030, DMI type 17, 40 bytes
Memory Device
        Array Handle: 0x002E
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: SODIMM
        Set: None
        Locator: DIMM_A
        Bank Locator: BANK 0  
        Type: DDR3
        Type Detail: Synchronous Unbuffered (Unregistered)
        Speed: 1600 MHz
        Manufacturer: Hynix/Hyundai
        Serial Number: 40378D63
        Asset Tag: A1_AssetTagNum0
        Part Number: HMT425S6AFR6A-PB  
        Rank: 1
        Configured Clock Speed: 1333 MHz
        Minimum voltage:  1.350 V
        Maximum voltage:  1.500 V
        Configured voltage:  1.500 V

---

### Post by MIJ-VI on 2014-11-07
The RAM appears to be maxed out. Exactly which machine do you have?

---

### Post by marchello_lippi2 on 2014-11-07
> **MIJ-VI said:**
> The RAM appears to be maxed out. Exactly which machine do you have?

$ sudo dmidecode | grep -A 9 "System Information"
System Information
        Manufacturer: Dell Inc.
        Product Name: Inspiron 3541
        Version: Not Specified
        Serial Number: BBHZC12
        UUID: 4C4C4544-0042-4810-805A-C2C04F433132
        Wake-up Type: Power Switch
        SKU Number: 0657
        Family:                       

Is there any chance that max ram memory can be increased in some way?

---

### Post by plucky on 2014-11-07
> **marchello_lippi2 said:**
> $ sudo dmidecode | grep -A 9 "System Information"
System Information
        Manufacturer: Dell Inc.
        Product Name: Inspiron 3541
        Version: Not Specified
        Serial Number: BBHZC12
        UUID: 4C4C4544-0042-4810-805A-C2C04F433132
        Wake-up Type: Power Switch
        SKU Number: 0657
        Family:                       

Is there any chance that max ram memory can be increased in some way?

See [Here](http://www.dell.com/in/p/inspiron-15-3541-laptop/pd)

You would have to replace the 2Gb memory module with a 4Gb (4GB Single Channel DDR3L 1600MHz (4GBx1) module as your laptop only has one memory slot.

Good Luck

---

