---
title: "Overclock monitor"
date: 2016-04-23
forum: Hardware
---

### Post by per_kllstrm on 2016-04-23
I have this monitor 60hz, wich can safely get clocked to 80hz.. it works fine in windows, but i dont seem to be able to get it goin in my xubuntu.
xubuntu 14.04 
kernel 4.2.0-35-generic
Nvidia driver 358.16

xrandr -q output:
```
Screen 0: minimum 8 x 8, current 6000 x 1440, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 connected 2560x1440+3440+0 (normal left inverted right x axis y axis) 527mm x 296mm
   2560x1440      60.0*+
   2048x1536      60.0  
   2048x1152      59.9  
   1920x1440      75.0     60.0  
   1920x1200      60.0     59.9  
   1920x1080      60.0     59.9     59.9     50.0     60.1     60.0  
   1856x1392      75.0     60.0  
   1792x1344      75.0     60.0  
   1680x1050      84.9     74.9     69.9     60.0     59.9  
   1600x1200      85.0     75.0     70.0     65.0     60.0  
   1440x900       59.9  
   1400x1050      85.0     74.8     70.0     60.0  
   1360x768       60.0     59.8  
   1280x1024      85.0     75.0     60.0  
   1280x960       85.0     60.0  
   1280x800       59.8  
   1280x720       60.0     59.9     50.0  
   1152x864       85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   960x600        60.0  
   960x540        60.0  
   840x525        85.0     75.0     69.9     60.0     59.9  
   832x624        74.6  
   800x600        85.1     75.0     72.2     60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   720x450        59.9  
   720x400        85.0  
   700x525        74.8     60.0  
   680x384        60.0     59.8  
   640x480        85.0     75.0     72.8     59.9     59.9  
   640x400        85.1  
   640x350        85.1  
   512x384        70.1     60.0  
   400x300        72.2  
   320x240        72.8     60.1  
   320x175        85.3  
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 connected 3440x1440+0+0 (normal left inverted right x axis y axis) 798mm x 335mm
   3440x1440      60.0*+   50.0  
   2560x1440      60.0  
   2560x1080      60.0  
   2048x1536      60.0  
   1920x1440      75.0     60.0  
   1920x1200      60.0  
   1920x1080      60.0     60.0     59.9     59.9     50.0     60.0  
   1856x1392      75.0     60.0  
   1792x1344      75.0     60.0  
   1720x1440      60.0  
   1680x1050      84.9     74.9     69.9     60.0     59.9  
   1600x1200      85.0     75.0     70.0     65.0     60.0  
   1440x900       59.9  
   1400x1050      85.0     74.8     70.0     60.0  
   1360x768       60.0     59.8  
   1280x1024      85.0     75.0     60.0  
   1280x960       85.0     60.0  
   1280x800       59.8  
   1280x720       59.9     50.0  
   1152x864       85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   960x600        60.0  
   960x540        60.0  
   840x525        85.0     75.0     69.9     60.0     59.9  
   832x624        74.6  
   800x600        85.1     75.0     72.2     60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   720x450        59.9  
   720x400        85.0  
   700x525        74.8     60.0  
   680x384        60.0     59.8  
   640x480        85.0     75.0     72.8     59.9     59.9  
   640x400        85.1  
   640x350        85.1  
   512x384        70.1     60.0  
   400x300        72.2  
   320x240        72.8     60.1  
   320x175        85.3  
DP-5 disconnected (normal left inverted right x axis y axis)
```

I have tried several ways one is
cvt 3440 1440 80
the output i get is: Modeline "3440x1440_80.00"  571.75  3440 3712 4088 4736  1440 1443 1453 1510 -hsync +vsync
then i type: xrandr --newmode "3440x1440_80.00"  571.75  3440 3712 4088 4736  1440 1443 1453 1510 -hsync +vsync
followed by:xrandr --addmode DP-4 "3440x1440_80.00"
here i start getting the problems:
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  47
  Current serial number in output stream:  48

