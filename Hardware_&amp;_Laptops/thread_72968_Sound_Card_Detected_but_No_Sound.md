---
title: "Sound Card Detected but No Sound"
date: 2005-10-07
forum: Hardware &amp; Laptops
---

### Post by new_to_unix on 2005-10-07
Hi,

I just installed Ubuntu- breezy Badger [5.10] on my system and I see that my sound card has been detected but I am unable to hear any sound on my system, including the Ubuntu login sound. I have been looking at a number of forums, & i ve tried various possibe solutions like the "alsamixer" command..... , but none of them have worked so far. Wud be really glad if some one could solve this issue. 

lspci command yielded the following:

vignesh@umavigram:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
        Subsystem: Rioworks: Unknown device 203a
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <available only to root>

0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
        Subsystem: Rioworks: Unknown device 203a
        Flags: bus master, fast devsel, latency 0

0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
        Subsystem: Rioworks: Unknown device 203a
        Flags: bus master, fast devsel, latency 0

0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Rioworks: Unknown device 203a
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Capabilities: <available only to root>

0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Rioworks: Unknown device 203a
        Flags: fast devsel
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Rioworks: Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1820 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Rioworks: Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Rioworks: Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1860 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Rioworks: Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 3
        Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e0200000-e02fffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Rioworks: Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]
        Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Rioworks: Unknown device 203a
        Flags: medium devsel, IRQ 10
        I/O ports at 1880 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Rioworks: Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Rioworks: Unknown device 2030
        Flags: medium devsel, IRQ 10
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <available only to root>

0000:02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
        Subsystem: Rioworks: Unknown device 203a
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 20001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 20400000-207ff000 (prefetchable)
        Memory window 1: 20800000-20bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
        Subsystem: Rioworks: Unknown device 203a
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at 20002000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 20c00000-20fff000 (prefetchable)
        Memory window 1: 21000000-213ff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

0000:02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01) (prog-if 10 [OHCI])
        Subsystem: Rioworks: Unknown device 203a
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at e0201000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <available only to root>

0000:02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Rioworks: Unknown device 202d
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at 3000 [size=256]
        Memory at e0201800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:02:09.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
        Subsystem: Intel Corp.: Unknown device 2701
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at e0200000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>


Thanks

---

### Post by mlomker on 2005-10-07
It can be caused by a lot of things, including permissions.  Have you seen [this one?]("http://linux.iuplog.com/default.asp?item=94639")

Does sound work when you boot a Knoppix disc or the liveCD?

---

### Post by new_to_unix on 2005-10-09
Hi 

Thanks for your reply. I have already tried all the possible solutions mentioned in the link you had mentioned and it didnt seem to work. Also could you tell me why I need to install Knoppix? 

If there is another way to solve this problem, pls let me know .

---

### Post by David Marrs on 2005-10-09
Due to a bug, I have to manually adjust the volume via the panel applet before I will hear any sound. Have you tried doing that?

---

### Post by mlomker on 2005-10-09
> Also could you tell me why I need to install Knoppix? 


You don't install it--it's a bootable version of linux.  It would allow you to test if your sound would work in another version of linux.  It looks like [this post]("http://www.ubuntuforums.org/showthread.php?p=268838#post268838") discusses the same card.  The poster mentions that the volume levels are lower than Windows and that he had to turn up 'headphones'.  You might want to read through that thread.

---

### Post by kehan on 2006-06-22
I had the same problem:

lspci gave me:

```
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Rioworks: Unknown device 202d
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at d0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at d0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
```
I then switched my volume control to the Intel ICH82801DB-ICH4 and in the properties enabled all of the interfaces.

I got this working by going to the switches panel and got sound working by turning off headphone jack sense and line jack sense and the external amplifier.

Thanks for your help.

---

