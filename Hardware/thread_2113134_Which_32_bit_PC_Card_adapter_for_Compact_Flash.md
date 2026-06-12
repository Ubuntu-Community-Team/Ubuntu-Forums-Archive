---
title: "Which 32 bit PC Card adapter for Compact Flash?"
date: 2013-02-06
forum: Hardware
---

### Post by Kixtosh on 2013-02-06
I'm trying to add a Compact Flash memory card to a PC Card adapter to add extra memory to one of my laptops. This has the potential to be:

[LIST]
[*]Fast ... hopefully faster that Class 10 SD cards, so almost as fast as some Solid State Drives from just a few years ago. I think 60 MB/s or 90 MB/s might be possible.
[*]Hidden, because once in the PC Card slot, it won't stick out or ever need to be removed. Unlike a USB drive, for example.
[*]Permanent. Since it's hidden, I might be able to stick my /home partition on there, or I could even put my whole O.S. on there potentially, if the speeds achieved are decent enough and if the drive is available to boot from.
[/LIST]
Unfortunately, it seems like most of these adapters, if not all of them, are Type I PCMCIA, which is 16 bit only. Apparently, that limits the speed to about 1 MB/s, so not much use, really.

If there is a Type II PCMCIA adapter out there, it could be 16 bit or 32 bit. In the case of the latter, I think that would allow the higher speeds that might make it suitable for installing. All I've been able to find out is that:

[LIST]
[*] Type I cards should be about 3.3 mm think, and are always 16 bit.
[*]Type II cards should be about 5 mm thick, and can be either 16 bit or 32 bit. They usually have a gold strip on one side of the connector.
[/LIST]
This may be a long shot, I know, but any ideas out there about this?!

---

### Post by Kixtosh on 2013-02-06
So, I've done some more research. It seems that 32 bit PC Cards (or CardBus, I think, is an alternative name) have vanished off the face of the earth, and can be hard to find anywhere in the known universe!

This is the most detailed description I have found:

> **Data Transfer Rates**

 The maximum throughput rates for PC Cards are as follows: 
 [B] 
16-bit Memory Transfers[/B]
[LIST]
[*]Byte mode: 10 Mbytes/sec 
[*]Word mode: 20 Mbytes/sec 
[/LIST]
 ** 16-bit I/O Transfers**
[LIST]
[*]Byte mode: 3.92 Mbytes/sec
[*] Word mode: 7.84 Mbytes/sec 
[/LIST]
 ** CardBus**

[LIST]
[*]Byte mode: 33 Mbytes/sec 
[*]Word mode: 66 Mbytes/sec 
[*] DWord mode: 132 Mbytes/sec 
[/LIST]
 ** Bootup support**

 It you can boot from a PCMCIA drive depends on the BIOS  implementation of the host system as well as the implementation of the  drives controller, aka the PC Card. They both have to support it. 
