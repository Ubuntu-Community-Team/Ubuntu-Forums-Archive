---
title: "Installing Nvidia 173.14 drivers in 16.04, how?"
date: 2016-05-06
forum: Hardware
---

### Post by mdlueck on 2016-05-06
I missed the detail on webpage ( [http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html) ) that all of the legacy Nvidia chips were not all supported by the 340.xx version driver.

I have a ThinkPad G41 which has a GeForce FX Go5200 GPU in it, and that page states actually that the 173.14 version driver is needed. There is no packages of that version driver in Synaptic for 16.04.

syslog gets filled with the following message, over and over... evidently Ubuntu keeps trying forever to find a GPU to engage:
[FONT=Courier New]May  4 21:27:48 eve nvidia-persistenced: Started (10551)
May  4 21:27:48 eve nvidia-persistenced: Failed to query NVIDIA devices. Please ensure that the NVIDIA device files (/dev/nvidia*) exist, and that user 121 has read and write permissions for those files.
May  4 21:27:48 eve nvidia-persistenced: The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
May  4 21:27:48 eve nvidia-persistenced: Shutdown (10551)
May  4 21:27:48 eve kernel: [  245.013324] NVRM: The NVIDIA GeForce FX Go5200 GPU installed in this system is
May  4 21:27:48 eve kernel: [  245.013324] NVRM:  supported through the NVIDIA 173.14.xx Legacy drivers. Please
May  4 21:27:48 eve kernel: [  245.013324] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
May  4 21:27:48 eve kernel: [  245.013324] NVRM:  information.  The 340.96 NVIDIA driver will ignore
May  4 21:27:48 eve kernel: [  245.013324] NVRM:  this GPU.  Continuing probe...
May  4 21:27:48 eve kernel: [  245.013412] NVRM: No NVIDIA graphics adapter found!
May  4 21:27:48 eve kernel: [  245.014445] NVRM: NVIDIA init module failed!
May  4 21:27:48 eve systemd-udevd[285]: Process '/sbin/modprobe nvidia-uvm' failed with exit code 1.
May  4 21:27:48 eve kernel: [  245.235462] NVRM: The NVIDIA GeForce FX Go5200 GPU installed in this system is
May  4 21:27:48 eve kernel: [  245.235462] NVRM:  supported through the NVIDIA 173.14.xx Legacy drivers. Please
May  4 21:27:48 eve kernel: [  245.235462] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
May  4 21:27:48 eve kernel: [  245.235462] NVRM:  information.  The 340.96 NVIDIA driver will ignore
May  4 21:27:48 eve kernel: [  245.235462] NVRM:  this GPU.  Continuing probe...
May  4 21:27:48 eve kernel: [  245.235508] NVRM: No NVIDIA graphics adapter found!
May  4 21:27:48 eve kernel: [  245.235929] NVRM: NVIDIA init module failed!
May  4 21:27:48 eve systemd-udevd[285]: Process '/usr/bin/nvidia-smi' failed with exit code 9.[/FONT]

How is it possible to obtain Ubuntu packages of the Nvidia 173.14 version driver which support this GPU?

I am thankful,

---

### Post by him610 on 2016-05-06
Hello MDLueck,

Did you try this...
Settings > Software & Updates > Additional Drivers

---

### Post by mdlueck on 2016-05-06
Greetings  him610,

Yes, it says no drivers available for the hardware. That is when I went looking through the available package list.

I have already done the research, I included the links.

I need to know how to install the Nvidia 173.14 drivers in 16.04 as there is no official package available of them for 16.04. So, perhaps via a PPA, or...

I am thankful,

---

