---
title: "Any Idea 667MHz 4th Memory Module"
date: 2015-10-02
forum: Hardware
---

### Post by 3246251196 on 2015-10-02
Hi all, is there a reason for the following:

```
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             physical id: 1
             slot: A1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM 800 MHz (1.2 ns)
             physical id: 2
             slot: A2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM 667 MHz (1.5 ns)
             physical id: 3
             slot: A3
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)

```

The fourth module @ 667 ? They all are the same type of memory. Kingston Hyperx ddr2

Thanks.

---

### Post by tgalati4 on 2015-10-02
Try bumping up the voltage to the RAM in BIOS.  Label them #1 through #4 with a Sharpie and rotate them around.  Take careful notes.  You may have a poor slot and the motherboard is compensating by lowering the speed.  Check the voltages on your power supply.  Try a different power supply.

---

### Post by 3246251196 on 2015-10-02
If one is running at 667 then they all do, right?

---

### Post by tgalati4 on 2015-10-02
Generally, yes.  The memory bus speed is consistent across all memory banks.  Run memtest from the GRUB2 menu and what speed is displayed?

---

### Post by Yellow Pasque on 2015-10-03
Does dmidecode confirm the information? (I guess that's from lshw?)
```
sudo dmidecode -t memory
```

---

### Post by 3246251196 on 2015-10-03
Hi all, thanks for the input.


Yes, everything confirms that this 4th module is running at 333/667 while the others run at 400. This includes memtest.

I am not sure why this is. I originally had two Kingston hyperx 2gb, I noticed in same uses of my machine I was running into swap space. I decided to get another two sticks of the same memory from ebay. The seller did state that these two were not a matching pair (but both were labeled as 
**[SIZE=2]4GB kit (2x2GB) DDR2 / PC2-6400 800 Mhz  / NON-ECC MEMORY Kingston HyperX[/SIZE]**

 
The model numbers and their respective specs
khx6400d2/2g ([http://www.kingston.com/datasheets/KHX6400D2_2G.pdf](http://www.kingston.com/datasheets/KHX6400D2_2G.pdf))
khx6400d2k2/4g ([http://content.ekatalog.biz/katalog/20365092/20365092.pdf](http://content.ekatalog.biz/katalog/20365092/20365092.pdf))

It seems that both have been tested to run at 800 but at different voltages. I have it set to 2.0V at the minute.

What do you think?

Cheers

PS: I remember in my younger days being obsessed with running things at the best performance. I am seriously not bothered these days. From what I have heard there is not much difference if they are all running at 667 anyway, but I am interested in the problem.

```
# dmidecode 2.12
SMBIOS 2.4 present.

Handle 0x0005, DMI type 5, 24 bytes
Memory Controller Information
    Error Detecting Method: 8-bit Parity
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 1024 MB
    Maximum Total Memory Size: 4096 MB
    Supported Speeds:
        Other
    Supported Memory Types:
        Other
    Memory Module Voltage: 5.0 V
    Associated Memory Slots: 4
        0x0006
        0x0007
        0x0008
        0x0009
    Enabled Error Correcting Capabilities:
        None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A0
    Bank Connections: 1
    Current Speed: Unknown
    Type: Other
    Installed Size: 2048 MB (Single-bank Connection)
    Enabled Size: 2048 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A1
    Bank Connections: 2
    Current Speed: Unknown
    Type: Other
    Installed Size: 2048 MB (Single-bank Connection)
    Enabled Size: 2048 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A2
    Bank Connections: 3
    Current Speed: Unknown
    Type: Other
    Installed Size: 2048 MB (Single-bank Connection)
    Enabled Size: 2048 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A3
    Bank Connections: 4
    Current Speed: Unknown
    Type: Other
    Installed Size: 2048 MB (Single-bank Connection)
    Enabled Size: 2048 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0019, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x001A, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0019
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    Type: Unknown
    Type Detail: None
    Speed: 800 MHz
    Manufacturer:  
    Serial Number:  
    Asset Tag:  
    Part Number:  

Handle 0x001B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0019
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A1
    Bank Locator: Bank2/3
    Type: Unknown
    Type Detail: None
    Speed: 800 MHz
    Manufacturer:  
    Serial Number:  
    Asset Tag:  
    Part Number:  

Handle 0x001C, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0019
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A2
    Bank Locator: Bank4/5
    Type: Unknown
    Type Detail: None
    Speed: 800 MHz
    Manufacturer:  
    Serial Number:  
    Asset Tag:  
    Part Number:  

Handle 0x001D, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0019
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A3
    Bank Locator: Bank6/7
    Type: Unknown
    Type Detail: None
    Speed: 667 MHz
    Manufacturer:  
    Serial Number:  
    Asset Tag:  
    Part Number:
```

---

### Post by tgalati4 on 2015-10-03
It's possible that your motherboard handles multiple memory slot speeds.  In my testing, overclocking RAM gave a 10% increase in memtest speed.  Does this mean a 10% increase in overall performance?  Probably not, since many processes are CPU-bound anyway.  The fact that the RAM sticks run at different voltages mean they are different production and perhaps different internal construction.

---

### Post by Yellow Pasque on 2015-10-03
What motherboard/CPU do you have? Do you have the latest BIOS?

Note that the 'Speed' field of dmidecode may not indicate the RAM's actual speed. Later versions of SMBIOS have a bit different structure: [http://ubuntuforums.org/showthread.php?t=2288742](http://ubuntuforums.org/showthread.php?t=2288742)

---

### Post by 3246251196 on 2015-10-03
Its a recently upgraded Core&#8482; 2 Quad Q9650 and the mobo is GA-EP45-UD3LR (gigabyte) - had this since 2010ish I think.

---

### Post by Yellow Pasque on 2015-10-03
There are some BIOS updates which claim improved memory compatibility. If you're up to it, you may want to update to the latest BIOS. Personally, I would check to see what the POST startup screen says about your memory when you turn on the system (you may have to disable the BIOS splash screen to see those details).

---

### Post by 3246251196 on 2015-10-09
I have not applied any BIOS updates but I thought I would see what would happen if I swapped the two modules around (which was suggested before). I have actually found that the module @ 2.0V is the one that is running at 667MHz.

I guess this makes sense... I will have to increase VDIMM ? I thought I already tried running enough but I will have a mess around again later on.
[ATTACH=CONFIG]264876[/ATTACH]

---

### Post by tgalati4 on 2015-10-09
It's quite possible that the RAM sticks were "binned".  As they go through testing, those that are stable at rated speed at 1.85 V get put in the 1.85 V bin.  Those that need 2.0 get put into the 2.0 V bin.  You might need 2.1 or 2.2 Volts to get that chip to run at the higher speeds.

Obviously, if you are building a new system, you want matched RAM sticks.  It's unsettling that Kingston uses the same part number for two different voltages.

---

### Post by Yellow Pasque on 2015-10-09
Again, I think this stick reports its SPD timings differently and that dmidecode reflects that. Apparently, this is not unheard of with Kingston sticks: [http://www.tomshardware.com/forum/265113-30-kingston-pc6400-strange-irregularities](http://www.tomshardware.com/forum/265113-30-kingston-pc6400-strange-irregularities)

If it was me, I would either.. 
A ) leave it alone because your all of the RAM is probably running at the same speed despite what dmidecode reports.
B ) set the BIOS to 1.85V, DDR2-667, and call it a day. If you can get it to run stable at CL4 without exceeding 2.0V, that's a nice bonus. From what I've read, tighter timings are more important than memory clock speeds for Core2 Duo/Quad anyway: [http://www.legionhardware.com/articles_pages/ddr2_memory_frequency_performance,6.html](http://www.legionhardware.com/articles_pages/ddr2_memory_frequency_performance,6.html)
[http://www.anandtech.com/show/2050/3](http://www.anandtech.com/show/2050/3)

>  You might need 2.1 or 2.2 Volts to get that chip to run at the higher speeds
Raising the voltage isn't going to change the SPD (until you fry the stick and it reports nothing). The risk of running the RAM at voltages that far above spec is not worth the reward (see the previous links). If you still insist on running a stick of DDR2 rated for 1.8V at more than 2.0V, make sure you have some airflow over the heat spreaders.

---

### Post by tgalati4 on 2015-10-10
I was only suggesting running the 2.0 stick (by itself) at 2.1 volts to see if it runs reliably at 800 MHz FSB speed.  I would return the 2.0 volts stick and get another matched 1.85 V stick.  It is not a good idea to run an entire bank of 1.85 V at 2 V or higher.  That will result in higher RAM temperatures and shorter life.

---

