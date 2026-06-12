---
title: "Install on Vaio tz series"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by errix on 2007-07-25
Hi all,

Is someone already install feisty on a Vaio tz series?
If yes, what are the difficulties you met?
Which stuff doesn't work natively?

Thank you for your attention, :)

---

### Post by misuto27 on 2007-07-27
I have just received Vaio TZ (VGN-TZ90HS, Sony Style Model) and installed Ubuntu 7.04.

Vaio's 1366x768 monitor is recognized without any trouble at all.
However, I have Intel's 4965 ab or agn wifi chip and it was not recognized by Ubuntu 7.04
I will get it working later today since there's a post in forum about getting 4965 working.

Some Japanese bloggers already posts information and here are some information I&#12288;pulled out from it.
- SSD is recognized as /dev/sda/
- models with Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02) does not have any problem at all.
- To show its bloggers respect, here are links.  (Japanese Only)
  [http://ult.riise.hiroshima-u.ac.jp/~nagato/?VAIO+TZ90](http://ult.riise.hiroshima-u.ac.jp/~nagato/?VAIO+TZ90)
  [http://www.asial.co.jp/blog/238](http://www.asial.co.jp/blog/238)

here's the output of lspci.  Hope it helps...

~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fc200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fc300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, fast devsel, latency 0
        Memory at fc280000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fc540000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f6000000-f7ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: fc000000-fc0fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=07, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: fa000000-fbffffff
        Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, medium devsel, latency 0, IRQ 22
        Memory at fc544000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=09, subordinate=0d, sec-latency=32
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: fc100000-fc1fffff
        Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Sony Corporation Unknown device 900e
        Flags: medium devsel
        I/O ports at 18a0 [size=32]

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 2000 [size=256]
        [virtual] Expansion ROM at f0000000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1103
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fc000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

09:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, medium devsel, latency 168, IRQ 20
        Memory at fc101000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=09, secondary=0a, subordinate=0d, sec-latency=176
        Memory window 0: 88000000-8bfff000 (prefetchable)
        Memory window 1: 8c000000-8ffff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

09:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04) (prog-if 10 [OHCI])
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at fc100000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

09:04.3 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 11)
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at fc100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

09:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
        Subsystem: Sony Corporation Unknown device 900e
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at fc100c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by errix on 2007-07-28
Hi Misuto,

Thank you very much for your reply.
Where did you order your tz?
I will receive my own one in 3 or 4 days now. I am very impatient.
I ordered it with Mandriva, but I don't like Mandriva so much (But better than Win..s). I think I will ghost the disk before installing Feisty in case of.
One of my friend lend me his Vaio SZ series this week. I have installed Feisty on it and made everything working. 
Fingerprint, eye motion, card reader, etc.... I hope I will success also with my tz.
Thank you for the japanese link, but I just can read the Kanji Characters not the rest. 
There are lot of japanese people in New Caledonia, I think I will ask someone translate the rest for me.
Keep me inform if you improve or discover something new with your tz.

I hope you enjoy it.

Cheers,:)

---

### Post by misuto27 on 2007-08-02
I have ordered my VGN-TZ90HS at Sony Style in Japan.

The only problem I have faced so far is the WiFi card.  I had to upgrade from Faisty to Gutsy to get it working.

Slowly, but I am making my way through the TZ to work well.  I&#12288;have replaced Beryl-Compiz to Compiz Fusion.  It works quite smoothly with the TZ.

As usual, function keys are not working.  Only volume control function keys worked which amazed me. :)

Oh, one more thing.  The Ricoh OEM webcam "MOTIONEYE" seems to be a new model and there was no driver available yet...

I will report more as I explore the TZ.

---

### Post by errix on 2007-08-03
Hi Misuto,

I received my TZ 3 days ago from Geekstuff4You.
I also noticed about the light fn key button, it's a pity.
What do you mean by updated to Gusty? You mean a kernel update?
Otherwise I am very happy with my new laptop.
Very light, very good looking almost perfect.
I was surprised that the multimedia buttons work with Rythm box out of the box.
About the wifi I read and test several posts but still doesn't work. I am happy to hear that yours is working with your upgrade.

See ya....:)

---

