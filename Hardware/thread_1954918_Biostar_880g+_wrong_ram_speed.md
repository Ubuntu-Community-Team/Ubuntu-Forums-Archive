---
title: "Biostar 880g+ wrong ram speed"
date: 2012-04-08
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2012-04-08
i manged to find the option in the bios and set it to manual dr3 1333 but the speed it still wrong
*the bios wanted to use 1.6volts
RAM:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231396](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231396)
Motherboard:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813138283](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138283)
Manual:
[http://www.biostar.com.tw/upload/Manual/A88PC-M3S%20&%20A88GC-M3S_100519_B.zip](http://www.biostar.com.tw/upload/Manual/A88PC-M3S%20&%20A88GC-M3S_100519_B.zip)
running ubuntu 10.10 64bit

```
sudo dmidecode --type 17
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x002A, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0028
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: Other
    Type Detail: Synchronous
    **Speed: 667 MHz (1.5 ns)**
    Manufacturer: Manufacturer00
    Serial Number: 00000000
    Asset Tag: AssetTagNum0
    Part Number: F3-10666CL9-2GBNS0

Handle 0x002C, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0028
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: Other
    Type Detail: Synchronous
    **Speed: 667 MHz (1.5 ns)**
    Manufacturer: Manufacturer01
    Serial Number: 00000000
    Asset Tag: AssetTagNum1
    Part Number: F3-10666CL9-2GBNS0

Handle 0x002E, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0028
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: Other
    Set: None
    Locator: DIMM2
    Bank Locator: BANK2
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Manufacturer02
    Serial Number: SerNum02
    Asset Tag: AssetTagNum2
    Part Number: ModulePartNumber02

Handle 0x0030, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0028
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: Other
    Set: None
    Locator: DIMM3
    Bank Locator: BANK3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Manufacturer03
    Serial Number: SerNum03
    Asset Tag: AssetTagNum3
    Part Number: ModulePartNumber03

```

---

### Post by Yellow Pasque on 2012-04-09
> Speed: 667 MHz (1.5 ns)

DDR = **Double** Data Rate..
..so 667MHz clock = DDR-1333

---

### Post by pqwoerituytrueiwoq on 2012-04-09
But my ddr3 1600 gets 1600MHz.... therefore ddr3 1333 should get 1333MHz
this one is running 10.04 lucid (hardware in sig)
```
sudo dmidecode --type 17
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0038, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0036
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Manufacturer00
    Serial Number: SerNum00
    Asset Tag: AssetTagNum0
    Part Number: ModulePartNumber00

Handle 0x003A, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0036
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: Other
    Type Detail: Synchronous
    **Speed: 1600 MHz (0.6 ns)**
    Manufacturer: Manufacturer01
    Serial Number: SerNum01
    Asset Tag: AssetTagNum1
    Part Number: ModulePartNumber01

Handle 0x003C, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0036
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM2
    Bank Locator: BANK2
    Type: Other
    Type Detail: Synchronous
   ** Speed: 1600 MHz (0.6 ns)**
    Manufacturer: Manufacturer02
    Serial Number: SerNum02
    Asset Tag: AssetTagNum2
    Part Number: ModulePartNumber02

Handle 0x003E, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0036
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM3
    Bank Locator: BANK3
    Type: Other
    Type Detail: Synchronous
    **Speed: 1600 MHz (0.6 ns)**
    Manufacturer: Manufacturer03
    Serial Number: SerNum03
    Asset Tag: AssetTagNum3
    Part Number: ModulePartNumber03

```

---

### Post by Yellow Pasque on 2012-04-09
I've never seen that (maybe it depends on how the BIOS reports it). Every board I've had (including 3 Biostar boards) has reported actual clock speed rather than DDR.
Here's my DDR3-1333 on a Biostar TA890FX:
```
# dmidecode 2.11
SMBIOS 2.5 present.

Handle 0x0026, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0024
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: Other
	Type Detail: Synchronous
	Speed: 667 MHz
	Manufacturer: Manufacturer00
	Serial Number: 00000000
	Asset Tag: AssetTagNum0
	Part Number: F3-10666CL8-2GBECO

Handle 0x0028, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0024
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: Other
	Type Detail: Synchronous
	Speed: 667 MHz
	Manufacturer: Manufacturer01
	Serial Number: 00000000
	Asset Tag: AssetTagNum1
	Part Number: F3-10666CL8-2GBECO

```

---

### Post by pqwoerituytrueiwoq on 2012-04-09
I also checked my dads system, it gives 1600mhz and it has a gigabyte board, but had to manually set it [details]("http://www.mushkingames.com/phpbb2/viewtopic.php?f=3&t=22112&sid=82d89830a9e028740f5a43a9c328e7df")
[SIZE=1]*Does the comma go before or after but?*[/SIZE]

---

### Post by pqwoerituytrueiwoq on 2012-04-09
this is from my mom's system
board:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131672](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131672)
ram:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231423](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231423)
```
sudo dmidecode --type 17
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0035, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0033
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: Other
    Type Detail: Synchronous
    Speed: 1333 MHz (0.8 ns)
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0

Handle 0x0037, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0033
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1

Handle 0x0039, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0033
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM2
    Bank Locator: BANK2
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Manufacturer2
    Serial Number: SerNum2
    Asset Tag: AssetTagNum2
    Part Number: PartNum2

Handle 0x003B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0033
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM3
    Bank Locator: BANK3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Manufacturer3
    Serial Number: SerNum3
    Asset Tag: AssetTagNum3
    Part Number: PartNum3

```

---

