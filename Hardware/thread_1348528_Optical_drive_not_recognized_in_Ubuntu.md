---
title: "Optical drive not recognized in Ubuntu"
date: 2009-12-07
forum: Hardware
---

### Post by zami on 2009-12-07
I recently installed an SATA interface, Blu-ray optical drive.  It is supposed to also function as ye olde basic CD-ROM/DVD/CD drive.

Ubuntu doesn't recognize it, at all.  I don't expect it to read Blu-ray discs, but I do expect it to at least show up.

I've got a dual-boot Vista/Ubuntu 9.10 here.  I had to tell the BIOS to enable SATA support, and after doing that the drive showed up in Vista and works fine, so I know it works, it's connected correctly, the BIOS is hopefully set correctly... no love from Ubuntu though.

Any suggestions?

Is this an issue with the optical drive itself?  A driver issue?  An SATA issue?

Thanks for any help!

-zami


Ubuntu 9.10
Optical Drive : [http://www.newegg.com/Product/Product.aspx?Item=N82E16827106325&cm_re=liteon_blueray-_-27-106-325-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16827106325&cm_re=liteon_blueray-_-27-106-325-_-Product)

---

### Post by speedkreature on 2009-12-08
This is actually a little concerning.  I was going to get a Bluray burner to archive compressed video files (*.ogv as files, not as playable content on a bluray player)...I go through about 2TB of data a month and if this won't work I'm out of ideas and out of disk space.  I admit this wasn't a great solution to begin with, but it's all I could think of.  
I may not be able to solve your problem, but I'll at least help you keep the thread alive for as long as it's relevant.

Can you post some information about your drive?

Copying and pasting lspci output from the terminal may be helpful.

---

### Post by zami on 2009-12-08
Hey speedkreature, thanks for the bump!  I haven't had much time to wrestle with this drive, and probably wont for a few days, but I'll definitely post the solution if I figure this out.

Please don't be too discouraged by my problem, I'm 95% sure this is user ignorance! 

lspci output
```

~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV670PRO [Radeon HD 3850]
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:02.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster

```

The blu-ray player is the only thing on my computer using an SATA interface... at least lspci notes *something* is there...

Still gladly taking suggestions.  :D

-Laura

---

### Post by HappyFeet on 2009-12-08
> **zami said:**
> 
The blu-ray player is the only thing on my computer using an SATA interface... at least lspci notes *something* is there...

Still gladly taking suggestions.  :D

-Laura

Who is the manufacturer?

---

### Post by zami on 2009-12-09
> **HappyFeet said:**
> Who is the manufacturer?
Sorry I wasn't clear in the first post, that Newegg link is to the the info page for the drive.  (Actually, double checking I linked to the wrong one!  Same model, but I bought 'retail' instead of 'OEM'.)

Problem Drive : LITE-ON , model iHOS104-08 , Retail
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827106326](http://www.newegg.com/Product/Product.aspx?Item=N82E16827106326)

Motherboard : is an Intel Desktop Board D875PBZ
CPU: 2, Pentium4 3GHz
RAM: 2 GiB 

I pulled two fans and the working normal CD-Rom drive to test if this was a power issue - it wasn't. Heh!  Didn't hurt to try, right?  

-zami

---

### Post by petefox on 2009-12-19
I am having the same issue. Before I read your post, I read other recent (~12/9/09) posts about this issue at launchpad.com, I think it was.
 
I also have a LiteOn IHOS104 blueray drive, connected to a SATA port on an ASUS P5N-D motherboard. 
 
Ironically I can boot the Ubuntu 9.04 install CD using this drive, but the installation itself does not recognize the drive as IDE or SCSI...which is good, I suppose, as it isn't either of those, but bad in that it is a SATA ;-)
 
Also, I am having problems with the drive being detected by windows, I gather, because my system hangs when I attempt to boot windows (dual boot, w/ windows occupying primary partition)...well, it hangs randomly, but that's par for the course with windows. At least it hasn't been giving me BSODs since i updated the ASUS chipset driver (for windows).
 
Unfortunately, I do not believe this is a problem to ASUS, as they have yet to address it in a BIOS update...it's not listed as a bug fix, at any rate, in their list of BIOS updates.

---

### Post by petefox on 2009-12-19
I just thought of something else...but am not sure it is relevant, as I am not very knowledgable about SATA.
 
What I mean is, apparently (from something I read in its BIOS config., I gather) the P5N-D mobo uses an extended IDE interface for SATA...so maybe this is not true SATA, but some emulation, and this could be the problem?

---

### Post by petefox on 2009-12-20
I know this is not a Fedora forum, but it appears fedora has the same issue...
 
[https://bugs.launchpad.net/fedora/+source/linux/+bug/344093](https://bugs.launchpad.net/fedora/+source/linux/+bug/344093)

---

### Post by zami on 2009-12-22
Hey Petefox, thanks for sharing your detective work.

I still havn't solved the mystery here... I've pretty much given up.  Though I would love to at least pinpoint the problem - drive? BIOS settings? SATA + Ubuntu?  SATA+Linux? - because I need to get a drive that can read SD cards and need to know if I should avoid the SATA interface.

Did you ever get Windows to boot back up?

I might try a third partition and installing another Linux distro, since the Fedora link you gave hints that other versions and/or distros detect the drive just fine.  I don't expect much but it's worth a try, even if just to help pinpoint the problem.

So.  Shameless bump for each of us.

Anyone have a suggestion?
:popcorn:

Thanks!
-zami

---

### Post by gaz2373 on 2009-12-31
Hi I have this same problem with the drive Geforce 6100 motherboard but found that installing an older version of linux detected the drive fine. Mandriva 2007. installed kernel 2.6.17 and detected the drive this doesn't solve this issue but could help someone who is more experienced identify the changes between these two kernels?  [https://bugs.launchpad.net/ubuntu/+bug/344093](https://bugs.launchpad.net/ubuntu/+bug/344093)

I will try and download Ubuntu 7.04 and see if it works on this or it is distro specific.

---

### Post by gaz2373 on 2010-01-01
Tried 7.04 but the kernel was 2.6.20 and didn't work so will have to look around for the .17 and try again when I get a chance.

---

### Post by wyleb2 on 2010-02-27
Has anyone gotten anywhere with this? Have the same problem with a LiteOn BD/DVD drive, BIOS recognises it but Ubuntu doesn't

---

### Post by Galban on 2010-02-28
Same problem, different maker/model. LG WH08LS20K BD-rom is not detected under Ubuntu Karmic. But it does works without any problems under Windows 7. Simply, the linux kernel does not recognize it. Looking forward for answers.

---

### Post by trorion on 2010-03-10
I don't know about the lite-on ones but the LG version works if you set your bios to recognize it as PATA (or IDE).  My linux didn't recognize it when I had it as SATA but it's fine as IDE.

---

### Post by speedkreature on 2010-03-11
Purchased a Panasonic BD-R drive (the only one currently sold on Newegg.com) and it works just as it should (given the lack of support for encrypted movies).  I can read all BluRay media and writing to BD-R's is just fine.

I should probably mention that I have not fully tested all functions of this drive.  For example, I have not tried dual layer BD-R's and I have not written more than the capacity of a single layer DVD to a BD-R in any of my tests.  I simply haven't gotten to it yet.  I'll do my first full video backup on Friday.

---

### Post by ascendotuum on 2010-03-14
Same problem here as well. Lite-On iHOS104 SATA Bluray drive that shows up in the BIOS, works in Windows, but not in Ubuntu. I'm running Ubuntu 9.10

Motherboard is an ASUS P5N-D (nvidia chipset)

Relevant part of my dmesg

[    1.476164] ata3.00: ATAPI: ATAPI   iHOS104, WL06, max UDMA/100
[    1.480359] ata1.00: ATA-7: Hitachi HDS721616PLA380, P22OABEA, max UDMA/133
[    1.480363] ata1.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    1.492191] ata3.00: configured for UDMA/100
[    1.496372] ata1.00: configured for UDMA/133
[    1.818459] ata2: SATA link down (SStatus 0 SControl 300)
[    6.492014] ata3.00: qc timeout (cmd 0xa0)
[    6.492018] ata3.00: TEST_UNIT_READY failed (err_mask=0x4)
[    6.960033] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.984186] ata3.00: configured for UDMA/100
[   11.984020] ata3.00: qc timeout (cmd 0xa0)
[   11.984024] ata3.00: TEST_UNIT_READY failed (err_mask=0x4)
[   11.984027] ata3: limiting SATA link speed to 1.5 Gbps
[   11.984029] ata3.00: limiting speed to UDMA/100:PIO3
[   12.452033] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   12.476186] ata3.00: configured for UDMA/100
[   17.476018] ata3.00: qc timeout (cmd 0xa0)
[   17.476022] ata3.00: TEST_UNIT_READY failed (err_mask=0x4)
[   17.476024] ata3.00: disabled
[   17.476036] ata3: hard resetting link
[   17.476038] ata3: nv: skipping hardreset on occupied port
[   17.944031] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   17.944039] ata3: EH complete
[   18.266454] ata4: SATA link down (SStatus 0 SControl 300)
[   18.439370] Write protecting the kernel read-only data: 1840k

