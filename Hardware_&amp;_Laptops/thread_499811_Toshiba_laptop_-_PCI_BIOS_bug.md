---
title: "Toshiba laptop - PCI BIOS bug?"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by detroit/zero on 2007-07-13
Hi,

I have a Toshiba Satellite A135 laptop. Every time I boot the system up, after I make my GRUB selection and Ubuntu begins to load, I get a quick message saying **PCI: BIOS BUG #81[49435000]**, but then the system loads fine and everything is OK.

I have the latest BIOS version from Toshiba. There don't seem to be any ill effects (that I've noticed..) from whatever this error is. A google search didn't turn up any real info about this specific bug. I didn't find anything in the forums, either.

Here's a quick outtake from */var/log/sys.log*:
```

Jul 12 03:39:49 zero-laptop kernel: [    0.003943] Brought up 2 CPUs
Jul 12 03:39:49 zero-laptop kernel: [    0.090127] migration_cost=54
Jul 12 03:39:49 zero-laptop kernel: [    0.090572] Booting paravirtualized kernel on bare hardware
Jul 12 03:39:49 zero-laptop kernel: [    0.090747] Time:  3:39:16  Date: 06/12/107
Jul 12 03:39:49 zero-laptop kernel: [    0.090845] NET: Registered protocol family 16
Jul 12 03:39:49 zero-laptop kernel: [    0.091007] EISA bus registered
Jul 12 03:39:49 zero-laptop kernel: [    0.091078] ACPI: bus type pci registered
** Jul 12 03:39:49 zero-laptop kernel: [    0.091287] PCI: BIOS BUG #81[49435000] found**
Jul 12 03:39:49 zero-laptop kernel: [    0.091357] PCI: Using configuration type 1
Jul 12 03:39:49 zero-laptop kernel: [    0.091427] Setting up standard PCI resources
Jul 12 03:39:49 zero-laptop kernel: [    0.104345] ACPI: Interpreter enabled
Jul 12 03:39:49 zero-laptop kernel: [    0.104418] ACPI: Using IOAPIC for interrupt routing
Jul 12 03:39:49 zero-laptop kernel: [    0.104981] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 12 03:39:49 zero-laptop kernel: [    0.105056] PCI: Probing PCI hardware (bus 00)
Jul 12 03:39:49 zero-laptop kernel: [    0.105844] Boot video device is 0000:00:02.0
Jul 12 03:39:49 zero-laptop kernel: [    0.106504] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Jul 12 03:39:49 zero-laptop kernel: [    0.106581] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
Jul 12 03:39:49 zero-laptop kernel: [    0.107653] PCI: Transparent bridge - 0000:00:1e.0
Jul 12 03:39:49 zero-laptop kernel: [    0.107796] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#06) (try 'pci=assign-busses')
```It says in that last line to *try 'pci=assign-busses'* but I'm not sure what that means. A little further down in the log it says to *use 'pci=route-irq'* as well, and I'm equally ignorant to what that's all about.

Since there doesn't seem to be any problems from these errors, does it even matter? I'm sure it matters somehow, or else whatever's going on wouldn't have its own error message.

Can anybody offer me any pointers? If it will help I can upload the entire log.

---

### Post by fiatguy85 on 2007-07-17
> **detroit/zero said:**
> 
```

Jul 12 03:39:49 zero-laptop kernel: [    0.091287] PCI: BIOS BUG #81[49435000] found

```

