---
title: "NetGear WG511 CardBus on Kubuntu"
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by srinivas1729 on 2006-01-02
I just installed kubuntu breezy on my compaq r3000 laptop and was impressed with it. I'm trying to get my NetGear WG511 CardBus PCMCIA card working with it and have been browsing thru the various sources of info online. One thing I am confused by.

When I plug the card in, I don't see any response from the system or the card. The cards lights don't come on. When I check /var/log/syslog, I don't see any msgs from cardmgr. When I unplug the card, I do see this error msg:

Jan  2 01:44:07 localhost kernel: [  535.963991] PCMCIA: socket ffff810018479c50: *** DANGER *** unable to remove socket power

I was hoping someone could give me some tips as to what I should do. Thanks in advance.

---

### Post by metalgorgar on 2006-01-03
I have just fixed this same problem on my presario v2000 . The problem is that one of the pci bridges is not set up correctly, so it does not know how to talk to any pcmcia cards.

go to a terminal window and type

lspci -vv

and post the output here, and I will show you how to get it working

---

### Post by Jeff924 on 2006-01-07
I have the same problem... I have just installed Ubuntu 5.10 on my Compaq Presario 2100 and it installed easily. My Netgear PCMCIA wireless card (WG511 v2) is not working. Can it be that the pci bus is not set up properly?

I executed the command "lscpi -vv" (it took me few tires to realize that is was actually 2 'v' and not a 'w')...   Here is the results any way


***************************
0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Region 0: Memory at d4000000 (32-bit, prefetchable) [size=64M]
        Region 1: Memory at d0500000 (32-bit, prefetchable) [size=4K]
        Region 2: I/O ports at 8090 [disabled] [size=4]
        Capabilities: [a0] AGP version 2.0
                Status: RQ=16 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
                Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x4
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: e0000000-efffffff
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 0024
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (20000ns max)
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at d0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [60] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 0024
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR+ <PERR+
        Interrupt: pin A routed to IRQ 5
        Region 0: I/O ports at 8400 [size=256]
        Region 1: Memory at d0001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
        Subsystem: ALi Corporation ALI M1533 Aladdin IV ISA Bridge
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: [a0] Power Management version 1
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company: Unknown device 0024
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 3
        Region 0: Memory at d0002000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at 8800 [size=256]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6912 Cardbus Controller
        Subsystem: Hewlett-Packard Company: Unknown device 0024
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 80000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 81000000-81100000 (prefetchable)
        Memory window 1: 1c000000-1c3ff000
        I/O window 0: 00003000-0000307f
        I/O window 1: 00004000-000040ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
        16-bit legacy interface ports at 0001

