---
title: "Hard drive is running hot in Ubuntu 9.10"
date: 2010-03-01
forum: Hardware
---

### Post by Linuxperiment on 2010-03-01
EDIT: My HD in Ubuntu 9.10 runs at 47 Deg. I understand that operating temperature is within 0-60 Deg, but why does this hard drive run hotter than it does in Windows? I'm hoping there is a way I can allow it to run cooler. For a point of reference, the hard drive usually ran between 37 and 42 Deg in Windows (XP, Vista, 7). The palm rest area/hard drive area is warm to the touch, which is very different from the usual.

EDIT #2: I've solved the problem a bit by changing the hdparm settings, but I'm trying to make the hdparm settings permanent if they aren't already. I've searched about this and I'm trying to make sure I don't screw anything up. When I type in the following into the terminal:

sudo hdparm -M 128 /dev/sda

Are the changes permanent, even if I restart? If not, how can I make sure it is permanent? I've read of going into the /etc/hdparm.conf file and editing it, but what exactly do I type and where should it be put in the file? Thanks in advance for help!

My laptop specs:
160GB 5400 RPM Western Digital Hard Drive
Intel Pentium Dual Core 2.0 GHZ
2 GB RAM
Intel X3100 Integrated Graphics

Why is it that my hard drive runs so hot? This was not an issue with Windows XP, Vista, or 7. I have not tested 9.04 or anything before this yet, but this bothers me...

---

### Post by mikewhatever on 2010-03-01
And by 'running so hot' you mean what exactly?
Moderately hot?
Rather hot?
Quite hot?
Very hot?
Too hot to handle?
Boiling hot?
Insanely hot?

Perhaps giving a temperature reading would be a good idea for this help request.

---

### Post by Linuxperiment on 2010-03-01
47 Deg. I understand that operating temperature is within 0-60 Deg, but why does this hard drive run hotter than it does in Windows? I'm hoping there is a way I can allow it to run cooler.

EDIT: For a point of reference, the hard drive usually ran between 37 and 42 Deg in Windows (XP, Vista, 7). The palm rest area/hard drive area is warm to the touch, which is very different from the usual.

---

### Post by Yellow Pasque on 2010-03-01
What's the temp reading in Windows or maybe even in the BIOS?

---

### Post by Linuxperiment on 2010-03-01
I edited my previous post to be more clear.

---

### Post by Linuxperiment on 2010-03-01
Basically what I'm asking is, is there a way I can limit I/O activity or activate hard drive power saving features?

---

### Post by mikewhatever on 2010-03-01
Sure, look at 'hdparm --help'.

Perhaps changing the acoustic value will make it both cooler and quieter.

_example_
sudo hdparm -M 128 /dev/sda

---

### Post by Linuxperiment on 2010-03-01
Ok I'll change it to that and see if it does anything. I'm not sure what the default setting was. Does it usually default on the highest number (254)?

---

### Post by Linuxperiment on 2010-03-01
Ok some decent news. It's running at around 42 deg now. I'm thinking that this setting helped a decent bit. The default must have been pretty high (or even at maximum 254). What does this setting alteration actually do? IE: What does it tell the hard drive, or what does it do for the hard drive?

---

### Post by mikewhatever on 2010-03-01
Yes, the acoustic value on AC defaults to the highest, 254. I think what it does, is spins faster, thus generating more heat. Obviously, the faster it spins, the quicker data gets handled.

---

### Post by Linuxperiment on 2010-03-02
Ok, I'm trying to make the hdparm settings permanent if they aren't already. I've searched about this and I'm trying to make sure I don't screw anything up. When I type in the following into the terminal:

sudo hdparm -M 128 /dev/sda

Are the changes permanent, even if I restart? If not, how can I make sure it is permanent? I've read of going into the /etc/hdparm.conf file and editing it, but what exactly do I type and where should it be put in the file? Thanks in advance for help!

---

### Post by mikewhatever on 2010-03-02
That particular setting seems to be permanent without adding anything anywhere. You can check after rebooting with

sudo hdparm -I /dev/sda | grep -i acoustic

---

### Post by Linuxperiment on 2010-03-02
Yeah I just checked it right now after rebooting my computer. It is still at 128. I have to check if it changes after suspend, a/c power and battery ,etc.

thanks!

---

### Post by abdusamed on 2010-10-30
I can't change mine though with the help of laptop-mode-tools.. i was able stop it spinning all the time but it still averages around 50 degree!!!!! I know its hot.

this is what i get after run the acoustic command
```

~$ sudo hdparm -M 128 /dev/sda

/dev/sda:
 setting acoustic management to 128
 HDIO_DRIVE_CMD:ACOUSTIC failed: Input/output error
 HDIO_DRIVE_CMD(identify) failed: Input/output error
~$ 

```

This the info on it

Note I have two physic HD

```

bahie@bahie-laptop:~$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
    Model Number:       TOSHIBA MK4058GSX                       
    Serial Number:      Y8UBP1H0T
    Firmware Revision:  FF011M  
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
    Supported: 8 7 6 5 
    Likely used: 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors:  781422768
    Logical  Sector size:                   512 bytes
    Physical Sector size:                   512 bytes
    device size with M = 1024*1024:      381554 MBytes
    device size with M = 1000*1000:      400088 MBytes (400 GB)
    cache/buffer size  = 8192 KBytes
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: 254
    DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
       *    Advanced Power Management feature set
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    64-bit World wide name
       *    IDLE_IMMEDIATE with UNLOAD
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    Idle-Unload when NCQ is active
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
    not    supported: enhanced erase
    166min for SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 5000039162685611
    NAA        : 5
    IEEE OUI    : 000039
    Unique ID    : 162685611
Checksum: correct
bahie@bahie-laptop:~$ sudo hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
    Model Number:       TOSHIBA MK3252GSX                       
    Serial Number:      Y8I9COUQT
    Firmware Revision:  LV010M  
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
    Supported: 8 7 6 5 
    Likely used: 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors:  625142448
    Logical  Sector size:                   512 bytes
    Physical Sector size:                   512 bytes
    device size with M = 1024*1024:      305245 MBytes
    device size with M = 1000*1000:      320072 MBytes (320 GB)
    cache/buffer size  = 8192 KBytes
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: 254
    DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
       *    Advanced Power Management feature set
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    64-bit World wide name
       *    IDLE_IMMEDIATE with UNLOAD
       *    Gen1 signaling speed (1.5Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    Idle-Unload when NCQ is active
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
    not    supported: enhanced erase
    130min for SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 50000391637048df
    NAA        : 5
    IEEE OUI    : 000039
    Unique ID    : 1637048df
Checksum: correct

```

---

### Post by Jimtheplanner on 2010-10-30
Hi Folks,

This is a similar post to [http://ubuntuforums.org/showthread.php?t=1600307](http://ubuntuforums.org/showthread.php?t=1600307)

I did a back to back clean install between 10.10 and Mandriva 2010.1 just to prove my hardware. I found that Mandriva was a cool 40 deg C where 10.10 was cooking my hardware at good 10+ Degs C higher.

Jim

---

### Post by abdusamed on 2010-10-30
this is the solution worked for me [http://colorfulcuriosities.blogspot.com/2008/05/ubuntu-hard-drive-cycle-linux-only.html](http://colorfulcuriosities.blogspot.com/2008/05/ubuntu-hard-drive-cycle-linux-only.html)

After reading the blog.. don't do anything but do as the first comments talks about laptop-mode-tools. I have experience with it and always stick to it for any HDD modification

---

