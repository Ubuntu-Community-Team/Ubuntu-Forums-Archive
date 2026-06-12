---
title: "Upgrading memory"
date: 2013-10-13
forum: Hardware
---

### Post by Ramesh_Jude_Fernando on 2013-10-13
Hi all I have Acer Aspire V3 771G-6662 model bought from Best Buy earlier this summer.
I ran dmidecode and this is the result I got which means I can have upto 32 GB of RAM. What's annoying is I chatted with online  Acer support and their Indian tech support  says I can only install 16 GB of RAM even with dmidecode saying I can have upto 32GB as I have 2  of 8GB DIMMs and I can install 2 more 8 GB modules. Unfortunately, I checked with Kingston Canada online and they only have 4 GB DIMMS for the 771G. I gotta laugh at Acer and Kingston, all these techs in India do is read scripts looking up online database. I am sure the Best Buy techs would know more, but  I wish there was another way to upgrade without having to take it into Best Buy and ridiculous charges. I have installed RAM before on a desktop so I doubt it would be much harder on a notebook.
# dmidecode 2.12
SMBIOS 2.7 present.

Handle 0x0005, DMI type 5, 24 bytes
Memory Controller Information
    Error Detecting Method: None
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 8192 MB
    Maximum Total Memory Size: 32768 MB
    Supported Speeds:
        Other
    Supported Memory Types:
        Other
    Memory Module Voltage: Unknown
    Associated Memory Slots: 4
        0x0006
        0x0007
        0x0008
        0x0009
    Enabled Error Correcting Capabilities:
        None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM0
    Bank Connections: None
    Current Speed: Unknown
    Type: DIMM
    Installed Size: 8192 MB (Single-bank Connection)
    Enabled Size: 8192 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM1
    Bank Connections: None
    Current Speed: Unknown
    Type: DIMM
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM1
    Bank Connections: None
    Current Speed: Unknown
    Type: DIMM
    Installed Size: 8192 MB (Single-bank Connection)
    Enabled Size: 8192 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM3
    Bank Connections: None
    Current Speed: Unknown
    Type: DIMM
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK

Handle 0x001A, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x001B, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x001A
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1600 MHz
    Manufacturer: Kingston
    Serial Number: 230B683B
    Asset Tag: Unknown
    Part Number: ACR16D3LS1KBG/8G  
    Rank: 2
    Configured Clock Speed: 1600 MHz

Handle 0x001C, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x001A
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK 1
    Type: Unknown
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Empty
    Serial Number: Empty
    Asset Tag: Unknown
    Part Number: Empty
    Rank: Unknown
    Configured Clock Speed: Unknown

Handle 0x001D, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x001A
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK 2
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1600 MHz
    Manufacturer: Kingston
    Serial Number: 1F0B323B
    Asset Tag: Unknown
    Part Number: ACR16D3LS1KBG/8G  
    Rank: 2
    Configured Clock Speed: 1600 MHz

Handle 0x001E, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x001A
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM3
    Bank Locator: BANK 3
    Type: Unknown
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Empty
    Serial Number: Empty
    Asset Tag: Unknown
    Part Number: Empty
    Rank: Unknown
    Configured Clock Speed: Unknown

---

### Post by Yellow Pasque on 2013-10-13
If the laptop really does support 32GB, then I can't see why this wouldn't work (DDR3-1600, CAS 11 like your current modules): [http://www.newegg.ca/Product/Product.aspx?Item=N82E16820239289](http://www.newegg.ca/Product/Product.aspx?Item=N82E16820239289)

> Even with dmidecode saying I can have upto 32GB as I have 2 of 8GB DIMMs and I can install 2 more 8 GB modules.
dmidecode can tell you the max RAM size per slot, but it can't tell you about chipset limitations, so be careful. If Acer says the max is 16GB, then you may want to heed that advice.

What are you doing that requires so much RAM?

---

### Post by Yellow Pasque on 2013-10-13
Alternatively: [http://www.ncix.ca/products/?sku=74956&vpn=KVR16S11/8&manufacture=Kingston](http://www.ncix.ca/products/?sku=74956&vpn=KVR16S11/8&manufacture=Kingston)
(Tried to get link before, but NCIX's site seems to dislike Firefox/iceweasel).

---

### Post by Ramesh_Jude_Fernando on 2013-10-14
Thanks guys, I want to run R as it loads everything into RAM( installed U of Toronto's Stats/CS prof  Radford Neal pqR but couldn't get RStudio running on it). and Python/Scipy/Numpy with massive data sets for  fun and Kaggle, I don't waste my time entering Kaggle  as I don't have a PhD in Statistics or CS but I registered for online  MSc in CS at Georgia Tech probably take Machine Learning option since my background is economics/econometrics, I find stats fun.  RAM memory is so cheap and getting cheaper! With parallel  processing if not quantum computers coming online in a twenty/thirty years if not sooner, most things won't need to be loaded from disks even SSDs. I actually find it really interesting time. What's the big deal about having so  much RAM?  it's better to have more RAM than disks  even SSDs or even faster CPU??? especially with 1600 MHz  RAM which comes faster from the bus. The only thing better than more RAM is a bigger L2 cache so sometimes a more powerful  CPU with a bigger L2 cache is better. I am not an expert, one of my best friends has a MSc in Electronics Engineering from U of Toronto and works for LSI,  perhaps I should ask him...  I only like software/analytics  and use of hardware only to use the software.

---

