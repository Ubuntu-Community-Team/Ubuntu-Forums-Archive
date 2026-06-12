---
title: "82801G (ICH7 Family) rev02 HDA no sound"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by chumbo on 2007-03-09
Toshiba Satellite M100 - card detected, yet there's no sound

I've installed alsa 1.0.12 manually, as 1.0.11 doesn't like HDA

any help is greatly appreciated

C.

lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7145
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:06.0 CardBus bridge: Texas Instruments Unknown device 8039
05:06.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
05:06.2 Mass storage controller: Texas Instruments Unknown device 803b
05:06.3 Class 0805: Texas Instruments Unknown device 803c

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

speaker-test 1.0.12

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 16384
Period size range from 1024 to 1024
Using max buffer size 16384
Periods = 4
was set period_size = 1024
was set buffer_size = 16384
 0 - Front Left
Time per period = 2.663904
 0 - Front Left
Time per period = 2.986481
 0 - Front Left
Time per period = 2.986509
 0 - Front Left
Time per period = 2.986510
 0 - Front Left
Time per period = 2.986521
 0 - Front Left

---

### Post by teaker1s on 2007-03-09
if alsaconfig sets it up and you still have no sound often the model has to be specified in config file.

I would post more but my laptop is away for repair and I have the config file location on a text file on it:(

---

### Post by vicky1984 on 2007-03-09
i had the same problem but i followed these instructions and it worked :)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by chumbo on 2007-03-10
Thanks for that Vicky, downloaded the latest dev build of Alsa (1.0.14rc4), installed it and tried under optons in /etc/modprobe.d/alsa-base to specify all these values for  snd-hda-intel:

laptop,
laptop-eapd,
3stack,
5stack,
6stack,
ref,

still no dice..

C.

---

### Post by chumbo on 2007-03-10
I managed to get better output from lspci:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems **Unknown device ff00**
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 50
        Region 0: Memory at d8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

the 'unknown device' part worries me - is there a place where I could specify it?

Thanks,

C.

---