lspci -v -k

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: 66MHz, fast devsel

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: bus master, 66MHz, fast devsel, latency 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
    Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
    I/O behind bridge: 0000a000-0000dfff
    Memory behind bridge: f2000000-fbffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000efffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 81bc
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device 81bc
    Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device 81bc
    Flags: 66MHz, fast devsel, IRQ 255
    I/O ports at 1c00 [size=64]
    I/O ports at 1c80 [size=64]
    Capabilities: <access denied>
    Kernel modules: i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device 81bc
    Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81bc
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 81bc
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 81bc
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at fd00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 81bc
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at f800 [size=16]
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 81bc
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at 09e0 [size=8]
    I/O ports at 0be0 [size=4]
    I/O ports at 0960 [size=8]
    I/O ports at 0b60 [size=4]
    I/O ports at f300 [size=16]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=128
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fdf00000-fdffffff
    Prefetchable memory behind bridge: fde00000-fdefffff
    Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 829e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device 8221
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f200 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

01:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=01, secondary=02, subordinate=06, sec-latency=0
    I/O behind bridge: 0000a000-0000dfff
    Memory behind bridge: f2000000-fbffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000efffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

02:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f2000000-f5ffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

02:01.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=02, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fbf00000-fbffffff
    Prefetchable memory behind bridge: 00000000eff00000-00000000efffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