```

Basically im trying to follow this guide: [http://www.monitortests.com/forum/Thread-Guide-to-Nvidia-monitor-overclocking-on-Linux](http://www.monitortests.com/forum/Thread-Guide-to-Nvidia-monitor-overclocking-on-Linux)
is there any other way i can do this or how do i fix the addmode error? searched google but havent really found an answer


EDIT:
forgot to post my xorg.conf
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL U3415W"
    HorizSync       29.0 - 113.0
    VertRefresh     49.0 - 86.0
    ModeLine       "3440x1440_80.00" 571.75 3440 3712 4088 4736 1440 1443 1453 1510 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 980 Ti"
    Option         "UseEDIDFreqs" "false"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ModeValidation" "AllowNonEdidModes,NoEdidMaxPClkCheck,NoMaxPClkCheck"
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-6"
    Option         "metamodes" "DP-4: 3440x1440_60 +0+0, DP-2: 2560x1440_60 +3440+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by him610 on 2016-05-01
How about posting the results of this command... (it will do no harm)

*sudo hwinfo --vbe*

It will allow us to see the capabilities of your gfxcard and monitor.

---

### Post by per_kllstrm on 2016-07-04
Sorry for the mega late reply....

```
01: None 00.0: 10105 BIOS                                         [Created at bios.186]
  Unique ID: rdCR.lZF+r4EgHp4
  Hardware Class: bios
  VESA BIOS Version: 3.0
  Current VESA Mode: 0x8118
  BIOS Keyboard LED Status:
    Scroll Lock: off
    Num Lock: off
    Caps Lock: off
  Base Memory: 626 kB
  PnP BIOS: @@@0000
  MP spec rev 1.4 info:
    OEM id: "A M I"
    Product id: "ALASKA"
    4 CPUs (0 disabled)
  SMBIOS Version: 3.0
  BIOS Info: #0
    Vendor: "American Megatrends Inc."
    Version: "1.90"
    Date: "05/11/2016"
    Start Address: 0xf0000
    ROM Size: 16384 kB
    Features: 0x0d03000000013f8b9880
      PCI supported
      BIOS flashable
      BIOS shadowing allowed
      CD boot supported
      Selectable boot supported
      BIOS ROM socketed
      EDD spec supported
      1.2MB Floppy supported
      720kB Floppy supported
      2.88MB Floppy supported
      Print Screen supported
      8042 Keyboard Services supported
      Serial Services supported
      Printer Services supported
      ACPI supported
      USB Legacy supported
      BIOS Boot Spec supported
  System Info: #1
    Manufacturer: "MSI"
    Product: "MS-7984"
    Version: "1.0"
    Serial: "Default string"
    UUID: undefined, but settable
    Wake-up: 0x06 (Power Switch)
  Board Info: #2
    Manufacturer: "MSI"
    Product: "Z170A GAMING PRO (MS-7984)"
    Version: "1.0"
    Serial: "F916276646"
    Asset Tag: "Default string"
    Type: 0x0a (Motherboard)
    Features: 0x09
      Hosting Board
      Replaceable
    Location: "Default string"
    Chassis: #3
  Chassis Info: #3
    Manufacturer: "MSI"
    Version: "1.0"
    Serial: "Default string"
    Asset Tag: "Default string"
    Type: 0x03 (Desktop)
    Bootup State: 0x03 (Safe)
    Power Supply State: 0x03 (Safe)
    Thermal State: 0x03 (Safe)
    Security Status: 0x03 (None)
  Port Connector: #4
    Type: 0x0e (Mouse Port)
    Internal Designator: "J1A1"
    External Designator: "PS2Mouse"
    External Connector: 0x0f (PS/2)
  Port Connector: #5
    Type: 0x0d (Keyboard Port)
    Internal Designator: "J1A1"
    External Designator: "Keyboard"
    External Connector: 0x0f (PS/2)
  Port Connector: #6
    Type: 0xff (Other)
    Internal Designator: "J2A1"
    External Designator: "TV Out"
    External Connector: 0x1d (Mini-Centronics Type-14)
  Port Connector: #7
    Type: 0x09 (Serial Port 16550A Compatible)
    Internal Designator: "J2A2A"
    External Designator: "COM A"
    External Connector: 0x08 (DB-9 pin male)
  Port Connector: #8
    Type: 0x1c (Video Port)
    Internal Designator: "J2A2B"
    External Designator: "Video"
    External Connector: 0x07 (DB-15 pin female)
  Port Connector: #9
    Type: 0x10 (USB)
    Internal Designator: "J3A1"
    External Designator: "USB1"
    External Connector: 0x12 (Access Bus [USB])
  Port Connector: #10
    Type: 0xff (Other)
    Internal Designator: "J9A1 - TPM HDR"
    Internal Connector: 0xff (Other)
  Port Connector: #11
    Type: 0xff (Other)
    Internal Designator: "J9C1 - PCIE DOCKING CONN"
    Internal Connector: 0xff (Other)
  Port Connector: #12
    Type: 0xff (Other)
    Internal Designator: "J2B3 - CPU FAN"
    Internal Connector: 0xff (Other)
  Port Connector: #13
    Type: 0xff (Other)
    Internal Designator: "J6C2 - EXT HDMI"
    Internal Connector: 0xff (Other)
  Port Connector: #14
    Type: 0xff (Other)
    Internal Designator: "J3C1 - GMCH FAN"
    Internal Connector: 0xff (Other)
  Port Connector: #15
    Type: 0xff (Other)
    Internal Designator: "J1D1 - ITP"
    Internal Connector: 0xff (Other)
  Port Connector: #16
    Type: 0xff (Other)
    Internal Designator: "J9E2 - MDC INTPSR"
    Internal Connector: 0xff (Other)
  Port Connector: #17
    Type: 0xff (Other)
    Internal Designator: "J9E4 - MDC INTPSR"
    Internal Connector: 0xff (Other)
  Port Connector: #18
    Type: 0xff (Other)
    Internal Designator: "J9E3 - LPC HOT DOCKING"
    Internal Connector: 0xff (Other)
  Port Connector: #19
    Type: 0xff (Other)
    Internal Designator: "J9E1 - SCAN MATRIX"
    Internal Connector: 0xff (Other)
  Port Connector: #20
    Type: 0xff (Other)
    Internal Designator: "J9G1 - LPC SIDE BAND"
    Internal Connector: 0xff (Other)
  Port Connector: #21
    Type: 0xff (Other)
    Internal Designator: "J8F1 - UNIFIED"
    Internal Connector: 0xff (Other)
  Port Connector: #22
    Type: 0xff (Other)
    Internal Designator: "J6F1 - LVDS"
    Internal Connector: 0xff (Other)
  Port Connector: #23
    Type: 0xff (Other)
    Internal Designator: "J2F1 - LAI FAN"
    Internal Connector: 0xff (Other)
  Port Connector: #24
    Type: 0xff (Other)
    Internal Designator: "J2G1 - GFX VID"
    Internal Connector: 0xff (Other)
  Port Connector: #25
    Type: 0xff (Other)
    Internal Designator: "J1G6 - AC JACK"
    Internal Connector: 0xff (Other)
  System Slot: #26
    Designation: "J6B2"
    Type: 0xa5 (Other)
    Bus Width: 0x0d (Other)
    Status: 0x04 (In Use)
    Length: 0x04 (Long)
    Slot ID: 0
    Characteristics: 0x010c (3.3 V, Shared, PME#)
  System Slot: #27
    Designation: "J6B1"
    Type: 0xa5 (Other)
    Bus Width: 0x08 (Other)
    Status: 0x04 (In Use)
    Length: 0x03 (Short)
    Slot ID: 1
    Characteristics: 0x010c (3.3 V, Shared, PME#)
  System Slot: #28
    Designation: "J6D1"
    Type: 0xa5 (Other)
    Bus Width: 0x08 (Other)
    Status: 0x04 (In Use)
    Length: 0x03 (Short)
    Slot ID: 2
    Characteristics: 0x010c (3.3 V, Shared, PME#)
  System Slot: #29
    Designation: "J7B1"
    Type: 0xa5 (Other)
    Bus Width: 0x08 (Other)
    Status: 0x04 (In Use)
    Length: 0x03 (Short)
    Slot ID: 3
    Characteristics: 0x010c (3.3 V, Shared, PME#)
  System Slot: #30
    Designation: "J8B4"
    Type: 0xa5 (Other)
    Bus Width: 0x08 (Other)
    Status: 0x04 (In Use)
    Length: 0x03 (Short)
    Slot ID: 4
    Characteristics: 0x010c (3.3 V, Shared, PME#)
  System Slot: #31
    Designation: "J8D1"
    Type: 0xa5 (Other)
    Bus Width: 0x08 (Other)
    Status: 0x04 (In Use)
    Length: 0x03 (Short)
    Slot ID: 5
    Characteristics: 0x010c (3.3 V, Shared, PME#)
  System Slot: #32
    Designation: "J8B3"
    Type: 0x06 (PCI)
    Bus Width: 0x05 (32 bit)
    Status: 0x04 (In Use)
    Length: 0x03 (Short)
    Slot ID: 6
    Characteristics: 0x010c (3.3 V, Shared, PME#)
  OEM Strings: #33
    Default string
  System Config Options (Jumpers & Switches) #34:
    Default string
  Type 32 Record: #35
    Data 00: 20 14 23 00 00 00 00 00 00 00 00 00 00 00 00 00
    Data 10: 00 00 00 00
  Type 34 Record: #36
    Data 00: 22 0b 24 00 01 04 00 00 00 00 03
    String 1: "LM78-1"
  Type 26 Record: #37
    Data 00: 1a 16 25 00 01 67 00 80 00 80 00 80 00 80 00 80
    Data 10: 00 00 00 00 00 80
    String 1: "LM78A"
  Type 36 Record: #38
    Data 00: 24 10 26 00 01 00 02 00 03 00 04 00 05 00 06 00
  Type 35 Record: #39
    Data 00: 23 0b 27 00 01 24 00 25 00 26 00
    String 1: "Default string"
  Type 28 Record: #40
    Data 00: 1c 16 28 00 01 67 00 80 00 80 00 80 00 80 00 80
    Data 10: 00 00 00 00 00 80
    String 1: "LM78A"
  Type 36 Record: #41
    Data 00: 24 10 29 00 01 00 02 00 03 00 04 00 05 00 06 00
  Type 35 Record: #42
    Data 00: 23 0b 2a 00 01 24 00 28 00 29 00
    String 1: "Default string"
  Type 27 Record: #43
    Data 00: 1b 0f 2b 00 28 00 67 01 00 00 00 00 00 80 01
    String 1: "Cooling Dev 1"
  Type 36 Record: #44
    Data 00: 24 10 2c 00 01 00 02 00 03 00 04 00 05 00 06 00
  Type 35 Record: #45
    Data 00: 23 0b 2d 00 01 24 00 2b 00 2c 00
    String 1: "Default string"
  Type 27 Record: #46
    Data 00: 1b 0f 2e 00 28 00 67 01 00 00 00 00 00 80 00
  Type 36 Record: #47
    Data 00: 24 10 2f 00 01 00 02 00 03 00 04 00 05 00 06 00
  Type 35 Record: #48
    Data 00: 23 0b 30 00 01 24 00 2e 00 2f 00
    String 1: "Default string"
  Type 29 Record: #49
    Data 00: 1d 16 31 00 01 67 00 80 00 80 00 80 00 80 00 80
    Data 10: 00 00 00 00 00 80
    String 1: "ABC"
  Type 36 Record: #50
    Data 00: 24 10 32 00 00 80 00 80 00 80 00 80 00 80 00 80
  Type 35 Record: #51
    Data 00: 23 0b 33 00 01 24 00 31 00 32 00
    String 1: "Default string"
  Type 26 Record: #52
    Data 00: 1a 16 34 00 01 6a 00 80 00 80 00 80 00 80 00 80
    Data 10: 00 00 00 00 00 80
    String 1: "LM78A"
  Type 28 Record: #53
    Data 00: 1c 16 35 00 01 6a 00 80 00 80 00 80 00 80 00 80
    Data 10: 00 00 00 00 00 80
    String 1: "LM78A"
  Type 27 Record: #54
    Data 00: 1b 0f 36 00 35 00 67 01 00 00 00 00 00 80 01
    String 1: "Cooling Dev 1"
  Type 29 Record: #55
    Data 00: 1d 16 37 00 01 6a 00 80 00 80 00 80 00 80 00 80
    Data 10: 00 00 00 00 00 80
    String 1: "ABC"
  Type 39 Record: #56
    Data 00: 27 16 38 00 01 01 02 03 04 05 06 07 00 80 a2 11
    Data 10: 34 00 36 00 37 00
    String 1: "To Be Filled By O.E.M."
    String 2: "To Be Filled By O.E.M."
    String 3: "To Be Filled By O.E.M."
    String 4: "To Be Filled By O.E.M."
    String 5: "To Be Filled By O.E.M."
    String 6: "To Be Filled By O.E.M."
    String 7: "To Be Filled By O.E.M."
  Type 41 Record: #57
    Data 00: 29 0b 39 00 01 83 01 00 00 00 10
    String 1: "Onboard IGD"
  Type 41 Record: #58
    Data 00: 29 0b 3a 00 01 85 01 00 00 00 c8
    String 1: "Onboard LAN"
  Type 41 Record: #59
    Data 00: 29 0b 3b 00 01 81 01 00 00 03 e2
    String 1: "Onboard 1394"
  Cache Info: #60
    Designation: "L1 Cache"
    Level: L1
    State: Enabled
    Mode: 0x01 (Write Back)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x04 (Parity)
    Type: 0x04 (Data)
    Associativity: 0x07 (8-way Set-Associative)
    Max. Size: 128 kB
    Current Size: 128 kB
    Supported SRAM Types: 0x0020 (Synchronous)
    Current SRAM Type: 0x0020 (Synchronous)
  Cache Info: #61
    Designation: "L1 Cache"
    Level: L1
    State: Enabled
    Mode: 0x01 (Write Back)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x04 (Parity)
    Type: 0x03 (Instruction)
    Associativity: 0x07 (8-way Set-Associative)
    Max. Size: 128 kB
    Current Size: 128 kB
    Supported SRAM Types: 0x0020 (Synchronous)
    Current SRAM Type: 0x0020 (Synchronous)
  Cache Info: #62
    Designation: "L2 Cache"
    Level: L2
    State: Enabled
    Mode: 0x01 (Write Back)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x05 (Single-bit)
    Type: 0x05 (Unified)
    Associativity: 0x05 (4-way Set-Associative)
    Max. Size: 1024 kB
    Current Size: 1024 kB
    Supported SRAM Types: 0x0020 (Synchronous)
    Current SRAM Type: 0x0020 (Synchronous)
  Cache Info: #63
    Designation: "L3 Cache"
    Level: L3
    State: Enabled
    Mode: 0x01 (Write Back)
    Location: 0x00 (Internal, Not Socketed)
    ECC: 0x06 (Multi-bit)
    Type: 0x05 (Unified)
    Associativity: 0x08 (16-way Set-Associative)
    Max. Size: 8192 kB
    Current Size: 8192 kB
    Supported SRAM Types: 0x0020 (Synchronous)
    Current SRAM Type: 0x0020 (Synchronous)
  Processor Info: #64
    Socket: "U3E1"
    Socket Type: 0x01 (Other)
    Socket Status: Populated
    Type: 0x03 (CPU)
    Family: 0xc6 (Other)
    Manufacturer: "Intel(R) Corporation"
    Version: "Intel(R) Core(TM) i7-6700K CPU @ 4.00GHz"
    Serial: "To Be Filled By O.E.M."
    Asset Tag: "To Be Filled By O.E.M."
    Part Number: "To Be Filled By O.E.M."
    Processor ID: 0xbfebfbff000506e3
    Status: 0x01 (Enabled)
    Voltage: 1.2 V
    External Clock: 100 MHz
    Max. Speed: 8300 MHz
    Current Speed: 4600 MHz
    L1 Cache: #61
    L2 Cache: #62
    L3 Cache: #63
  Physical Memory Array: #65
    Use: 0x03 (System memory)
    Location: 0x03 (Motherboard)
    Slots: 4
    Max. Size: 64 GB
    ECC: 0x03 (None)
  Memory Device: #66
    Location: "ChannelA-DIMM0"
    Bank: "BANK 0"
    Manufacturer: "0215"
    Serial: "00000000"
    Asset Tag: "9876543210"
    Part Number: "CMK16GX4M2A2400C14"
    Memory Array: #65
    Form Factor: 0x09 (DIMM)
    Type: 0x1a (Other)
    Type Detail: 0x0080 (Synchronous)
    Data Width: 64 bits
    Size: 8 GB
    Speed: 2400 MHz
  Memory Device: #67
    Location: "ChannelA-DIMM1"
    Bank: "BANK 1"
    Manufacturer: "0215"
    Serial: "00000000"
    Asset Tag: "9876543210"
    Part Number: "CMK16GX4M2A2400C14"
    Memory Array: #65
    Form Factor: 0x09 (DIMM)
    Type: 0x1a (Other)
    Type Detail: 0x0080 (Synchronous)
    Data Width: 64 bits
    Size: 8 GB
    Speed: 2400 MHz
  Memory Device: #68
    Location: "ChannelB-DIMM0"
    Bank: "BANK 2"
    Manufacturer: "0215"
    Serial: "00000000"
    Asset Tag: "9876543210"
    Part Number: "CMK16GX4M2A2400C14"
    Memory Array: #65
    Form Factor: 0x09 (DIMM)
    Type: 0x1a (Other)
    Type Detail: 0x0080 (Synchronous)
    Data Width: 64 bits
    Size: 8 GB
    Speed: 2400 MHz
  Memory Device: #69
    Location: "ChannelB-DIMM1"
    Bank: "BANK 3"
    Manufacturer: "0215"
    Serial: "00000000"
    Asset Tag: "9876543210"
    Part Number: "CMK16GX4M2A2400C14"
    Memory Array: #65
    Form Factor: 0x09 (DIMM)
    Type: 0x1a (Other)
    Type Detail: 0x0080 (Synchronous)
    Data Width: 64 bits
    Size: 8 GB
    Speed: 2400 MHz
  Memory Array Mapping: #70
    Memory Array: #65
    Partition Width: 4
    Start Address: 0x0000000000000000
    End Address: 0x0000000800000000
  Memory Device Mapping: #71
    Memory Device: #66
    Array Mapping: #70
    Interleave Pos: 1
    Interleaved Depth: 2
    Start Address: 0x0000000000000000
    End Address: 0x0000000200000000
  Memory Device Mapping: #72
    Memory Device: #67
    Array Mapping: #70
    Interleave Pos: 1
    Interleaved Depth: 2
    Start Address: 0x0000000400000000
    End Address: 0x0000000600000000
  Memory Device Mapping: #73
    Memory Device: #68
    Array Mapping: #70
    Interleave Pos: 2
    Interleaved Depth: 2
    Start Address: 0x0000000200000000
    End Address: 0x0000000400000000
  Memory Device Mapping: #74
    Memory Device: #69
    Array Mapping: #70
    Interleave Pos: 2
    Interleaved Depth: 2
    Start Address: 0x0000000600000000
    End Address: 0x0000000800000000
  Type 130 Record: #75
    Data 00: 82 14 4b 00 24 41 4d 54 00 00 00 00 00 a5 af 02
    Data 10: c0 00 00 00
  Type 131 Record: #76
    Data 00: 83 40 4c 00 31 00 00 00 00 00 00 00 00 00 00 00
    Data 10: f8 00 45 a1 00 00 00 00 01 00 00 00 00 00 0b 00
    Data 20: ea 03 0a 00 00 00 00 00 fe 00 b8 15 00 00 00 00
    Data 30: 00 00 00 00 22 00 00 00 76 50 72 6f 00 00 00 00
  Type 221 Record: #77
    Data 00: dd 1a 4d 00 03 01 00 01 09 00 00 00 02 00 00 00
    Data 10: 00 84 00 03 00 00 05 00 00 00
    String 1: "Reference Code - CPU"
    String 2: "uCode Version"
    String 3: "TXT ACM version"
  Type 221 Record: #78
    Data 00: dd 1a 4e 00 03 01 00 01 09 00 00 00 02 00 01 09
    Data 10: 00 00 00 03 04 0b 00 0a ea 03
    String 1: "Reference Code - ME 11.0"
    String 2: "MEBx version"
    String 3: "ME Firmware Version"
    String 4: "Consumer SKU"
  Type 221 Record: #79
    Data 00: dd 44 4f 00 09 01 00 01 09 00 00 00 02 03 ff ff
    Data 10: ff ff ff 04 00 ff ff ff 31 00 05 00 ff ff ff 31
    Data 20: 00 06 00 ff ff ff ff ff 07 00 3e 00 00 00 00 08
    Data 30: 00 34 00 00 00 00 09 00 3e 00 00 00 00 0a 00 34
    Data 40: 00 00 00 00
    String 1: "Reference Code - SKL PCH"
    String 2: "PCH-CRID Status"
    String 3: "Disabled"
    String 4: "PCH-CRID Original Value"
    String 5: "PCH-CRID New Value"
    String 6: "OPROM - RST - RAID"
    String 7: "SKL PCH H Bx Hsio Version"
    String 8: "SKL PCH H Dx Hsio Version"
    String 9: "SKL PCH LP Bx Hsio Version"
    String 10: "SKL PCH LP Cx Hsio Version"
  Type 221 Record: #80
    Data 00: dd 36 50 00 07 01 00 01 09 00 00 00 02 00 01 09
    Data 10: 00 00 00 03 00 01 09 00 00 00 04 05 ff ff ff ff
    Data 20: ff 06 00 ff ff ff 07 00 07 00 ff ff ff 07 00 08
    Data 30: 00 ff ff ff 00 00
    String 1: "Reference Code - SA - System Agent"
    String 2: "Reference Code - MRC"
    String 3: "SA - PCIe Version"
    String 4: "SA-CRID Status"
    String 5: "Disabled"
    String 6: "SA-CRID Original Value"
    String 7: "SA-CRID New Value"
    String 8: "OPROM - VBIOS"
  Type 221 Record: #81
    Data 00: dd 60 51 00 0d 01 00 00 00 00 a6 00 02 00 ff ff
    Data 10: ff ff ff 03 04 ff ff ff ff ff 05 06 ff ff ff ff
    Data 20: ff 07 08 ff ff ff ff ff 09 00 00 00 00 00 00 0a
    Data 30: 00 ff ff ff ff ff 0b 00 ff ff 00 00 00 0c 00 ff
    Data 40: ff ff ff ff 0d 00 ff ff ff ff ff 0e 00 ff ff ff
    Data 50: ff ff 0f 00 ff ff ff ff ff 10 11 01 02 02 01 01
    String 1: "Lan Phy Version"
    String 2: "Sensor Firmware Version"
    String 3: "Debug Mode Status"
    String 4: "Enabled"
    String 5: "Performance Mode Status"
    String 6: "Disabled"
    String 7: "Debug Use USB(Disabled:Serial)"
    String 8: "Disabled"
    String 9: "ICC Overclocking Version"
    String 10: "UNDI Version"
    String 11: "EC FW Version"
    String 12: "GOP Version"
    String 13: "BIOS Guard Version"
    String 14: "Base EC FW Version"
    String 15: "EC-EC Protocol Version"
    String 16: "Royal Park Version"
    String 17: "BP1.2.2.1_RP01"
  Type 136 Record: #82
    Data 00: 88 06 52 00 00 00
  Group Associations: #83
    Group Name: "Firmware Version Info"
    Items: #77, #78, #79, #80, #81
  Type 143 Record: #84
    Data 00: 8f 10 54 00 00 01 02 03 04 05 06 07 08 09 0a 0b
    String 1: "MEFW-11.0.10.1002"
    String 2: "VBIOS-0000"
    String 3: "PXEL1-v0.1.04"
    String 4: "AMI-AptioV"
    String 5: "GSES-5/1"
    String 6: "N/A"
    String 7: "N/A"
    String 8: "N/A"
    String 9: "N/A"
    String 10: "N/A"
    String 11: "N/A"
    String 12: "N/A"
  Type 144 Record: #85
    Data 00: 90 05 55 00 01
    String 1: "$INT15SWIDd0"
  Group Associations: #86
    Group Name: "$MEI"
    Items: #0
  Type 219 Record: #87
    Data 00: db 51 57 00 01 03 01 55 02 00 90 06 03 00 66 00
    Data 10: 02 00 00 00 40 08 00 00 00 00 00 02 00 00 00 02
    Data 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
    Data 30: ff ff ff ff ff ff ff ff 03 00 00 00 80 00 00 00
    Data 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
    Data 50: 00
    String 1: "MEI1"
    String 2: "MEI2"
    String 3: "MEI3"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.459]
  Unique ID: rdCR.Zxin6WTMOrB
  Hardware Class: framebuffer
  Model: "NVIDIA GM200 Board"
  Vendor: "NVIDIA Corporation"
  Device: "GM200 Board"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 16 MB
  Memory Range: 0xd1000000-0xd1ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown


03: None 00.2: 10002 LCD Monitor
  [Created at monitor.97]
  Unique ID: aHB6.y_I4XQ_B828
  Hardware Class: monitor
  Model: "DELL U3415W"
  Vendor: DEL "DELL"
  Device: eisa 0xa0a7 "DELL U3415W"
  Serial ID: "68MCF5CF06FL"
  Resolution: 720x400@70Hz
  Resolution: 640x480@60Hz
  Resolution: 640x480@75Hz
  Resolution: 800x600@60Hz
  Resolution: 800x600@75Hz
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@75Hz
  Resolution: 1280x1024@75Hz
  Resolution: 1152x864@75Hz
  Resolution: 1280x1024@60Hz
  Resolution: 1600x1200@60Hz
  Resolution: 3440x1440@60Hz
  Size: 798x335 mm
  Year of Manufacture: 2015
  Week of Manufacture: 51
  Detailed Timings #0:
     Resolution: 3440x1440
     Horizontal: 3440 3520 3552 3600 (+80 +112 +160) -hsync
       Vertical: 1440 1468 1478 1481 (+28 +38 +41) +vsync
    Frequencies: 319.75 MHz, 88.82 kHz, 59.97 Hz
  Driver Info #0:
    Max. Resolution: 3440x1440
    Vert. Sync Range: 48-85 Hz
    Hor. Sync Range: 30-89 kHz
    Bandwidth: 319 MHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown



```

---

### Post by him610 on 2016-07-05
This is what your monitor is capable of displaying. Highest frequency is 75Hz at fairly low resolution.

>  Resolution: 720x400@70Hz
  Resolution: 640x480@60Hz
  Resolution: 640x480@75Hz
  Resolution: 800x600@60Hz
  Resolution: 800x600@75Hz
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@75Hz
  Resolution: 1280x1024@75Hz
  Resolution: 1152x864@75Hz
  Resolution: 1280x1024@60Hz
  Resolution: 1600x1200@60Hz
  Resolution: 3440x1440@60Hz


This is probably not the answer you were looking for, but your equipment will probably last longer if you do not overstress it.

---

### Post by per_kllstrm on 2016-07-06
yea, its capable of that... but i run it in 3440x1440 @ 80hz in windows with no issues whatsoever thats why i want to overclock it

---

### Post by per_kllstrm on 2016-07-07
And i get this freakin flickering when watching youtube and scrolling on long webpages... same problem in firefox, chrome and vivaldi... was hoping higher hz would smooth that out

---

### Post by banceu_sergiu_ione on 2016-07-07
> **per_kllstrm said:**
> And i get this freakin flickering when watching youtube and scrolling on long webpages... same problem in firefox, chrome and vivaldi... was hoping higher hz would smooth that out

For firefox, Check if your graphic acceleration is enable 
type in a tab: about:support
and check under Graphics if GPU acceleration is set as 1/1. If is 0/1 then its off.
to set it on type in a new tab: about:config
search for :
layers.acceleration.force-enabled - set to true

layers.offmainthreadcomposition.enabled - set to true (default)

restart firefox and check if you still have the flickering

if you do, then try set off the hardware acceleration from Menu/Preferences/Advanced/General. restart firefox check it

---

