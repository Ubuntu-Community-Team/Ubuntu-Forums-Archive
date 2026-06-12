---
title: "Boot-up Errors..."
date: 2008-07-21
forum: General Help
---

### Post by Nybb on 2008-07-21
Ok, here's the story. I'm a very new Ubuntu/Linux user. I recently made a drastic switch with both my desktop and my laptop and put them both fully to Ubuntu with basically no prior Linux experience. I am moderately competent with computers in general, and I figured the best way to learn quickly would be to just dive in.

I later came to the conclusion that this was silly, and decided to settle for an Ubuntu/XP dual boot on both computers. I followed [this tutorial]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") and it worked perfectly fine on my desktop (which I'm using to type this). I then went about doing the same thing on the laptop (which is a Lenovo Thinkpad T61 if that matters).

The problem occurred when I told the lappy to make room for the new partition and shrink down the old one. An error came up, and the details window said something along the lines of, I can't expand the new partition, its already the correct size, or something like that. I looked at the other details and concluded (incorrectly in retrospect) that all it had done so far was check the hard drive for errors, and no changes had really been made before the partitioning was halted by the error.

I then proceeded to restart the laptop (an old Windows habit, lol) and try running the partition editor again. It appeared to work, so I shut it down and put in the XP disk. Upon booting with XP, it said that it couldn't install anything because there was no hard drive detected. I tried booting normally to Ubuntu (not off the CD) and during bootup about a bazillion messages came up about DRDY ERROR and some numbers and stuff and it just seemed to go on forever, either telling me about the same error over and over, or finding an absurd number of errors.

It just kept going and I didn't see any way to stop it, so I forced the computer to shut down and I haven't touched it since. 

Any recommendations?

---

### Post by ajmorris on 2008-07-22
hi there,
which partitioning tool did you use to partition your hard disk?
When you boot into the ubuntu live cd, can you please post the output of ```
sudo fdisk -l
```
and also the output of hdparm -I <your hard disk>

AJ

---

### Post by Nybb on 2008-07-22
Thanks for the response.

I used the regular partition editor that was available while booting from the Ubuntu disk (GParted, I believe).

As for the first part:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b0e4893

Device Boot      Start      End      Blocks     ID   System
/dev/sda1  *         1    13250   106430593+    83   Linux
/dev/sda2        18663    19457     6385837+     5   Extended
/dev/sda5        18663    19457     6385806     82   Linux swap / Solaris
```

for the hdparm -I, what do you mean by my hard disk? Like, how should I refer to it?

---

### Post by ajmorris on 2008-07-22
> **Nybb said:**
> 
for the hdparm -I, what do you mean by my hard disk? Like, how should I refer to it?

hdparm -I /dev/sda (needs root permission)

AJ

---

### Post by Nybb on 2008-07-23
Here goes:
```
ubuntu@ubuntu:~$ sudo hdparm -I /dev/sda

/dev/sda:

ARA device, with non-removable media
    Model Number:          FUJITSU MHW2160BJ G1
    Serial Number:         K314T8525FJ0
    Firmware Revision:     0084001D
    Transport:             Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5; Revision: ATA8-AST T13 Project D1697 Revision 0b
Standards:
    Used: ATA-8-ACS revision 3f
    Supported: 8 7 6 5
Configuration:
    Logical        max      current
    cylinders      16383    16383
    heads          16       16
    sectors/track  63       63
    --
    CHS current addressable sectors:    16514064
    LBA    user addressable sectors:   268435455
    LBA48  user addressable sectors:   312581808
    device size with M = 1024*1024:       152527 MBytes
    device size with M = 1000*1000:       160041 MBytes (160 GB)
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16  Current = 16
    Advanced power management level: 128
    Recommended acoustic management value: 254, current value: 254
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    DOWNLOAD_MICROCODE
       *    Advanced Power Management feature set
            SET_MAX security extension
       *    Automatic Acoustic Management feature set
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_TEXT
       *    64-bit World wide name
       *    IDLE_IMMEDIATE with UNLOAD
            Disable Data Transfer After Error Detection
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    SATA-I signaling speed (1.5Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
            DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT LBA Segment Access (AC2)
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
Security:
    Master password revision code = 65534
            supported
    not     enabled
    not     locked
            frozen
    not     expired: security count
    not     supported: enhanced erase
    160min for SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000e042056f72
    NAA                 : 5
    IEEE OUI            : e
    Unique ID           : 042056f82
Checksum: correct
```

What exactly are we looking for in all that data?

---

### Post by ajmorris on 2008-07-23
That was checking for inconsitencies in your hard disk as windows had errors with it...
That option was a no go, so can you please post the errors you are getting from trying to boot your ubuntu partition?

AJ

---

### Post by Nybb on 2008-07-23
So I turn the computer on, and it makes it to the regular Ubuntu loading bar. It doesn't finish the bar, but instead starts flashing a whole bunch of things like:
```

[   23.6352833]  ata1.00: status:  { DRDY ERR }
[   24.5440982]  ata1.00: error:   { UNC }
[   24.8203295]  ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   25.3543625]  ata1.00: irq_stat 0x40000001
[   25.4650809]  ata1.00  cmd c8/00:08:ef:49:0n/00:00:00:00/e0 tag 0 dma 20480 in

```

Basically, it keeps printing those five lines over and over, with the numbers on the left steadily increasing (the number after 'tag 0 dma' changes as well). The leftmost numbers usually start at around 23.something and slowly go up; in the time it took me to type this it's gone up to about 40.something.

There are also a few lines about input/output errors, but they come up rarely and get pushed off the screen by the other messages too fast for me to copy them.

---

### Post by Nybb on 2008-07-26
Bump?

---

### Post by clark3rd on 2008-07-26
> **Nybb said:**
> Bump?

I had this problem as well on my laptop (inspiron 1100 ha!) with Hardy. It kept popping up and fdsk found some problems, but things degenerated and the file system went to crap. I then installed opensuse and things were okay, if you like opensuse (I don't). I then installed Linux Mint XFCE CE and thought my problems were solved. Two weeks and things were great. Now the DRDY problems are back. Seems to be Ubuntu related, though it doesn't happen on my desktop computer. any help would be appreciated.

---

### Post by Nybb on 2008-07-27
A friend of mine who knows at least a little bit more than me about this stuff says that I should just reinstall Ubuntu, and that that would fix it. While I haven't had the computer long, and therefore I don't have *too* much stuff to lose on the drive, it would be awesome if there was some other way.

Although, in light of what you, clark3rd, said about your experience, reinstalling the OS might not even help, in which case we're still as stuck as before.

---

### Post by Nybb on 2008-08-01
So I went ahead and reinstalled Ubuntu. I can now run it, but it pauses during the boot up with an error.

The error is with the Avahi mDNS/DNS-SD Daemon (I think?). It says "Timeout reached while waiting for return value. Could not receive return value form daemon process. [fail]" or something pretty close to that. 

After that, it makes it to the login screen, but after I login there are sometimes errors loading some of the GNOME stuff (I say sometimes because oddly enough GNOME has only complained once or twice out of a few bootups, the other sessions going completely normally).

After a fair bit of searching, I found that many people had a very similar problem caused by incompatible wireless cards, but this can't be the case as prior to my original attempt to create a Windows partition (described in the first post), this avahi-daemon never complained and I never had any problems with my wireless.

I found several other solutions that worked for other people on the net. They included playing with the apparmor and capability modules, and changing some wifi stuff, but nothing has helped so far.

---