02:02.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=02, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f6000000-f9ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

02:03.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=02, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fbe00000-fbefffff
    Prefetchable memory behind bridge: 00000000efe00000-00000000efefffff
    Capabilities: <access denied>
    Kernel modules: shpchp

03:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 0910
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at f2000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at f5fe0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

05:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 0910
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f6000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at bc00 [size=128]
    [virtual] Expansion ROM at f9000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

07:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 81fe
    Flags: bus master, medium devsel, latency 32, IRQ 18
    Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

---

### Post by Quarn on 2010-06-14
Same thing for me, I actually have: 

5 HD who are SATA 
1 DVD IDE
1 Blue-Ray SATA

and the only thing who doesn't work is the Blue-Ray, 
so it's not only a SATA problem, but more a Blue-Ray on SATA problem

Tried it on Windows 7 and XP and everything work fine:popcorn:

---

### Post by tylersontag on 2010-07-14
Galban, i'm looking to buy a "LG WH10LS30K" BD-Burner.  Have you had any lick gettting your model to work?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16827136181](http://www.newegg.com/Product/Product.aspx?Item=N82E16827136181)

---

### Post by ds_pablo on 2010-07-18
I am having the same problem with my Lite-On iHOS104 Blu-Ray drive.  Running Ubuntu 10.04.

Uname -a: 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux


Relevant dmesg output:
```
[    2.605933] ata6.00: ATAPI: ATAPI   iHOS104, WL0D, max UDMA/100
[    2.645944] ata6.00: configured for UDMA/100
[    7.645905] ata6.00: qc timeout (cmd 0xa0)
[    7.645910] ata6.00: TEST_UNIT_READY failed (err_mask=0x4)
[    8.135928] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    8.196042] ata6.00: configured for UDMA/100
[   13.196002] ata6.00: qc timeout (cmd 0xa0)
[   13.196007] ata6.00: TEST_UNIT_READY failed (err_mask=0x4)
[   13.196010] ata6: limiting SATA link speed to 1.5 Gbps
[   13.196012] ata6.00: limiting speed to UDMA/100:PIO3
[   13.686027] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   13.746140] ata6.00: configured for UDMA/100
[   18.746100] ata6.00: qc timeout (cmd 0xa0)
[   18.746104] ata6.00: TEST_UNIT_READY failed (err_mask=0x4)
[   18.746106] ata6.00: disabled
[   18.746118] ata6: hard resetting link
[   18.746120] ata6: nv: skipping hardreset on occupied port
[   19.236124] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   19.236133] ata6: EH complete

```