### Post by him610 on 2016-05-06
Go to the download page for Nvidia driver, vers 173.14.39
[http://www.nvidia.com/Download/driverResults.aspx/71302/en-us]("http://www.nvidia.com/Download/driverResults.aspx/71302/en-us")

Click the Download widget...
You should get this file...
/home/your/Downloads/NVIDIA-Linux-x86-173.14.39-pkg1.run

You can probably (sudo) run it from the command line, or double-click it from you file manager, and go from there.

---

### Post by $yl9pAR%t on 2016-05-06
I am afraid you should not install this nvidia driver. Nvidia-173.14 does not (and will not) support xorg-server 1.18.

---

### Post by him610 on 2016-05-06
@mefisto888
> you should not install this nvidia driver. Nvidia-173.14 does not (and will not) support xorg-server 1.18.

Thanks for the advice. mefisto888. I was not aware of the non-support issue.

How would you resolve the problem of nvidia driver for  Mdleuck?

---

### Post by $yl9pAR%t on 2016-05-06
I see no sensible solution to install this driver on 16.04, he should stay with nouveau driver. If I remember right Ubuntu 14.04.1 was last Ubuntu release, that was using Xorg 1.15 (last supported by nvidia-173.xx), so OP can take step back and install 14.04.1 if nvidia driver is important here. OP is not newcomer and probably he understands his choices.

---

### Post by mdlueck on 2016-05-07
> **mefisto888 said:**
> he should stay with nouveau driver.

Since I have already installed the Nvidia 340.96 driver package on this system (After having done the LTS upgrade from 14.04 to 16.04), suggestions how to next migrate to the suggested nouveau driver?

I am thankful,

---

### Post by mdlueck on 2016-05-07
Answering my own question... I did the following:

```
mdlueck@eve:~$ dpkg -l|grep nvidia
ii  nvidia-340                                 340.96-0ubuntu3                                      i386         NVIDIA binary driver - version 340.96
ii  nvidia-340-updates                         340.96-0ubuntu3                                      i386         Transitional package for nvidia-340
ii  nvidia-opencl-icd-340                      340.96-0ubuntu3                                      i386         NVIDIA OpenCL ICD
ii  nvidia-prime                               0.8.2                                                i386         Tools to enable NVIDIA's Prime
ii  nvidia-settings                            361.42-0ubuntu1                                      i386         Tool for configuring the NVIDIA graphics driver
mdlueck@eve:~$ sudo dpkg -P nvidia-340 nvidia-340-updates nvidia-opencl-icd-340 nvidia-prime  nvidia-settings
```

IPL'ed successfully and at least have low resolution graphics on my external display. Now to see if I can figure out how to configure the correct resolution to my external display with what drivers the system now runs with. Failing that, I guess it is reimage time back to Xubuntu 14.04.

I am thankful,

---

### Post by him610 on 2016-05-07
How about posting the results, using code tags, of these two commands from a terminal... (They will do no harm)
```
inxi -b
sudo hwinfo --vbe
```

You may need to install* hwinfo* if you do not already have it installed...
```
sudo apt install hwinfo
```
It will allow us to see the resolutions your GFX card and monitor are capable of.

---

### Post by mdlueck on 2016-05-07
[FONT=Courier New]mdlueck@eve:~$ inxi -b
System:    Host: eve Kernel: 4.4.0-22-generic i686 (32 bit) Desktop: Xfce 4.12.3 Distro: Ubuntu 16.04 xenial
Machine:   System: IBM product: 28867YU v: ThinkPad G41
           Mobo: IBM model: 28867YU Bios: IBM v: 1XET57WW (1.16 ) date: 11/30/2006
CPU:       Single core Mobile Intel Pentium 4 (-HT-) speed: 3319 MHz (max)
Graphics:  Card: NVIDIA NV34M [GeForce FX Go5200 64M]
           Display Server: X.Org 1.18.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1400x1050@60.02hz, 1024x768@60.00hz
           GLX Renderer: Gallium 0.4 on NV34 GLX Version: 1.5 Mesa 11.2.0
Network:   Card: Broadcom NetXtreme BCM5705M_2 Gigabit Ethernet driver: tg3
Drives:    HDD Total Size: 60.0GB (11.4% used)
Info:      Processes: 196 Uptime: 2 min Memory: 233.7/2013.1MB Client: Shell (bash) inxi: 2.2.35[/FONT]



[FONT=Courier New]mdlueck@eve:~$ sudo hwinfo --vbe
01: None 00.0: 10105 BIOS                                       
  [Created at bios.186]
  Unique ID: rdCR.lZF+r4EgHp4
  Hardware Class: bios
  VESA BIOS Version: 3.0
  Current VESA Mode: 0x411b
  BIOS Keyboard LED Status:
    Scroll Lock: off
    Num Lock: on
    Caps Lock: off
  Parallel Port 0: 0x3bc
  Base Memory: 636 kB
  PnP BIOS: @@@0000
  MP spec rev 1.4 info:
    OEM id: ""
    Product id: "845E  Board"
    1 CPUs (0 disabled)
  BIOS32 Service Directory Entry: 0xfd700
  SMBIOS Version: 2.33
  BIOS Info: #0
    Vendor: "IBM"
    Version: "1XET57WW (1.16 )"
    Date: "11/30/2006"
    Start Address: 0xdc000
    ROM Size: 1024 kB
    Features: 0x0107000000007d09df80
      PCI supported
      PCMCIA supported
      PnP supported
      APM supported
      BIOS flashable
      BIOS shadowing allowed
      ESCD supported
      CD boot supported
      Selectable boot supported
      EDD spec supported
      720kB Floppy supported
      Print Screen supported
      8042 Keyboard Services supported
      Serial Services supported
      Printer Services supported
      CGA/Mono Video supported
      ACPI supported
      USB Legacy supported
      AGP supported
      BIOS Boot Spec supported
  System Info: #1
    Manufacturer: "IBM"
    Product: "28867YU"
    Version: "ThinkPad G41"
    Serial: "L3AX827"
    UUID: undefined, but settable
    Wake-up: 0x06 (Power Switch)
  Board Info: #2
    Manufacturer: "IBM"
    Product: "28867YU"
    Version: "Not Available"
    Serial: "1ZAUK58G049"
  Chassis Info: #3
    Manufacturer: "IBM"
    Version: "Not Available"
    Serial: "Not Available"
    Asset Tag: "No Asset Information"
    Type: 0x0a (Notebook)
    Bootup State: 0x02 (Unknown)
    Power Supply State: 0x02 (Unknown)
    Thermal State: 0x02 (Unknown)
    Security Status: 0x02 (Unknown)
  Inactive Record: #4
    Data 00: 7e 11 04 00 01 0c 02 03 04 02 02 02 02 00 00 00
    Data 10: 00
    String 1: "IBM"
    String 2: "Not Available"
    String 3: "Not Available"
    String 4: "Not Available"
  Inactive Record: #5
    Data 00: 7e 11 05 00 01 15 02 03 04 02 02 02 02 00 00 00
    Data 10: 00
    String 1: "IBM"
    String 2: "Not Available"
    String 3: "Not Available"
    String 4: "Not Available"
  Processor Info: #6
    Socket: "None"
    Socket Type: 0x06 (None)
    Socket Status: Populated
    Type: 0x03 (CPU)
    Family: 0xb2 (Pentium 4)
    Manufacturer: "GenuineIntel"
    Version: "Pentium(R) 4"
    Processor ID: 0xbfebfbff00000f41
    Status: 0x01 (Enabled)
    Voltage: 1.5 V
    External Clock: 400 MHz
    Max. Speed: 3330 MHz
    Current Speed: 3330 MHz
    L1 Cache: #10
    L2 Cache: #11
  Type 5 Record: #7
    Data 00: 05 14 07 00 03 04 03 03 09 01 00 00 05 02 02 08
    Data 10: 00 09 00 04
  Type 6 Record: #8
    Data 00: 06 0c 08 00 01 01 00 00 05 8a 8a 00
    String 1: "DIMM Slot 1"
  Type 6 Record: #9
    Data 00: 06 0c 09 00 01 23 00 00 05 8a 8a 00
    String 1: "DIMM Slot 2"
  Cache Info: #10
    Designation: "Internal L1 Cache"
    Level: L1
    State: Enabled
    Mode: 0x01 (Write Back)
    Location: 0x00 (Internal, Socketed)
    ECC: 0x05 (Single-bit)
    Type: 0x04 (Data)
    Associativity: 0x05 (4-way Set-Associative)
    Max. Size: 8 kB
    Current Size: 8 kB
    Supported SRAM Types: 0x0020 (Synchronous)
    Current SRAM Type: 0x0020 (Synchronous)
  Cache Info: #11
    Designation: "Internal L2 Cache"
    Level: L2
    State: Enabled
    Mode: 0x01 (Write Back)
    Location: 0x00 (Internal, Socketed)
    ECC: 0x06 (Multi-bit)
    Type: 0x05 (Unified)
    Associativity: 0x07 (8-way Set-Associative)
    Max. Size: 1024 kB
    Current Size: 1024 kB
    Supported SRAM Types: 0x0008 (Burst)
    Current SRAM Type: 0x0008 (Burst)
  Port Connector: #12
    Type: 0x05 (Parallel Port ECP/EPP)
    Internal Designator: "Not Available"
    External Designator: "Parallel"
    External Connector: 0x05 (DB-25 pin female)
  Port Connector: #13
    Type: 0x1c (Video Port)
    Internal Designator: "Not Available"
    External Designator: "External Monitor"
    External Connector: 0x07 (DB-15 pin female)
  Port Connector: #14
    Type: 0x0e (Mouse Port)
    Internal Designator: "Not Available"
    External Designator: "PS/2 Mouse"
    External Connector: 0x0f (PS/2)
  Inactive Record: #15
    Data 00: 7e 09 0f 00 01 00 02 0f 0d
    String 1: "Not Available"
    String 2: "PS/2 Keyboard"
  Inactive Record: #16
    Data 00: 7e 09 10 00 01 00 02 1f 1d
    String 1: "Not Available"
    String 2: "Line-Out Jack"
  Port Connector: #17
    Type: 0x1d (Audio Port)
    Internal Designator: "Not Available"
    External Designator: "Microphone Jack"
    External Connector: 0x1f (Mini-jack [headphones])
  Port Connector: #18
    Type: 0x1d (Audio Port)
    Internal Designator: "Not Available"
    External Designator: "Headphone Jack"
    External Connector: 0x1f (Mini-jack [headphones])
  Inactive Record: #19
    Data 00: 7e 09 13 00 01 00 02 ff 1c
    String 1: "Not Available"
    String 2: "Digital Video"
  Port Connector: #20
    Type: 0x1e (Modem Port)
    Internal Designator: "Not Available"
    External Designator: "Modem"
    External Connector: 0x0a (RJ-11)
  Port Connector: #21
    Type: 0x1f (Network Port)
    Internal Designator: "Not Available"
    External Designator: "Ethernet"
    External Connector: 0x0b (RJ-45)
  Port Connector: #22
    Type: 0x10 (USB)
    Internal Designator: "Not Available"
    External Designator: "USB 1"
    External Connector: 0x12 (Access Bus [USB])
  Port Connector: #23
    Type: 0x10 (USB)
    Internal Designator: "Not Available"
    External Designator: "USB 2"
    External Connector: 0x12 (Access Bus [USB])
  Port Connector: #24
    Type: 0x10 (USB)
    Internal Designator: "Not Available"
    External Designator: "USB 3"
    External Connector: 0x12 (Access Bus [USB])
  Port Connector: #25
    Type: 0x10 (USB)
    Internal Designator: "Not Available"
    External Designator: "USB 4"
    External Connector: 0x12 (Access Bus [USB])
  System Slot: #26
    Designation: "CardBus Slot 1"
    Type: 0x07 (PC Card [PCMCIA])
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x01 (Other)
    Slot ID: 0
    Characteristics: 0x03f6 (5.0 V, 3.3 V, PC Card-16, CardBus, Zoom Video, Modem Ring Resume, PME#, Hot-Plug)
  Inactive Record: #27
    Data 00: 7e 0d 1b 00 01 07 05 03 01 00 01 b6 03
    String 1: "CardBus Slot 3"
  Inactive Record: #28
    Data 00: 7e 0d 1c 00 01 07 05 03 01 01 01 b6 03
    String 1: "CardBus Slot 4"
  System Slot: #29
    Designation: "Mini-PCI Slot 1"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x03 (Available)
    Length: 0x01 (Other)
    Slot ID: 1
    Characteristics: 0x0506 (5.0 V, 3.3 V, PME#)
  Inactive Record: #30
    Data 00: 7e 0d 1e 00 01 06 05 03 03 02 00 06 05
    String 1: "PCI Slot 1"
  Inactive Record: #31
    Data 00: 7e 06 1f 00 81 01
    String 1: "IBM Embedded Security hardware"
  Language Info: #32
    Languages: enUS
    Current: enUS
  Type 15 Record: #33
    Data 00: 0f 19 21 00 10 00 00 00 10 00 04 02 00 00 00 00
    Data 10: 00 00 00 00 01 01 02 08 04
  Physical Memory Array: #34
    Use: 0x03 (System memory)
    Location: 0x03 (Motherboard)
    Slots: 2
    Max. Size: 3 GB
    ECC: 0x03 (None)
  Memory Device: #35
    Location: "DIMM 1"
    Bank: "Bank 0/1"
    Memory Array: #34
    Error Info: No Error
    Form Factor: 0x0d (SODIMM)
    Type: 0x12 (DDR)
    Type Detail: 0x0080 (Synchronous)
    Data Width: 64 bits
    Size: 1 GB
  Memory Device: #36
    Location: "DIMM 2"
    Bank: "Bank 2/3"
    Memory Array: #34
    Error Info: No Error
    Form Factor: 0x0d (SODIMM)
    Type: 0x12 (DDR)
    Type Detail: 0x0080 (Synchronous)
    Data Width: 64 bits
    Size: 1 GB
  32bit-Memory Error Info: #37
    Type: 0x03 (OK)
    Granularity: 0x02 (Unknown)
    Operation: 0x02 (Unknown)
  Memory Array Mapping: #38
    Memory Array: #34
    Partition Width: 2
    Start Address: 0x00000000
    End Address: 0x80000000
  Memory Device Mapping: #39
    Memory Device: #35
    Array Mapping: #38
    Row: 1
    Interleave Pos: 0
    Interleaved Depth: 0
    Start Address: 0x00000000
    End Address: 0x40000000
  Memory Device Mapping: #40
    Memory Device: #36
    Array Mapping: #38
    Row: 1
    Interleave Pos: 0
    Interleaved Depth: 0
    Start Address: 0x40000000
    End Address: 0x80000000
  Pointing Device: #41
    Type: 0x05 (Track Point)
    Interface: 0x04 (PS/2)
    Buttons: 3
  Hardware Security: #42
    Power-on Password: 0x00 (Disabled)
    Keyboard Password: 0x00 (Disabled)
    Admin Password: 0x00 (Disabled)
    Front Panel Reset: 0x03 (Unknown)
  Type 32 Record: #43
    Data 00: 20 0b 2b 00 00 00 00 00 00 00 00
  Type 131 Record: #44
    Data 00: 83 66 2c 00 01 00 00 00 00 01 72 03 40 00 ae 80
    Data 10: 00 02 00 00 00 00 00 2a 00 40 2a 00 00 00 00 00
    Data 20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
    Data 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
    Data 40: 00 00 00 00 00 00 00 00 00 00 16 00 80 16 00 00
    Data 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
    Data 60: 00 00 00 00 00 00
    String 1: "IBMCFGDATA"
  Inactive Record: #45
    Data 00: 7e 05 2d 00 01
    String 1: "KHOIHGIUCCHHII"
  Type 134 Record: #46
    Data 00: 86 0d 2e 00 16 10 05 20 00 00 00 00 00
  Type 131 Record: #47
    Data 00: 83 11 2f 00 01 02 03 ff ff 1f 00 00 00 00 00 02
    Data 10: 00
    String 1: "BOOTINF 20h"
    String 2: "BOOTDEV 21h"
    String 3: "KEYPTRS 23h"
  Type 132 Record: #48
    Data 00: 84 07 30 00 01 d8 36
  Config Status: cfg=new, avail=yes, need=no, active=unknown

02: None 00.2: 10002 LCD Monitor
  [Created at monitor.97]
  Unique ID: aHB6.UaXt0+SnMW6
  Hardware Class: monitor
  Model: "SAMSUNG LCD Monitor"
  Vendor: SEC "SAMSUNG"
  Device: eisa 0x0000 
  Resolution: 1400x1050@60Hz
  Size: 305x228 mm
  Year of Manufacture: 2003
  Week of Manufacture: 0
  Detailed Timings #0:
     Resolution: 1400x1050
     Horizontal: 1400 1448 1560 1688 (+48 +160 +288) -hsync
       Vertical: 1050 1051 1055 1066 (+1 +5 +16) -vsync
    Frequencies: 108.00 MHz, 63.98 kHz, 60.02 Hz
  Config Status: cfg=new, avail=yes, need=no, active=unknown[/FONT]

hhhmmm.... Evidently my KVM switch returns to computers that the screen is a SAMSUNG LCD Monitor with Resolution: 1400x1050@60Hz. Actually I have a 21" CRT attached with 1600x1200@85Hz. That is why I needed to use custom xorg.conf files with my CRT's EDID file specified.

Basically I need two different xorg.conf files:
1) Working at my desk with KVM attached 21" CRT attached with 1600x1200@85Hz.
2) Working with a projector type display at a lower resolution and 60Hz refresh.

The notebook LCD is correctly shown as: Resolution: 1400x1050@60.02hz

I am thankful,

---

### Post by him610 on 2016-05-07
Well, the output of *hwinfo --vbe *is not quite what I expected. I assume it is because yours is a laptop while mine is a desktop with attached monitor. Anyway, I think you have found a solution to your original problem. Nvidia driver 173.xx is no longer supported in LTS 16.04. Meefisto888 who seems to be more knowledgeable about Nvidia drivers than either of us, has recommended using the *nouveau* driver.


> Basically I need two different xorg.conf files:

No, I don't think it works like that; I don't believe you can use two xorg.conf files. You need one xorg.conf file that will handle all of your different outputs.

You should probably mark this thread as closed and open a new one addressing the requirements of your xorg.conf file  which will alert responders who know something about configuring xorg files to help with that issue.

---

### Post by mdlueck on 2016-05-14
> **him610 said:**
> Nvidia driver 173.xx is no longer supported in LTS 16.04. Meefisto888 who seems to be more knowledgeable about Nvidia drivers than either of us, has recommended using the *nouveau* driver.


I ended up reloading just my OS partition back to Xubuntu 14.04 and have everything working again as needed. I have again the Nvidia binary drivers working.

> **him610 said:**
> 
> Basically I need two different xorg.conf files: 

No, I don't think it works like that; I don't believe you can use two xorg.conf files. You need one xorg.conf file that will handle all of your different outputs.


The reason I have separate xorg.conf files is to support different display configurations:
1) Desktop use with 1600x1200x85hz screen (only running at 1400x1050 of the CRT's maximum resolution)
2) Presentation mode which usually projectors are only capable of 60hz refresh.

I simply copy in the correct xorg.conf / IPL / and away I go.

Problem solved / Xubuntu 14.04 will be the end of the line for this dependable system.

I am thankful,

---

