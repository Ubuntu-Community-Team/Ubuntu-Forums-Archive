---
title: "dmidecode - &quot;speed&quot; vs &quot;configured clock speed&quot; for RAM"
date: 2015-07-29
forum: Hardware
---

### Post by medialdemocrat on 2015-07-29
Hi guys, this is my first post to the forum so I hope this post is properly placed and formatted according to norms... Anyhow, to the question. I typed the following command in my terminal to return info about my RAM, seeing as how I just built my computer and want to ensure it is all working normally. 

sudo dmidecode --type 17

This is the data it returns: 

```

# dmidecode 2.12
# SMBIOS entry point at 0x000f04c0
SMBIOS 2.7 present.


Handle 0x0026, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0024
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM_A1
    Bank Locator: A1_BANK0
    Type: DDR3
    Type Detail: Synchronous Unbuffered (Unregistered)
    [COLOR=#0000ff]Speed: 1333 MHz[/COLOR]
    Manufacturer: A1_Manufacturer1
    Serial Number: A1_SerNum1
    Asset Tag: A1_AssetTagNum1
    Part Number: Array1_PartNumber1
    Rank: Unknown
    [COLOR=#ff0000]Configured Clock Speed: 2132 MHz[/COLOR]


Handle 0x0028, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0024
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: Unknown
    Set: None
    Locator: DIMM_A2
    Bank Locator: A1_BANK1
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: A1_Manufacturer0
    Serial Number: A1_SerNum0
    Asset Tag: A1_AssetTagNum0
    Part Number: Array1_PartNumber0
    Rank: Unknown
    Configured Clock Speed: Unknown


Handle 0x002A, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0024
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM_B1
    Bank Locator: A1_BANK2
    Type: DDR3
    Type Detail: Synchronous Unbuffered (Unregistered)
    [COLOR=#0000ff]Speed: 1333 MHz[/COLOR]
    Manufacturer: Corsair         
    Serial Number: 00000000  
    Asset Tag: A1_AssetTagNum2
    Part Number: CMY8GX3M2B2133C9  
    Rank: 1
    [COLOR=#ff0000]Configured Clock Speed: 2132 MHz[/COLOR]


Handle 0x002C, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0024
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: Unknown
    Set: None
    Locator: DIMM_B2
    Bank Locator: A1_BANK3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: A1_Manufacturer3
    Serial Number: A1_SerNum3
    Asset Tag: A1_AssetTagNum3
    Part Number: Array1_PartNumber3
    Rank: Unknown
    Configured Clock Speed: Unknown

```

I know that the SPD default speed for the RAM I have is 1333, and I tried to set my BIOS to get 2133 MHz out of the RAM, which is the advertised speed of the RAM. The RAM: [http://www.corsair.com/en/vengeance-pro-series-8gb-2-x-4gb-ddr3-dram-2133mhz-c9-memory-kit-cmy8gx3m2b2133c9](http://www.corsair.com/en/vengeance-pro-series-8gb-2-x-4gb-ddr3-dram-2133mhz-c9-memory-kit-cmy8gx3m2b2133c9)

Which is the ACTUAL speed that the RAM is operating at; is it 1333 MHz or 2132 MHz?

Thanks guys

---