lscpi:
```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

```

Anyone here have any luck yet?  I have a biostar motherboard (MCP6P M2+ 6.x I think) and have tried all the various SATA settings and other settings in the bios I could find.  None of the bios updates on the website appear to be related to this issue and everything else is working fine so I am avoiding updating the bios.  The BR Drive does not appear to have a firmware update either.

---

### Post by ds_pablo on 2010-07-18
I found this patch for use with the 2.6.32 kernel and nVidia MCP51 or MCP55 SATA controller.  I am going to try it out to see if it solves my problem too.

[http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=1170613;page=1;mh=-1;list=linux;sb=post_latest_reply;so=ASC](http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=1170613;page=1;mh=-1;list=linux;sb=post_latest_reply;so=ASC)

---

### Post by freezkatlodge on 2010-08-29
So what you are saying is this issue is low priority because it only effects a couple bd-rom drives that are on specific nvidia chipsets. The link in the previous post found the fix but it was never implemented anywhere. Since everybody is going to the "Linux Kernel" there is no option for the non-self-patching crowd but to use older kernels,  or use Microsoft Windows

---

### Post by nyteryder79 on 2010-10-28
Don't feel bad, I have AMD/ATI combo on my workstation at work.  It's an HP Pavilion Elite with blu-ray and it fails miserably.  When Ubuntu boots, all power is cut completely to the blu-ray drive.  I can't even hit the eject button to pop the tray open.  Yet when I boot into Windows, it works perfectly.  Here's the relevant portion of my dmesg:


[   11.810854] ata3: softreset failed (device not ready)
[   21.820854] ata3: softreset failed (device not ready)
[   32.430018] ata3: link is slow to respond, please be patient (ready=0)
[   56.850018] ata3: softreset failed (device not ready)
[   56.850022] ata3: limiting SATA link speed to 1.5 Gbps
[   62.080018] ata3: softreset failed (device not ready)
[   62.080020] ata3: reset failed, giving up

The last line there made me laugh.  "reset failed, giving up".  And people are supposed to take Ubuntu seriously?  I love the OS, but it's stuff like this Canonical, stuff like this!

---

### Post by gunnarflax on 2010-11-21
Just want to bump this because I have the exact same problem with a LG CH10 Blu-Ray on an amd-motherboard (gigabyte 880gma-ud2h)

---

### Post by Lukas32 on 2010-11-21
Hey, I'm having trouble with my drive to. It's about 2 weeks old. Here are the specs:

LG Internal/GH22 Super Multi DVD Rewriter 22x (with LightScribe)

Here is the error that I get when trying to install the disc:

Archive:  /media/SuperMulti/AutoRun/AutoRun.exe
[/media/SuperMulti/AutoRun/AutoRun.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/SuperMulti/AutoRun/AutoRun.exe or
          /media/SuperMulti/AutoRun/AutoRun.exe.zip, and cannot find /media/SuperMulti/AutoRun/AutoRun.exe.ZIP, period.

I'm am very new to Ubuntu, so maybe this is just a quick fix. I know this drive works because I installed it on Windows XP and installed Ubuntu with it.

---

### Post by bejinx on 2011-08-19
I just picked up a LITE-ON iHOS104 for my media box, and it still has issues with linux.  Windows 7 is fine.  

Various flavors of 11.04 dont like it, vannilla ubuntu 10.04 installed but doesnt recognize the drive afterwards.  

A kernel patch [**from here**]("http://www.gossamer-threads.com/lists/linux/kernel/1230167#1230167") is supposed to work but Ive never patched the kernel before.  

Going to try it this weekend, if I can't get it to work I will just return it.

---

### Post by mc@2 on 2011-12-05
I've been stuck with a non functioning ihos104+AT3IONT-I (Nvidia ION) for quite a while now. I've upgraded to 11.10 but it still fails. Any suggestions how to fix this?

---

### Post by gunnarflax on 2011-12-06
Sorry but I don't know anything that might help you. I gave up and bought a LITE-ON iHOS104 and it worked out of the box for me, no trouble at all.

---

