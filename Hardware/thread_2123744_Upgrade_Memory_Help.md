---
title: "Upgrade Memory Help"
date: 2013-03-08
forum: Hardware
---

### Post by lemonoid on 2013-03-08
Hi all,
I've always had help here when I needed it, so I'm hoping someone can answer a couple questions for me about upgrading my RAM. I have an older computer, non-specific manufacturer or model number as it is custom built. What I do know is I'm running an AMD Sempron 2500+ with 2GB RAM. I need more RAM as I no longer have my laptop and need at least 4GB of RAM and a good 150GB free memory to build Android source I'm planning on building. As I'm dual-booting with Win7, it takes up a lot of my storage space so I'm going to have to figure out how to downsize Win7 to a safe size so I can get more storage here. I need 150 GB more storage. So that is one issue in itself. But I need to upgrade from 2GB RAM to at least 4GB. Can anyone tell me any commands to run to figure out what type of memory my motherboard supports (ie currently has) as I know that for instance if I have DDR then I cant use DDR2 or DDR3. Also is there a way to upgrade my storage without losing everything that's currently stored on my hard drive. I don't know much about Solid State hard drives, I'm sure I can google it in about 5 seconds and find out all about it but it just popped in my head while I was typing this so figure I'd ask, can I install a SSHD and move my Win installation to this, so that my current HDD is free to expand that which my Ubuntu uses. BTW I'm on 12.04 as when I tried to run 12.10 live, it didn't work correctly, I'm guessing because of my old hardware. If anyone could answer the question about finding a way to expand my storage and give me a command to figure out what all my hardware is, I could figure out the compatibility issues on my own. When it comes down to it, I just would like to have all of that storage Win7 is taking up for Ubuntu, without going through all the trouble of deleting my win7 stuff, because its my dad's, and a way to figure out all my hardware specs so I can  get online and research what memory I can get that will work properly with my current motherboard. Thanks in advance, I hope this wasn't confusing. I worded it as best as possible.

---

### Post by jerome1232 on 2013-03-08
Personally, I'd just pop off the side of the case and look for the motherboards serial number, then google the serial number. You can usually find the specs for your motherboard exactly that way.

---

### Post by lemonoid on 2013-03-09
thx so much. I think I'll do that. I've never actually pulled much hardware apart. Do I need to do so to find the serial #?

---

### Post by jerome1232 on 2013-03-09
Most likely no, but every motherboard is different and it's possible your serial number is in a goofy spot, under something. 

I just realized there is another way. You could try dmidecode, I didn't realize it often has serial number information and more.

On my system this command returns my motherboards serial
```
sudo dmidecode -s baseboard-product-name
```

you could also try

```
sudo dmidecode -s baseboard-serial-number
```

---

### Post by Cheesemill on 2013-03-09
Can you post the output of...
```
sudo dmidecode -t memory
```

This will tell us how many RAM slots your motherboard has and what's plugged into each one.

---

### Post by lemonoid on 2013-03-10
thx I'm about to try all those suggestions. post back when i have results

---

### Post by lemonoid on 2013-03-10
andyripper@andyripper-4:~$ sudo dmidecode -t memory
[sudo] password for andyripper: 
# dmidecode 2.11
SMBIOS 2.3 present.

Handle 0x0005, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: None
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: Four-way Interleave
    Maximum Memory Module Size: 256 MB
    Maximum Total Memory Size: 512 MB
    Supported Speeds:
        70 ns
        60 ns
    Supported Memory Types:
        DIMM
        SDRAM
    Memory Module Voltage: 3.3 V
    Associated Memory Slots: 2
        0x0006
        0x0007
    Enabled Error Correcting Capabilities: None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A0
    Bank Connections: 0 1
    Current Speed: 60 ns
    Type: Other SDRAM
    Installed Size: 1024 MB (Double-bank Connection)
    Enabled Size: 1024 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A1
    Bank Connections: 2 3
    Current Speed: 60 ns
    Type: Other SDRAM
    Installed Size: 1024 MB (Double-bank Connection)
    Enabled Size: 1024 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0019, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 2 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x001A, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0019
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x001B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0019
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: A1
    Bank Locator: Bank2/3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

---

### Post by lemonoid on 2013-03-10
andyripper@andyripper-4:~$ sudo dmidecode -s baseboard-product-name
MS-7061

base-board-serial-number provided no output. the command executed but I had no output return, just a blank line

---

### Post by Cheesemill on 2013-03-10
By the looks of things your motherboard only has 2 RAM slots, both of which currently have a 1GB stick in.

Also your motherboard will take a maximum of 2GB total, so upgrading isn't a possibility I'm afraid.
```
Handle 0x0019, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
[COLOR=#ff0000]     Maximum Capacity: 2 GB[/COLOR]
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x001A, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0019
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    [COLOR=#ff0000]Size: 1024 MB[/COLOR]
    Form Factor: DIMM
    Set: None
[COLOR=#ff0000]     Locator: A0[/COLOR]
    Bank Locator: Bank0/1
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x001B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0019
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    [COLOR=#ff0000]Size: 1024 MB[/COLOR]
    Form Factor: DIMM
    Set: None
[COLOR=#ff0000]     Locator: A1[/COLOR]
    Bank Locator: Bank2/3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None
```

---