Source: [http://www.thinkwiki.org/wiki/PCMCIA#Data_Transfer_Rates](http://www.thinkwiki.org/wiki/PCMCIA#Data_Transfer_Rates)

So it would seem that if I can find the right adapter, speeds up to, and beyond 100 MB/s should be attainable. There seems to have been much discussion of this in photography websites, and two brands seem to have offered 32 bit CardBus adpaters:

[LIST]
[*]Lexar Media 
[*]Delkin Devices 
[/LIST]
Only the Delkin seems to be available new, and both are very hard to find used. In the case of Delkin, they sell these direct in two versions from their "bargain basement" selection:

[LIST]
[*]PC/ATA 
[*]UDMA 
[/LIST]
The theoretical speeds announced for both are 132 MB/s, but they claim that this is "4-6 Times Faster Than Standard 16-Bit Adapters", whereas I was under the impression that 16 bit adapters could only manage much lower speeds than that (see also the quoted reference above)!

Link to their search results: [http://delkinbargains.com/?s=CardBus](http://delkinbargains.com/?s=CardBus)
 
I don't mind being a test dummy for this, if it helps other users (and if it doesn't cost too much), so I've ordered both options to see how I get along.

*P.S. ... I'm not sure this belongs in the "installation" section of the forum, but I thought it belonged rightly in the "upgrades" section, so I'm hope I'm posting in the right section!*

---

### Post by Kixtosh on 2013-02-08
Well, I received the Delkin PC/ATA card today, and I have some good news as well as some bad news!

**1. Lucid Lynx 10.04 LTS**

[LIST]
[*]The card is recognized immediately by Lucid Lynx 10.04 LTS.
[*]A 16GB 500x Compact Flash card inserted in the CardBus slot is recognized and can be used.
[*]Speeds are much slower than the internal SD Card slot with Class 10 SD Cards.
[*]The Disk Utility refuses to benchmark the drive with an error message that it is "too slow".
[/LIST]

**2. Microsoft Windows (Vista Business)**

[LIST]
[*]The card is recognized but requests drivers, which it cannot locate automatically, either locally or on the Internet.
[*]Once the drivers are downloaded manually from Delkin and the Device Manager is used to manually identify the location of the drivers, the device installs correctly.
[*]A Compact Flash card inserted in the CardBus slot is recognized and can be used.
[*]Speeds are much faster than the SD Card slot with Class 10 SD Cards. I do not have a benchmark I can use with the Windows O.S., but speeds seem to be more than twice as fast for copying a large test file than a Class 10 SD Card.
[*]Using this laptop, equipped with a slowish PATA Solid State Drive, speeds are almost as fast as the main SDD (to within less than 10 seconds!). I would estimate the speeds to be close to claimed capability of the card, which is 75MB read and 40MB/s write.
[/LIST]
So, this is a superb addition if I were using the Windows O.S., but I'm not! For Ubuntu, there is no point in using this CardBus and card right now instead of other options. 

I seem to have encountered some sort of driver problem here, maybe? The drivers installed by Windows identify themselves in the Device Manager as follows:

[LIST]
[*]Under the heading of IDE ATA/ATAPI Controllers
[*]Delkin CardBus Adapter
[*]IDE Channel
[*]Intel (R) 82801G (ICH7 Family) Ultra ATA Storage Controllers - 27DF
[/LIST]
I've attached an image below if the output, as well as an image from the Disk Utility for the same drive.

---

### Post by lisati on 2013-02-09
*Thread moved to **Hardware**.*

---

### Post by Kixtosh on 2013-02-09
Conclusions so far:

[LIST]
[*]Delkin CardBus 32 Compact Flash adapter works.
[*]Delkin CardBus 32 Compact Flash adapter is a FANTASTIC addition to any Windows laptop with a Type II PC Card slot available.
[*]Windows laptops will get super fast storage, much faster than even Class 10 SD cards or USB 2.0 flash storage according to my benchmarks.
[/LIST]
Unfortunately for Linux users, so far, I don't have a satisfactory solution since, although the card is recognized immediately and works out of the box, the fast speeds available with Windows are not available with Ubuntu.

Maybe I'll try a LIVE CD of Mint, in case their policy of including more stuff that is not Open Source than Ubuntu might allow the device to work differently.

---

### Post by spynoodle on 2013-02-24
I'm a Linux Mint user, and I registered for this forum just to express my interest in your endeavors with this project. I have a Dell Latitude D410, which also has a PC Card slot that I have hoped to possibly take on this same type of expansion with. If you find success with Mint, I would definitely like to try this out. :)

---

### Post by Kixtosh on 2013-02-24
Thanks, spynoodle! Signing up just to reply to one thread is a noble effort indeed.

I tried Mint (the current release, 14 MATE, I think), but no dice. The performance was the same dull result. 

I also wanted to try PCLinuxOS, but I couldn't even get it to load up completely, so there was nothing to try.

Puppy works great on this laptop, but since boot times are so fast with Ubuntu, as well as shut down, there's no real reason to use it. Firefox takes two seconds or less to load from a cold boot (less than one second if already used during the same session), so there again, Puppy can offer no compelling speed advantage over a complete Ubuntu system. The speed tests on the CF card and CardBus adapter were the same with Puppy, unfortunately: slow and boring.

I think I may update to 12.04 on this laptop  (I prefer LTS releases on slightly older hardware) and then open a bug report, under the assumption that a bug report for a current LTS release might be worthy of more attention than an LTS release that is within weeks of end of life.

For your Latitude D410, this would be of huge benefit, if it would just work! In Windows, the speeds on my 500x CF card are comparable to an external hard drive connected using IEEE 1394 on the same laptop   (firewire 400 to Apple, or i.Link to others), with what seems to be similar reliability and stability in speed, unlike USB 2.0. It's noticeably faster than my USB driven 3.5" storage drives, in fact (which are fine and dandy, but not very portable, right?). Damn, it would be so  useful for my Ubuntu, or your Mint!

I'm ready to invest time and energy to investigate any avenues of discovery, but it doesn't seem to be a hot topic. In comparison USB 2.0 just seems too slow, fiddly and inconvenient for something this lightweight and portable.

---

### Post by Kixtosh on 2013-02-24
Did a little bit more research, and I'm wondering if there may be something wrong with the settings for this device.

I tried the following terminal command:
```
~$ sudo hdparm -I /dev/sdb
```Results:
```
/dev/sdb:

CompactFlash ATA device
    Model Number:       SanDisk SDCFH-004G                      
    Serial Number:      APZ101010200032
    Firmware Revision:  HDX 6.02
Standards:
    Likely used: 6
Configuration:
    Logical        max    current
    cylinders    7751    7751
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:    7813008
    LBA    user addressable sectors:    7813120
    LBA48  user addressable sectors:    7813120
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:        3815 MBytes
    device size with M = 1000*1000:        4000 MBytes (4 GB)
    cache/buffer size  = 1 KBytes (type=DualPort)
Capabilities:
    LBA, IORDY(may be)(cannot be disabled)
    bytes avail on r/w long: 4
    Standby timer values: spec'd by Standard
    R/W multiple sector transfer: Max = 1    Current = 0
    Advanced power management level: disabled
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 (?)
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    Write cache
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    CFA feature set
            Advanced Power Management feature set
       *    48-bit Address feature set
            Mandatory FLUSH_CACHE
            FLUSH_CACHE_EXT
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    Data Set Management determinate TRIM supported
       *    CFA advanced modes: pio5 *pio6 
       *    CFA Power Level 1  (max 500mA)
Integrity word not set (found 0x0000, expected 0x54a5)

```So then I tried:
```
~$ sudo hdparm -d1 /dev/sdb
```Results:
```
/dev/sdb:
 setting using_dma to 1 (on)
[B] HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device[/B]
```Those last two lines don't look good. Something must not be working correctly, and I'm wondering if this would have an effect on transfer speeds. If anyone has any ideas about turning UDMA on or off for this device, I'd love to see if it makes any difference.

Remember that **I was only able to purchase the PC/ATA CardBus** adapter from Delkin Devices, **not the UDMA CardBus adapter**, even if the CF card itself may be UDMA capable.

---

### Post by spynoodle on 2013-02-24
Hmm, that error does seem like it might be the source of your problem. Perhaps Linux is assigning a 16-bit kernel driver to your cardbus adapter, thus making it unable to support the full speed of the CF card's ATA interface? I'm a little bit of a Linux noob, but maybe an "lspci -v" command would display the driver that's being assigned to the adapter?

---

### Post by Kixtosh on 2013-02-24
Great idea, and good for you! I'm not great with terminal commands, I just use this O.S. blindly! Most of them make little or no sense to me, so I don't feel like I know what they're doing. This one should have been obvious, though, even for me, as *ls=list* and *PCI=**Peripheral Component Interconnect.* I must need to make more effort or something since the terminal seems to be frequently needed to troubleshoot anything even the slightest bit obscure or vaguely old technology.

I highlighted some of the output below, including references to PC Express, since this laptop only has a PCMCIA CardBus slot, not the newer PC Express (so maybe it's relevant). There's also a reference to IDE, which would include the rather unusual PATA Solid State Drive (there weren't ever very many of those, to my knowledge).

```
~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device 0022
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ffc80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at cff8 [size=8]
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Memory at ffc40000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device 0022
    Flags: fast devsel
    Memory at 8a000000 (32-bit, non-prefetchable) [disabled] [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 8a080000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

[B]00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: ff900000-ff9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: ff800000-ff8fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp
[/B]
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at afe0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at af80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at af60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at af40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ffc3fc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 84000000-89ffffff
    Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

[B]00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at af10 [size=16]
    Kernel driver in use: ata_piix
[/B]
01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Memory at ff9e0000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at bfe0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
    Subsystem: Intel Corporation Device 1100
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at ff8fe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

[B]03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 168, IRQ 21
    Memory at 88004000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
    Memory window 0: 80000000-83fff000 (prefetchable)
    Memory window 1: 84000000-87fff000
    I/O window 0: 00001000-000010ff
    I/O window 1: 00001400-000014ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
[/B]
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at 88005000 (32-bit, non-prefetchable) [size=2K]
    Memory at 88000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

03:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 64, IRQ 23
    Memory at 88005800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
[B]
04:00.0 Mass storage controller: Workbit Corporation NinjaPATA-32 Delkin Cardbus UDMA (rev 01)
    Subsystem: Workbit Corporation NinjaPATA-32 Delkin Cardbus UDMA
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at 1000 [size=32]
    Memory at 84000000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: pata_ninja32
    Kernel modules: pata_ninja32[/B]
```

---

### Post by Kixtosh on 2013-02-26
I've got a little further with this, but I'm not sure if the result will help, using this command on an inserted CF card (this is not the larger card I want to use eventually for data, but it is capable of 30MB/s write speed with Windows Vista).

The CF card in the CardBus adapter is identified as sdb1. Note the final footnote (which I did NOT add myself) and how there are no "*" next to any of the parameters.

```
~$ sudo hdparm -i /dev/sdb1

/dev/sdb1:

 Model=SanDisk, FwRev=HDX, SerialNo=APZ101010200032
 Config={ HardSect NotMFM Removeable DTR>10Mbs nonMagnetic }
 RawCHS=7751/16/63, TrkSize=0, SectSize=576, ECCbytes=4
 BuffType=DualPort, BuffSize=1kB, MaxMultSect=1, MultSect=off
 CurCHS=7751/16/63, CurSects=7813008, LBA=yes, LBAsects=7813120
 IORDY=no, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 
 AdvancedPM=yes: disabled (255) WriteCache=enabled

  * signifies the current active mode
```P.S. according to wikipedia:

[LIST]
[*]  Mode pio4 should be capable of 16.7 MB/s.
[*]Ultra dma4 should be capable of 66.7 MB/s.
[/LIST]
Both seem to be "supported", so why am I not getting either?

---

### Post by spynoodle on 2013-02-27
Hmm, it would look like all the drivers are configured correctly. This page looks a bit old, but maybe it would help: [http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-3.html](http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-3.html)

EDIT: Haha, I didn't see your other post there. Here's my desktop's output for that same command:
```
/dev/sda1:

 Model=WDC WD1200BB-00GUA0, FwRev=08.02D08, SerialNo=WD-WMALA1120430
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=234441648
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode


```
I have an asterisk on udma5, so I would assume that your card somehow has no ATA mode enabled. :confused: I was wondering, though: are you using the 5-in-1 card, or the CF-only card?

---

### Post by Kixtosh on 2013-03-01
Sorry, it took me a while to respond, but I had one of those emergency situations ...

Anyway, to answer your question, I'm using a CardBus 32 bit CF adapter only.

Here's an interesting thing, and maybe it explains a lot. This is with the card I originally wanted to use, not the one that gave the result posted above. I've just done a low level format on this card to get it working again (the partition table and MBR were broken, it's a long story ...) It is only a week or two old, but it's been through the mill a few times with my various experiments. Notice the asterisk is finally there, but not where I'd want it!

```
/dev/sdb:

 Model=CF, FwRev=Ver6.09A, SerialNo=14EF072C050800456330
 Config={ HardSect NotMFM Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=32256, SectSize=512, ECCbytes=4
 BuffType=DualPort, BuffSize=1kB, MaxMultSect=1, MultSect=1
 CurCHS=16383/16/63, CurSects=28278432, LBA=yes, LBAsects=28278432
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 *mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-4,5

 * signifies the current active mode


```You can see that it is using mdma2 mode. Probably not a very good thing! I'm guessing that the device is currently stuck in 16 bit mode, and 2.5 MB/s.

I don't know if the problem is the adapter (would a different adapter work differently?) or the CF card settings, which could be managed by hdparm maybe.

---

### Post by Kixtosh on 2013-03-01
Well, I don't know if I'm actually getting anywhere, but I came across this guide for PCMCIA cards, including the second link, which is specifically for memory cards (sections 4.7 and 4.8):

[http://www.tldp.org/HOWTO/PCMCIA-HOWTO.html](http://www.tldp.org/HOWTO/PCMCIA-HOWTO.html)
[http://www.tldp.org/HOWTO/PCMCIA-HOWTO-4.html#ss4.7](http://www.tldp.org/HOWTO/PCMCIA-HOWTO-4.html#ss4.7)

I don't know how old this guide is, and how relevant it is today, but there are some interesting comments:

> The following information applies only to so-called ``linear flash'' memory cards.  Many flash cards, including all SmartMedia and CompactFlash cards, actually include circuitry to emulate an IDE disk device.  Those cards are thus handled as IDE devices, not memory cards. 
There are two major formats for flash memory cards: the FTL or ``flash translation layer'' style, and the Microsoft Flash File System.  The FTL format is generally more flexible because it allows any ordinary high-level filesystem (ext2, ms-dos, etc) to be used on a flash card as if it were an ordinary disk device.  The FFS is a completely different filesystem type.  Linux cannot currently handle cards formated with FFS. 
To use a flash memory card as an ordinary disk-like block device, first create an FTL partition on the device with the ftl_format command.  This layer hides the device-specific details of flash memory programming and make the card look like a simple block device.  For example:[INDENT] 
** [FONT=arial] ftl_format -i /dev/mem0c0c  [/FONT]**
[/INDENT]

Note that this command accesses the card through the ``raw'' memory card interface.  Once formatted, the card can be accessed as an ordinary block device via the ftl_cs driver.  For example:[INDENT] 
[B][FONT=arial] mke2fs /dev/ftl0c0 
mount -t ext2 /dev/ftl0c0 /mnt[/FONT][/B]
[/INDENT]
I wouldn't advise anyone to try those commands unless somebody more knowledgeable is able to clarify what we're doing ... unless they're willing to sacrifice a working card in the process.

* Edit: looks like it's from December of 2003. That's a long time ago, and the fast cards we can buy today weren't available then, nor did they have such relatively large capacity.*

---

### Post by spynoodle on 2013-03-02
Interesting stuff. I think that I might go ahead and buy the adapter and a 600x 16GB Kingston CF card, just to see how it goes. Maybe I'll get lucky, and be able to make it work. The good thing is that we know that it *can* work with this adapter, since you achieved the speeds you wanted on Windows.

---

### Post by spynoodle on 2013-03-14
Any news? I haven't bought one yet, mainly because I had my laptop's main HDD returned to Samsung/Seagate for a replacement, and I think I may just stick with one drive if it seems fast enough. If you succeed in your endeavor, though, keep me posted; I'm still considering going through with this. :)

---

### Post by Kixtosh on 2013-03-14
No news, unfortunately.

I'm delayed in my efforts since I seem to have wrecked my best Compact Flash card. I was using it in an attempt to boot from an IDE to CF adapter in another laptop, and now I'm getting all sorts of errors from it. I'm going to have to order another, or wait to see what the manufacturer says about the "damage", and whether or not I caused it.

I'm also investigating using a CardBus adapter for an SD card instead, since those are now available in larger capacities with higher read and write speeds. The built-in SD card reader on my laptop doesn't seem to take advantage of those speeds beyond 20MB/s. The distributor of this adapter on amazon.com sent a one line reply to my request for information that the card would not work with Linux. No extra details were provided.

[http://www.amazon.com/SDHC-to-CardBus-PC-Card/dp/B0027VL2F2](http://www.amazon.com/SDHC-to-CardBus-PC-Card/dp/B0027VL2F2)

I'm not sure what differences between SD cards and CF cards might influence the result in any way, but this CardBus adapter solution seems ideal for me, especially with the speeds observed in Windows already. My SSD drive has some sort of proprietary ZIF connector and I don't think it can be upgraded. It seems that there could be a solution to get the CardBus adapter working somewhere, but I still don't know what it is.

---

### Post by spynoodle on 2013-03-23
Well, if that adapter supports UHS SD cards, then you may be able to achieve some pretty high speeds. What class card are you going to try to use?

---

### Post by Kixtosh on 2013-03-23
So far, I've got a SanDisk Extreme 16GB card to experiment with. 


[LIST]
[*]Claimed read and write speeds of up to 45MB/sec.
[*]SDHC
[*]Class 10
[*]UHS-1
[/LIST]
 
The bigger cards (32GB and up) were too expensive; the faster cards (such as SanDisk Extreme Pro, 95MB/sec.) were also too expensive for an experiment that might not work. I don't want to pay the premium for these faster cards unless I'm going to get faster speeds than USB 2.0, and so far on my equipment, that has not been the case. All the SD Cards and USB sticks I've measured seem to have _average_ read or write speeds around 20MB/sec. This is actually better than Class 10, as I understand that to mean the card will have a minimum of 10MB/sec. sustained speed. Access times are between 0.8ms and 1.2ms. SD Cards do seem to have more consistent results than USB sticks: there's much less of a spread between the highest and lowest speeds measured. 

If I got any of these adapters to work, though, then I wouldn't hesitate to get one of the faster cards.

---

### Post by spynoodle on 2013-03-24
If you end up finding success with a UHS SD cardbus adapter, than make sure to post how it goes. ;) Those seem like some pretty good speeds to start with, and I guess it can only get better.

EDIT: I also want to add: I'm currently using a Samsung HM160HC IDE hard drive, and it's giving me pretty good read speeds of somewhere around 70+ MB/s IIRC.

---

