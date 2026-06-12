---
title: "Nightmare installing ATI drivers"
date: 2008-09-29
forum: General Help
---

### Post by Lysander666 on 2008-09-29
Hi everyone, 

I have been struggling for days to install ATI drivers on the latest version of Ubuntu.

I could easily use EnvyNG but it only seems to want to install the latest 8.6 drivers - I don't want to install these since they have a scaling problem with HDMI. I am therefore trying to install anything previous to 8.3 but I can't work out how to do it in the terminal, I don't really know where to start. Ive tried following the instructions on ATI's website but it just says 'command not found' after I've navigated to the folder and told it to install the drivers. 

I am totally new to the Linux phenomenon and trying to get a 1920x1200 resolution is becoming annoying! Any help would be appreciated.

---

### Post by Uchiha_madara on 2008-09-29
> **Lysander666 said:**
> 
I have been struggling for days to install ATI drivers on the latest version of Ubuntu.


Why all of this ????

I have ATI drivers ... it works Perfect on My Laptop....

Listen .... after you install Ubuntu 8.04 
1 - make the update
2 - after the update click on System >>Administration ...
3 - choose the restricted hardware
4 - check on the drivers you see ...
5 - and wait the Download and the installation...

6 - then reboot..
:D:D
if all the steps above don't work with you ..
open the terminal and type :
> lspci -v

paste the result as new reply to see it and determine how could we help you ???

---

### Post by Flynn555 on 2008-09-29
yes...i didnt have any trouble getting my ati card to work under hardy.  i just installed hardy and away i went.  but i remember in gusty, yes it was a nightmare. (wouldnt even let me install ubuntu without taking the card out)

---

### Post by binbash on 2008-09-29
I have same problems.I tried with different computers(5).Without envyng , I get blank white screen with official ati drivers.Is there a way to update 8.9 with envyng?

---

### Post by Lysander666 on 2008-09-29
> **Uchiha_madara said:**
> Why all of this ????


1 - make the update
2 - after the update click on System >>Administration ...
3 - choose the restricted hardware

Got this far, but what do you mean by 'choose the restricted hardware'? There's a section for Hardware drivers, and it just says 'no proprietary drivers are in use on this system'. 

> **Uchiha_madara said:**
> if all the steps above don't work with you ..
open the terminal and type :


paste the result as new reply to see it and determine how could we help you ???

OK, here we go:

> 

lysander@PSYCHOPIGEON-III:~$ lspci -v 
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
	Subsystem: Giga-byte Technology Unknown device 5000
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: ee000000-efffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at d000 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at c000 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology Unknown device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f0105000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Unknown device a002
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00008000-00009fff
	Memory behind bridge: f0000000-f00fffff
	Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: ec000000-edffffff
	Prefetchable memory behind bridge: 00000000f0200000-00000000f02fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at c400 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at c800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at cc00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology Unknown device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0104000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: e4000000-ebffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
	Subsystem: Giga-byte Technology Unknown device 5001
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Unknown device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Giga-byte Technology Unknown device 5001
	Flags: medium devsel, IRQ 11
	Memory at f0106000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 0500 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Unknown device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at d800 [size=8]
	I/O ports at dc00 [size=4]
	I/O ports at e000 [size=8]
	I/O ports at e400 [size=4]
	I/O ports at e800 [size=16]
	I/O ports at ec00 [size=16]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9440 (prog-if 00 [VGA controller])
	Subsystem: ATI Technologies Inc Unknown device 0502
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ef000000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 7000 [size=256]
	[virtual] Expansion ROM at ee000000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 Audio device: ATI Technologies Inc Unknown device aa30
	Subsystem: ATI Technologies Inc Unknown device aa30
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at ef010000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Giga-byte Technology Unknown device b000
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f0000000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Unknown device b000
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 8000 [size=8]
	I/O ports at 8400 [size=4]
	I/O ports at 8800 [size=8]
	I/O ports at 8c00 [size=4]
	I/O ports at 9000 [size=16]
	Capabilities: <access denied>

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
	Subsystem: Giga-byte Technology Marvell 88E8053 Gigabit Ethernet Controller (Gigabyte)
	Flags: bus master, fast devsel, latency 0, IRQ 507
	Memory at ed000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at a000 [size=256]
	[virtual] Expansion ROM at f0200000 [disabled] [size=128K]
	Capabilities: <access denied>

05:00.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs X-Fi Platinum
	Flags: bus master, medium devsel, latency 32, IRQ 12
	I/O ports at b000 [size=32]
	Memory at e8000000 (64-bit, non-prefetchable) [size=2M]
	Memory at e4000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

lysander@PSYCHOPIGEON-III:~$ 

---

### Post by Lysander666 on 2008-09-30
Can anyone help? :)

---

### Post by kewlpics on 2008-10-03
I have the same issue.  I get the white screen.  I have not been able to get it to work.  

I am running hardy x64.  Trying to get ATI Radeon HD 3200 - HDMI output work with my Sharp LCD TV.

No luck.

---

### Post by markbuntu on 2008-10-03
Use this guide, it is the only one I know that works properly, it also has special directions for 64 bit users:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The driver in the repos and from envy do not support many of the newer cards, like the 3200 and 48xx series. The guide above will get the 8.9 driver which supports all the newer cards except the 3800x2 cards.

Release notes for 8.9

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html)

Release notes for 8.8

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html)

---