0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if b0)
        Subsystem: Hewlett-Packard Company: Unknown device 0024
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 1000ns max)
        Interrupt: pin A routed to IRQ 0
        Region 4: I/O ports at 8080 [size=16]
        Capabilities: [60] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Hewlett-Packard Company: Unknown device 0024
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
        Subsystem: Hewlett-Packard Company: Unknown device 0024
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 90 (2750ns min, 13000ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at 8c00 [size=256]
        Region 1: Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=320mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME+

0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1 (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company: Unknown device 0024
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B+
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 66 (2000ns min), Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Region 1: I/O ports at 9000 [size=256]
        Region 2: Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [58] AGP version 2.0
                Status: RQ=48 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2,x4
                Command: RQ=16 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x4
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

******************************

Can someone help me?

Thanks

Jeff

---

### Post by metalgorgar on 2006-01-08
In your case I don't think it is the same problem I had.

If you have a look at the entry for the cardbus bridge in yours you will see this
 >> Bus: primary=00, secondary=02, subordinate=05, sec-latency=176

what this means is that the cardbus bridge is on the main pci bus with no other bridges in between. It was one of the in between bridges which was my problem.

However look at this page [http://www1.pacific.edu/~khughes/presario-r3120us/]("http://www1.pacific.edu/~khughes/presario-r3120us/")
and look at the PCMCIA section.  It may be the fixes for IO Ranges will help you.

Do you see any messages in your system log when you unplug the card.

---

### Post by Jeff924 on 2006-01-08
Thanks for the advice... But I don't feel expert enoug to go through all this memory allocation change.

I noticed that it is somewhat detected in the device mansager. When I plug the card in, a new line appear under "Cadrbus Controller". The new line says: "Unknown (0x1faa). The string pci.subsys_vendore says: "Netgear" so it seems to be identified.

My card is the WG511 v2 made in China... I read somewhere else that these v2 made in China are a bit tricky...

Is it still the Prism54 chipset? I tried to load the Prism54 chipset by using the command "modprobe prism54" but nothing happened. the output of "cartctl ident" gives:


jeff@JeffLinux:~$ cardctl ident
Socket 0:
  no product info available


and "cardctl info" gives:

jeff@JeffLinux:~$ cardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


Does anyone has an idea of where to start looking?

Thanks

Jeff

---

### Post by mabster on 2006-01-09
I'm not sure about the PCI bridge stuff.

I have the same card (the chinese version), and yes it is more complicated, unfortunately.  You can have a look at what's been said on [http://ubuntuforums.org/showthread.php?t=114122](http://ubuntuforums.org/showthread.php?t=114122).  You basically need to install ndiswrapper which is a wrapper around the card's WinXP driver.

---

### Post by Jeff924 on 2006-01-09
I installed the ndiswrapper and everything is working perfectly now :p . I will perform some tests in the coming days and let you know if there is any bugs.

Note: Ubuntu is not provided with gcc-3.4 but when I wanted to compile the ndiswrapper, it required it (I assume because the kernel was compiled with gcc-3.4). It took me some effort to get the gcc-3.4 packages ](*,) ...

Thanks


Jeff

---

### Post by mabster on 2006-01-10
I just apt-get'd ndiswrapper ;)  The version with ubuntu worked great!

---

### Post by healychan on 2006-01-10
I have the same card. I can installed the driver and get it to work.

But it is inconsistent, always hang when I change the setting.

First things need to do is identify your card.
What version your card is??? v1 or v2
Also is it "made in Taiwan" or "made in China". I know that Taiwan one works fine with ndiswrapper but not the China one. I have the China one and it is very inconsistent. Always hang.....

Type "lspci" and see what chipset your card is.

---

### Post by mabster on 2006-01-10
It's a v2 and does indeed come from China, and it has been working completely fine.  As far as I understood, the Taiwanese version works straight off the bat because the driver is already supplied (prism54) but the Chinese version doesn't unless you install ndiswrapper (which is more painful).

```
mabster@ubuntu:~$ lspci -vv
<snip>

0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)
        Subsystem: Netgear: Unknown device 4e00
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at 20800000 (32-bit, non-prefetchable) [size=64K]
        Region 1: Memory at 20810000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
mabster@ubuntu:~$ lspci -n
<snip>
0000:03:00.0 0200: 11ab:1faa (rev 03)
```

What do you mean hangs when you change settings?  Did you install the driver the wiki suggested or the ones off the CD?  How is the wifi connection setup (restricted/WAP/etc.) ?

---

### Post by healychan on 2006-01-10
My situation is special. I have more than one access point and I have to switch between them. Everytime I do the setting it hang. Even I did nothing, it still hang sometime. Did you ever hang when using this card?? Which driver did you used??

You said your card works fine. Do you mind to output the result of "ls /etc/ndiswrapper/wg511v2" for me as a reference??

---

### Post by mabster on 2006-01-10
I used the driver that the ndiswrapper webpage pointed me to (Card: Digitus DN-7006G/E (802.11a/b/g) PCI card [http://downloads.trendnet.com/TEW-421PC_B1/Driver/Utility_Driver_TEW-421PC_423PI_b1_2.00.zip)](http://downloads.trendnet.com/TEW-421PC_B1/Driver/Utility_Driver_TEW-421PC_423PI_b1_2.00.zip)).  This is called mrv8000c as you'll see below.

I've seen a few people use a driver called 'wg511v2'. Was that a rename of the driver above or the one off the CD?  If it's the one off the CD then apparently that's bad (the driver info above had a note that the drivers shipped with the wg511v2 don't work with ndiswrapper).  I'd like to know the source of your driver for reference :)...

```
mabster@ubuntu:~$ ls /etc/ndiswrapper/mrv8000c/
11AB:1FAA.5.conf  mrv8000c.inf  mrv8000c.sys
```

And yes, my card has had no troubles at all.  I've been using it for about 10 hours a day for about a week now and haven't had a single disconnection / lockup.

---

### Post by healychan on 2006-01-10
[QUOTE=mabster]I've seen a few people use a driver called 'wg511v2'. Was that a rename of the driver above or the one off the CD?  If it's the one off the CD then apparently that's bad (the driver info above had a note that the drivers shipped with the wg511v2 don't work with ndiswrapper). [/QUOTE]

In the wiki I read, it said that using the Win2000 driver come with CD will be fine. That's why I used the driver come with CD. I will try your driver as well. And thank you so much you share your information with me:p

This is the wiki I read [https://wiki.ubuntu.com/NetgearWG511AndNdiswrapper](https://wiki.ubuntu.com/NetgearWG511AndNdiswrapper)

I will post it after I have lunch.

---

### Post by mabster on 2006-01-10
That would explain why a few people have tried to install that driver.  It'd be interesting to see what the differences are.  Shout how it went!

Sure, no problem (it's bed-time here anyway ; ).

---

### Post by healychan on 2006-01-10
Oh...I find the ndiswrapper page you mention before. According to that wiki, WG511 v2 shouldn't use the driver that you are using.

I would like to make sure one thing, which is the card model.
I am using WG511 v2, made in China, the chipset is made by Marvell.

I guess your card is not the same as my one.
Your one should be WG511 v3, made in China, chipset is Intersil

So, there are two possibilities.

1. Your card are v3 instead of v2, so that your card works fine.
2. Your card are the same card as me, which is v2. But you didn't follow the instruction of ndiswrapper and installed Intersil driver. And you are very lucky to get the card work.

which one is it then??

---

### Post by mabster on 2006-01-10
Ok, after a look through all this it seems to have been a big screw up on my part that has somehow worked.

Here's what mine says on the card itself, just pulled it out:

NETGEAR
54 Mbps Wireless PC Card
WG511 v2
Made in China

```
mabster@ubuntu:~$ lspci
<snip>
0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)
mabster@ubuntu:~$ lspci -n
<snip>
0000:03:00.0 0200: 11ab:1faa (rev 03)
```

So I can confirm all the Marvell Technology part of it.

Now, on the driver list ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)), I just looked for that lspci identifier (11ab:1faa).  Funnily enough I came up with heaps of entries that had that identifer?!  For some reason I chose:

[INDENT]Card: Digitus DN-7001G MV (802.11a/b/g) PCMCIA
[LIST][*]Chipset: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)
[*]pciid: 11ab:1faa (rev 03)
[*]Driver: [http://downloads.trendnet.com/TEW-421PC_B1/Driver/Utility_Driver_TEW-421PC_423PI_b1_2.00.zip](http://downloads.trendnet.com/TEW-421PC_B1/Driver/Utility_Driver_TEW-421PC_423PI_b1_2.00.zip)
[*]Other: Does not seem to work with the delivered drivers, The XP ones from trendnet (Mrv8000c.*) seem to work well, tested on 2.6.10 (Ubuntu Hoary), there might be other chipsets in use, check below for Trendnet devices.[/LIST][/INDENT]

It seems that I typed "1faa" into firefox search and that's the first entry it came up with.  Now I'm not sure /why/ that works, and I should probably contact someone at ndiswrapper about it.  Note though that the identifier is exactly the same.  I have a vague suspicion that multiple vendors are using  the same chipset but branding it as their own card.

But that driver definitely has been working (and it's been more stable under Linux than it ever was under Windows).  I'd suggest giving it a go either way to see if it solves your problems.

---

### Post by healychan on 2006-01-10
Thank you for your patient. I am now pretty sure that your card is the same as my.;) 

Reason I asked too much and deep is because there are too many uncertain things about wireless. I guess this is the most popular topic in this forum.

> Funnily enough I came up with heaps of entries that had that identifer?! For some reason I chose:
You were just so lucky to get that driver:rolleyes: 

I will give it a try and thanks again

---

### Post by mabster on 2006-01-10
That's not a problem :)  I liked the ubuntu community because they *do* take time out to help so it's only fair to try help in return (and I've only been a linux kid for less than a week, go figure ;)...

I've posted this situation to the ndiswrapper forums.  Let's see what they have to say.....  I don't believe I've suggested that driver to a few people now ;)  Be interesting to see what the consensous is!

If it *doesn't* help your situation then I'll try an uninstall the driver on my machine and install the correct driver so that we're using the exact same setup.

---

### Post by healychan on 2006-01-10
One more question. After you unzip the file, there are 4 kind of drivers. Which one did you used.

---

### Post by healychan on 2006-01-10
One more question. After you unzip the file, there are 4 kind of drivers. Which one did you used.

---

### Post by healychan on 2006-01-10
:( I tried the driver you provided. It doesn't work. It still hang when I do the command like "sudo ifup wlan0". I couldn't switch between AP.
It doesn't work because my case is a bit special. For people like you, having only 1 AP should have no problem with it.
It was OK because I was on holiday, I only use the AP at home, I can browse whatever I like with that card. Since my term start again, I need to bring my laptop to school and using school's AP.

Fortunately I have a USB adapter which working perfectly with Ubuntu.
I will wait for the ndiswrapper update and see if they can support the card better.

Good luck all.

---

### Post by srinivas1729 on 2006-02-02
I'm the person who had initially posted the message. This is my output with lspci -vv. Hoping someone can help me get my card working. Thanks.

0000:00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
	Subsystem: nVidia Corporation: Unknown device 0c80
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

0000:00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
	Subsystem: Hewlett-Packard Company: Unknown device 006d
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 10
	Region 4: I/O ports at 2040 [size=64]
	Region 5: I/O ports at 2000 [size=64]
	Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5) (prog-if 10 [OHCI])
	Subsystem: nVidia Corporation: Unknown device 0c80
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at e8000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5) (prog-if 10 [OHCI])
	Subsystem: nVidia Corporation: Unknown device 0c80
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 20
	Region 0: Memory at e8001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <available only to root>

0000:00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2) (prog-if 20 [EHCI])
	Subsystem: nVidia Corporation: Unknown device 0c80
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin C routed to IRQ 22
	Region 0: Memory at e8004000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
	Subsystem: Hewlett-Packard Company: Unknown device 006d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: I/O ports at 1400 [size=256]
	Region 1: I/O ports at 1c00 [size=128]
	Region 2: Memory at e8002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <available only to root>

