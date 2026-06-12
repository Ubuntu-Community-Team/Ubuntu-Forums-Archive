---
title: "Epson LX-3WCH CH351Q PCI card I/O port disabled"
date: 2020-08-26
forum: Hardware
---

### Post by LannaD on 2020-08-26
Greetings. I have a slightly long thread here, so bear with me.

Recently I've been given an older printer (Epson LX-300+) that uses a  parallel port. I bought an LPT-to-USB cable that sort of managed to get  the work done, but I could only print one page in either Ubuntu or  Windows (dual boot) before the printer stopped responding and I had to  reset the computer. After that it would sometimes resume printing, but  not always and I needed something more reliable (I read somewhere that  these cables are to be avoided, if possible). I tried two different  LPT-to-USB cables and the results were the same.


 Since my motherboard (MSI Z97 PC Mate) has no built in parallel port  (although it's UEFI shows the option to enable/disable it and which mode  it should run in, which makes no difference for the card in Windows), I  purchased a WCH CH351 PCI card that provides a parallel port.

[ATTACH=CONFIG]286813[/ATTACH]

I got a mini-CD with it that contains Windows, Linux and Mac drivers,  and installing it on Windows went off without a hitch. The printer now  responds whenever I order it to print something immediately. It even has  some 8 shades mode that gives me very sharp images for a dot-matrix  printer in a 244x144 dpi resolution.

However, with Ubuntu it's a different story. Since the printer can and  does work using the PCI parallel port card in Windows (and occasionally  with the LPT-to-USB cable in both Windows and Ubuntu), the problem is  definitely between Ubuntu and the card driver. First off all, I get this  when I type **lspci -vv**:
> 05:01.0 Parallel controller: Device 1c00:2170 (rev 0f) (prog-if 01 [BiDir])
    Subsystem: Device 1c00:2170
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 255
    Region 0: I/O ports at c030 [disabled] [size=8]
    Region 1: I/O ports at c020 [disabled] [size=8]


editing **/sys/bus/pci/devices/0000:05:01.0/enable** to "**1**" enables the ports (even though there's only a single port on the card)

> 05:01.0 Parallel controller: Device 1c00:2170 (rev 0f) (prog-if 01 [BiDir])
    Subsystem: Device 1c00:2170
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 19
    Region 0: I/O ports at c030 [size=8]
    Region 1: I/O ports at c020 [size=8]


However, the printer is still not recognized when I try using "Add  Printer" feature (when I use the LPT-to-USB cable it always discovers  the printer as LX-300, plus it always finds a CUPS-BRF-Printer even when  there's nothing plugged in). The printing resolution is always stuck at  120x72 DPI, unless I use a custom PPD file, and even then it's always  doing a single monochrome shade.

I tried installing the drivers I got with the parallel card, but ended up getting this message every time I tried to use **make clean**, **make**, or **make install** in either **DRV_1PA**, or **DRV_1PB**  directory (I got the drivers off the mini CD that came with the card  and had to extract the linux ones from the .exe file for my particular  card model):
> make clean
make: *** No rule to make target 'clean'.  Stop.


If I open the Makefile files I can clearly see all the targets in it,  they're all properly tabbed, though I did have to change "SUBDIRS" to  "M", but that didn't help.

I am at the end of my wits here, and several pages of google results didn't help me, so I'd appreciate any input I can get here.

Thanks in advance.

---

