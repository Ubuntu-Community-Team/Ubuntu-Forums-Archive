---
title: "Adding more RAM to my CLEVO M771SUN laptop, 2x2GB or 2x4GB?"
date: 2012-08-11
forum: Hardware
---

### Post by hihihi100 on 2012-08-11
Hello:
 
My laptop is a clevo-M771SUN (terminal will list it as M7X0SUN) and at present time I have one 2GB RAM unit (machine has 2 slots). If I can have 8GB RAM in total instead of 4GB; id aim for that, but questions arise about these 3 conflicting sources of info:
 
**First:**
 
```
sudo dmidecode --type memory
```
 
Returns:
 
```
# dmidecode 2.11
SMBIOS 2.4 present.
 
Handle 0x000E, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 12 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2
 
Handle 0x000F, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000E
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: 1
    Locator: DIMM1
    Bank Locator: DIMM1
    Type: DRAM
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
 
Handle 0x0010, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000E
    Error Information Handle: No Error
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: 1
    Locator: DIMM2
    Bank Locator: DIMM2
    Type: DRAM
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

```
 
_Maximum Capacity: 12 GB_ <----- according to this, I could add 2x4GB RAM, Id still have 4GB "free" (not really free, I only have 2 slots).
 
**Second:**
 
I have been told to use crucial to upgrade my RAM, so after writing brand and model I get:
 
[http://www.crucial.com/store/mpartspecs.aspx?mtbpoid=DE2E9328A5CA7304](http://www.crucial.com/store/mpartspecs.aspx?mtbpoid=DE2E9328A5CA7304)
 
which is "Guaranteed-compatible with the Clevo M771SUN", as they say. Furthermore, on the left column that includes information about my machine, it clearly states: "Each memory slot can hold DDR2 PC2-5300, DDR2 PC2-6400 with a maximum of 2GB per slot.*
*Not to exceed manufacturer supported memory."
 
According to this, I can only have 2x2GB RAM memory
 
What information should I give preference?
 
I am aware that I already have one single 2GB RAM card in one slot, cheapest and easiest option would be to buy one exactly identical to the one already present in the used slot. UPDATE: I have finally managed to open the mem module part of the laptop: the memory module is a 2G DDR2 800 SO-DIMM from Transcend.
 
**Third:**
 
[http://laptops.productwiki.com/clevo-m770sun/](http://laptops.productwiki.com/clevo-m770sun/) says in the features section: ---> "Supports up to 4GB of DDR2 RAM"
 
Then I dont understand why the first command lists 12GB as maximum

---