0000:00:06.1 Modem: nVidia Corporation: Unknown device 00d9 (rev a2) (prog-if 00 [Generic])
	Subsystem: Hewlett-Packard Company: Unknown device 006d
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 22
	Region 0: I/O ports at 1800 [size=256]
	Region 1: I/O ports at 1c80 [size=128]
	Region 2: Memory at e8003000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <available only to root>

0000:00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5) (prog-if 8a [Master SecP PriP])
	Subsystem: nVidia Corporation: Unknown device 0c80
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Region 4: I/O ports at 2080 [size=16]
	Capabilities: <available only to root>

0000:00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
	I/O behind bridge: 00003000-00007fff
	Memory behind bridge: e8100000-e97fffff
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-

0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 16
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
	Memory behind bridge: ea000000-eaffffff
	Prefetchable memory behind bridge: f8000000-fc0fffff
	BridgeCtl: Parity+ SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3) (prog-if 00 [VGA])
	Subsystem: Hewlett-Packard Company: Unknown device 006d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (1250ns min, 250ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at ea000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Region 2: Memory at fc000000 (32-bit, prefetchable) [size=512K]
	Capabilities: <available only to root>

0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Hewlett-Packard Company: Unknown device 006b
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (8000ns min, 16000ns max)
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at 7000 [size=256]
	Region 1: Memory at e8104000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <available only to root>

0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
	Subsystem: Hewlett-Packard Company: Unknown device 12f4
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at e8100000 (32-bit, non-prefetchable) [size=8K]

0000:02:04.0 CardBus bridge: Texas Instruments: Unknown device ac54 (rev 01)
	Subsystem: Hewlett-Packard Company: Unknown device 006d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168, Cache Line Size: 0x10 (64 bytes)
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at e8102000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: e8200000-e83ff000 (prefetchable)
	Memory window 1: e8400000-e85ff000
	I/O window 0: 00004000-000040ff
	I/O window 1: 00004400-000044ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
	16-bit legacy interface ports at 0001

0000:02:04.1 CardBus bridge: Texas Instruments: Unknown device ac54 (rev 01)
	Subsystem: Hewlett-Packard Company: Unknown device 006d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168, Cache Line Size: 0x10 (64 bytes)
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at e8103000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: e9000000-e93ff000 (prefetchable)
	Memory window 1: e8c00000-e8fff000
	I/O window 0: 00006000-00006fff
	I/O window 1: 00005000-00005fff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

0000:02:04.2 System peripheral: Texas Instruments: Unknown device 8201 (rev 01)
	Subsystem: Hewlett-Packard Company: Unknown device 006d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (1750ns min, 1000ns max), Cache Line Size: 0x10 (64 bytes)
	Region 0: I/O ports at 7400 [size=64]
	Capabilities: <available only to root>

---

### Post by mabster on 2006-02-03
I noticed that your cardbus is labeled as an unknown device (AC54).  I googled 'texas instruments ac54) and came up with the following:

[http://www1.pacific.edu/~khughes/presario-r3120us/](http://www1.pacific.edu/~khughes/presario-r3120us/)
[http://ubuntuforums.org/archive/index.php/t-39379.html](http://ubuntuforums.org/archive/index.php/t-39379.html)

Unfortunately kernel patches are unknown territory so I won't be able to help there :-/

I also noticed that you have a Broadcom 802.11b card already in the laptop?!  If you want to install that, apparently ndiswrapper is the way to go.

Oh, and I found this, specific to your laptop:
[http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/](http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/)

---

### Post by srinivas1729 on 2006-02-03
Thanks for the tip. The broadcom card is not an option right now since I'm running in 64-bit mode and the broadcom win drivers are 32-bit. I've looked at the other two and might try them.

Its funny. I made the initial posting and went on vacation for 3 weeks. I was surprised to see all the activity when I checked it yesterday. Only problem was that my specific case hadn't been covered :-).

---

### Post by mabster on 2006-02-03
Hahaha, that seems to happen on these forums a fair bit.

I think you may know all this already, but I thought I'd post it for brevity: Now, either way it appears that you're going to be using ndiswrapper because neither the broadcom nor the netgear wg511 have linux drivers.  That said, ndiswrapper supports 64-bit ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#Can_I_use_ndiswrapper_in_64-bit_mode_for_AMD64.3F)](http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#Can_I_use_ndiswrapper_in_64-bit_mode_for_AMD64.3F)).

I tried to hunt for the 64-bit drivers but with not much luck.  Does ndiswrapper have a 64-bit section with lspci identifiers -> drivers?

Either way, good luck ;)

---