I too have noticed the same thing (also #81 and the following number are the same), with no apparent ill effects.  This is on a Gateway MX6453 Laptop.

---

### Post by detroit/zero on 2007-07-17
I've searched high and low and I can't find any info beyond the generic.

I'd like to know what I'm dealing with before I go and alter my bootloader with any of the recommended options.. i'd rather make somewhat of an educated guess than just take a stab in the dark. I've noticed from past experience that playing with those loader switched can open up cans of worms.. or maybe I just have bad luck.

---

### Post by fiatguy85 on 2007-07-18
I notice your log says brought up 2 CPUs.  What's in it?  Mine is dual AMD 64-bit, but i'm running the 32-bit OS.  (Acutally Linux Mint).

---

### Post by detroit/zero on 2007-07-18
P4 1.73GHz. This is for my laptop... desktop comp runs way hotter. It's nothing fancy.. just an off-the-shelf Toshiba Satellite  a135.

lspci for your viewing pleasure:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

---

### Post by pkl266 on 2007-07-19
I have this problem aswell, a Toshiba A135-4666 laptop, think it might be the same one as you detroit/zero.

I have tried passing both the "pci=routeirq" and "pci=assign-busses" option and I still get the error. I thought this error had something to do with my wireless not working but you say you're not getting any problems. I'll keep looking for more information on it.

PS: Did you have to do anything to make your wireless work? I've been having great difficulty with it.

---

### Post by detroit/zero on 2007-07-19
Actually, no. I was quite surprised. Everything was detected and worked right from the start. I was a little worried after reading some other people's horror stories, but it wasn't the case for me.

---

### Post by amphoterous on 2007-07-19
> **fiatguy85 said:**
> I too have noticed the same thing (also #81 and the following number are the same), with no apparent ill effects.  This is on a Gateway MX6453 Laptop.

I also have a Gateway MX6453 and I have the same problem. I wonder if anyone else with the same model has figured it out.

---

### Post by svartalfar on 2007-07-20
I don't think this message has much to do with laptop manufacturer/model. I have the same message on my Acer Aspire 5101AWLMi.
But all the hardware runs perfectly so far.

---

### Post by fiatguy85 on 2007-07-24
> **svartalfar said:**
> I don't think this message has much to do with laptop manufacturer/model. I have the same message on my Acer Aspire 5101AWLMi.
But all the hardware runs perfectly so far.

I agree, it doesn't seem to occur on a specific laptop from people's postings so far.  Why doesn't everyone post the output of lspci to see if there is something in common that may be causing this.  

```
$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

---

### Post by bradmayne on 2007-07-25
i have been getting bios error's also! this is a quick printout of what i've got. p.s everything is working!

brad@brad-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast devsel, latency 0
        Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d8000000-d9ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=56
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: dc000000-dc0fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: medium devsel, IRQ 20
        I/O ports at 18c0 [size=32]

04:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7106
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at 4000 [size=256]
        Memory at da000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at d4000000 [disabled] [size=64K]
        Capabilities: <access denied>

06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at dc006000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at dc005000 (32-bit, non-prefetchable) [size=2K]
        Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 18
        Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 20
        Memory at dc005800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

brad@brad-laptop:~$

---

### Post by amphoterous on 2007-07-25
Here is my lspci output:

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

---

### Post by brunomfs on 2007-07-28
Same here with my HP Pavilion DV2125US. Looking forward to know what this message means, although i am not experiencing any hardware issues.

---

### Post by fiatguy85 on 2007-07-28
From all of the posts so far, the one thing in common seems to be the TI Firewire port and Card reader.  I know my card reader works, with SD anyway.  Anyone use the firewire port?

---

### Post by amphoterous on 2007-07-29
All of the hardware seems to work fine so far. I've used my card reader as well and it worked perfectly. The only thing that didn't work out of the box was my sound.

---

### Post by detroit/zero on 2007-07-29
I use the card reader religiously, for getting photos off my camera - seems Ubuntu and Canon Cameras have some kind of history.. I can't get Ubuntu to recognize the camera when I try to connect the PC and camera via USB cable. Card reader works fine, though, so I'm not complaining.

I've never used the 1394 connection, though, so I don't know if that's an issue or not.

---

### Post by happygoodluck on 2007-07-29
"CPU runs way hotter" -- 
Not sure if this is your problem, but I had the same problem with my Toshiba Satellite A75. I foudn on another forum that it's very common for these laptops to get their CPU-cooling fan ducts clogged with dust. The way to solve is to get an air blower (I got one from an inflatable camping mattress) and blow into fans and any open slots on the bottom of the machine. Then, my laptop stopped getting so hot and shutting down randomly. It also helps to put somethign under it so more air can get through. 
Sorry - I don't know about the Linux stuff.

---

### Post by fiatguy85 on 2007-07-29
> **happygoodluck said:**
> "CPU runs way hotter" -- 
Not sure if this is your problem, but I had the same problem with my Toshiba Satellite A75. I foudn on another forum that it's very common for these laptops to get their CPU-cooling fan ducts clogged with dust. The way to solve is to get an air blower (I got one from an inflatable camping mattress) and blow into fans and any open slots on the bottom of the machine. Then, my laptop stopped getting so hot and shutting down randomly. It also helps to put somethign under it so more air can get through. 
Sorry - I don't know about the Linux stuff.

This is occuring on laptops of all brands.  And I am not having any cooling issues.  I believe it must be related to the card readers, firewire port, or the bus these are connected to.  **Still wondering if anyone has used the 1394 port?**  I would test it, but I have nothing that uses this.

---

### Post by ronaru on 2008-03-01
I'm very very new to Ubuntu. But I noticed I have the same bug. I don't know if is the bug but I don't get any audio. I'm running ubuntu gusty 7.10 on a Toshiba Satellite A135-S4727
Can anyone help me please?

---

### Post by detroit/zero on 2008-03-02
No, it's not that bug. I can't say I've noticed any adverse effects from that bug across three versions of Ubuntu going back to February of 2007.

I have the sound problem on my Satellite A135, too, every time I upgrade the kernel or the OS.

First, check your ALSA mixer settings; make sure you have the proper channels enabled to be controlled. For example, on my A135, I have the "front" channel for control of the laptop speakers. Enable every channel available and unmute/turn them all up to maximum, then go through them one by one to see which one controls the speakers. 

If that doesn't get you sound from your laptop speakers, then you may need to recompile ALSA. The method [outlined in this post]("http://ubuntuforums.org/showthread.php?t=539595&highlight=headphones+speakers") is as good as any for fixing the problem.

For headphone jack sensing (to turn off the laptop speakers when the headphones are plugged in), the last part where the author edits */etc/modprobe.d/alsa-base* is important, as well.

Good luck!

---

### Post by VMan on 2008-03-02
> Still wondering if anyone has used the 1394 port?
I haven't used it since 7.04, but it worked just fine then.  I got video off of a Panasonic camcorder and was able to use a firewire DVD writer.  I haven't tried it with 7.10 yet.  Been snowed under with other projects.  This is on a A135-S3367.  Only changes from stock are 2G RAM and a 250G HD.  

By the way, for anyone with a A135 series laptop, Bestbuy has memory sticks (ie. RAM) on sale for $30/G.  I upgraded my RAM to 2G for about $60.  One of the best things I have done in the way of performance/price upgrades.  If anyone wants the original two 512 RAM sticks, PM me.

---

### Post by detroit/zero on 2008-03-03
I've not used the 1394 on any of my versions of Ubuntu.

---

