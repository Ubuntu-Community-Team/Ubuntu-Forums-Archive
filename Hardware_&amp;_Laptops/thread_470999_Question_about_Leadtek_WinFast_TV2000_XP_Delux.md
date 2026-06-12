---
title: "Question about Leadtek WinFast TV2000 XP Delux"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by MentholLite on 2007-06-11
Hi guys,

I am trying to setup my tv tuner card on ubuntu.

I search the forums and google, and find it confusing.
Some sites or tutorials are suggesting to enable bttv modules.

While when I look at the Hardware Information, it shows that the driver used is cx8800.
Can anyone tell me which modules to used for installing this piece of hardware? :(

```

menthollite@ubuntu7:~$ sudo lspci -vn
Password:
00:00.0 0600: 10de:01e0 (rev c1)
        Subsystem: 147b:1c00
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [40] AGP version 3.0
        Capabilities: [60] HyperTransport: Host or Secondary Interface

00:00.1 0500: 10de:01eb (rev c1)
        Subsystem: 10de:0c17
        Flags: 66MHz, fast devsel

00:00.2 0500: 10de:01ee (rev c1)
        Subsystem: 10de:0c17
        Flags: 66MHz, fast devsel

00:00.3 0500: 10de:01ed (rev c1)
        Subsystem: 10de:0c17
        Flags: 66MHz, fast devsel

00:00.4 0500: 10de:01ec (rev c1)
        Subsystem: 10de:0c17
        Flags: 66MHz, fast devsel

00:00.5 0500: 10de:01ef (rev c1)
        Subsystem: 10de:0c17
        Flags: 66MHz, fast devsel

00:01.0 0601: 10de:0060 (rev a4)
        Subsystem: 147b:1c00
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [48] HyperTransport: Slave or Primary Interface

00:01.1 0c05: 10de:0064 (rev a2)
        Subsystem: 147b:1c00
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at e000 [size=32]
        Capabilities: [44] Power Management version 2

00:02.0 0c03: 10de:0067 (rev a4) (prog-if 10 [OHCI])
        Subsystem: 147b:1c00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at ea080000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:02.1 0c03: 10de:0067 (rev a4) (prog-if 10 [OHCI])
        Subsystem: 147b:1c00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at ea083000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:02.2 0c03: 10de:0068 (rev a4) (prog-if 20 [EHCI])
        Subsystem: 147b:1c00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at ea086000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:04.0 0200: 10de:0066 (rev a1)
        Subsystem: 147b:1c00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at ea087000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e400 [size=8]
        Capabilities: [44] Power Management version 2

00:05.0 0401: 10de:006b (rev a2)
        Subsystem: 147b:1c00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at ea000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [44] Power Management version 2

00:06.0 0401: 10de:006a (rev a1)
        Subsystem: 147b:1c00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        I/O ports at d000 [size=256]
        I/O ports at d400 [size=128]
        Memory at ea081000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:08.0 0604: 10de:006c (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=02, sec-latency=32
        I/O behind bridge: 0000a000-0000bfff
        Memory behind bridge: e6000000-e9ffffff
        Prefetchable memory behind bridge: 50000000-500fffff

00:09.0 0101: 10de:0065 (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: 147b:1c00
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: [44] Power Management version 2

00:0d.0 0c00: 10de:006e (rev a3) (prog-if 10 [OHCI])
        Subsystem: 147b:1c00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at ea084000 (32-bit, non-prefetchable) [size=2K]
        Memory at ea085000 (32-bit, non-prefetchable) [size=64]
        Capabilities: [44] Power Management version 2

00:1e.0 0604: 10de:01e8 (rev c1) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: e4000000-e5ffffff
        Prefetchable memory behind bridge: c0000000-dfffffff

01:09.0 0604: 3388:0021 (rev 11) (prog-if 00 [Normal decode])
        Flags: bus master, medium devsel, latency 32
        Bus: primary=01, secondary=02, subordinate=02, sec-latency=32
        Memory behind bridge: e6000000-e7ffffff
        Capabilities: [80] Power Management version 2
        Capabilities: [90] #06 [0080]

01:0b.0 0104: 1095:3112 (rev 02)
        Subsystem: 1095:6112
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        I/O ports at a000 [size=8]
        I/O ports at a400 [size=4]
        I/O ports at a800 [size=8]
        I/O ports at ac00 [size=4]
        I/O ports at b000 [size=16]
        Memory at e9000000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 50000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 2

02:0c.0 0400: 14f1:8800 (rev 05)
        Subsystem: 107d:6620
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at e6000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

02:0d.0 0c00: 104c:8024 (prog-if 10 [OHCI])
        Subsystem: 107d:6620
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at e7004000 (32-bit, non-prefetchable) [size=2K]
        Memory at e7000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

03:00.0 0300: 1002:4152 (prog-if 00 [VGA])
        Subsystem: 18bc:0246
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 21
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at c000 [size=256]
        Memory at e5000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e4000000 [disabled] [size=128K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2

03:00.1 0380: 1002:4172
        Subsystem: 18bc:0247
        Flags: 66MHz, medium devsel
        Memory at d0000000 (32-bit, prefetchable) [disabled] [size=256M]
        Memory at e5010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [50] Power Management version 2

menthollite@ubuntu7:~$ 

```

Below are the "Hardware Information" screen cap:

---

### Post by MentholLite on 2007-06-11
Can anybody help or advise?! :confused:

---

### Post by DriftShin on 2007-06-12
```
driftshin@driftshin-desktop:~$ sudo rmmod bt878
Password:
ERROR: Module bt878 does not exist in /proc/modules
driftshin@driftshin-desktop:~$ sudo rmmod tuner
ERROR: Module tuner does not exist in /proc/modules
driftshin@driftshin-desktop:~$ sudo rmmod bttv
ERROR: Module bttv does not exist in /proc/modules

driftshin@driftshin-desktop:~$ sudo modprobe bttv card=34 tuner=37
FATAL: Error inserting bttv (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/bt8xx/bttv.ko): Invalid argument
```

```
01:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
Subsystem: LeadTek Research Inc. WinFast TV 2000
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 32 (4000ns min, 10000ns max)
Interrupt: pin A routed to IRQ 9
Region 0: Memory at d8100000 (32-bit, prefetchable) [size=4K]
Capabilities: <access denied>

01:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
Subsystem: LeadTek Research Inc. Unknown device 6606
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 32 (1000ns min, 63750ns max)
Interrupt: pin A routed to IRQ 18
Region 0: Memory at d8101000 (32-bit, prefetchable) [size=4K]
Capabilities: <access denied>
```

Bin hoping for some kind of help but alas the only help i can find is for the RM card and a bit for the Expert but none for the Deluxe. I too find the configurations confusing coz they seem to work for some people but not all. How can i be getting 'invalid argument' warnings when everyone else is not?? btw, i do have sudo access as can be seen from from the code.

---

### Post by MentholLite on 2007-06-12
Alright, I make a mistake about my card model.

Mine is actually [**Leadtek WinFast DV2000**]("http://www.leadtek.com/usa/tv_tuner/specification.asp?pronameid=92&lineid=6&act=2"); and its confirmed to be on the Conexant CX2388x chipset.
According to [**linuxtv.org**]("http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_%28cx2388x%29"), The cx2388x chip is the successor to the bt848/bt878 chips; cf. PCI interface chipsets used for v4l cards.

However, currently I am using bttv modules to load my tv tuner card to test out whether it works in Ubuntu.

```

menthollite@ubuntu7:~$ sudo modprobe bttv card=34 tuner=3
menthollite@ubuntu7:~$

```

I tried out the above settings with [**tvtime**]("http://sourceforge.net/projects/tvtime/") & [**aumix**]("http://sourceforge.net/projects/aumix/").
Initially, I am only able to watch TV programme and do channel scanning (though not very good, need to fine tune).
And I am unable to get any sound output.
After which I tried to use aumix and played around with the slider, and sure enough now I got the sound.
Have yet to test whether remote control works though.

I am now confused whether should I load the CX2388x modules, as it seems fine now.
Will be trying out on MythTV when I have sorted this out.

---

