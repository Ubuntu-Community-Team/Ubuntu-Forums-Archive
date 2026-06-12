---
title: "Ubuntu muted after update"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by jet-san on 2009-11-07
_***EDIT: Solved (old kernel), cheers!***_

Hi there

Few days ago I upgraded my Ubuntu to version 9.10 - the Karmic Koala.
Like almost everytime after update I had to reinstall my graphic card drivers (ati-driver-installer-9-9-x86.x86_64) to enable Compiz and Visual Effects.
However for the first time I have a problem with my sound.
I can't hear either music or videos, nothing.

My PC
Processor:      Intel Core 2 Duo E8600
Memory:      4GB (2 X 2GB) Kingston PC6400 800Mhz DDR2
PCI-E Graphics:      512MB ATI HD4850
Sound Card:      Creative PCI Audigy SE 7.1

```

_@_:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
    Subsystem: ASRock Incorporation Device 29c0
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
    Subsystem: ASRock Incorporation Device 3662
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Prefetchable memory behind bridge: 00000000cff00000-00000000cfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 00000000cfe00000-00000000cfefffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
    Subsystem: ASRock Incorporation Device 27c8
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 4: I/O ports at b480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
    Subsystem: ASRock Incorporation Device 27c9
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at b800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
    Subsystem: ASRock Incorporation Device 27ca
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at b880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
    Subsystem: ASRock Incorporation Device 27cb
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 16
    Region 4: I/O ports at bc00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
    Subsystem: ASRock Incorporation Device 27cc
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at fe9fbc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: ASRock Incorporation Device 27b8
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: ASRock Incorporation Device 27df
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASRock Incorporation Device 27c0
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 0: I/O ports at b400 [size=8]
    Region 1: I/O ports at b080 [size=4]
    Region 2: I/O ports at b000 [size=8]
    Region 3: I/O ports at ac00 [size=4]
    Region 4: I/O ports at a880 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
    Subsystem: ASRock Incorporation Device 27da
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 5
    Region 4: I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: ASRock Incorporation Device 8136
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 2300
    Region 0: I/O ports at c800 [size=256]
    Region 2: Memory at cfeff000 (64-bit, prefetchable) [size=4K]
    Region 4: Memory at cfee0000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at feae0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
    Subsystem: Creative Labs Device 100a
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 5000ns max)
    Interrupt: pin A routed to IRQ 22
    Region 0: I/O ports at dc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: CA0106
    Kernel modules: snd-ca0106

04:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
    Subsystem: Giga-byte Technology Device 21c0
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 2299
    Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 2: Memory at febe0000 (64-bit, non-prefetchable) [size=64K]
    Region 4: I/O ports at e000 [size=256]
    Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx

04:00.1 Audio device: ATI Technologies Inc HD48x0 audio
    Subsystem: Giga-byte Technology Device aa30
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```I've been told to try installing the "alsa-firmware" package, but don't know how to do it.
Can anyone help me please?

Regards
Jet

---

### Post by Lateralis on 2009-11-07
If you want to install a specific package you can either use a GUI or the command line.  To make things easier for me (haha!) fire up a terminal (Applications->Accessories->Terminal) and type the following into the command line

```

sudo apt-get install alsa-firmware

```

This will install that specific package for you.  


But... I too had some sound issues with an Intel HD audio card in my laptop after upgrading from Jaunty to Karmic.  It seems like these problems have cleared up in the last few days, but I am not sure which update has fixed it, but I believe it is one from the proposed repository.

---

### Post by jet-san on 2009-11-07
```
_@_:~$ sudo apt-get install alsa-firmware
[sudo] password for damian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsa-firmware
_@_:~$ 

```

What does next to last line mean?
Is it alright?
Ok, I'm gonna restart now and we'll see.
Fingers crossed^^

---

### Post by jet-san on 2009-11-07
FAIL...
Dammit:(

---

### Post by Lateralis on 2009-11-08
Ah... I've just done a bit of digging and it looks like there isn't a package specifically called "alsa-firmware" in any of the repositories I check.  There is a package called alsa-firmware-loaders, however, which may be what you're after...

As a check, type the following into a terminal:

```

sudo aptitude search alsa-firmware

```

You should then (hopefully!) get this line: 

p   alsa-firmware-loaders       - ALSA software loaders for specific hardware      


If you want to install this package, just type:

[code]
sudo apt-get install alsa-firmware-loaders 
[code]

into the terminal.  Give it a minute or two and it should be done!  


Now, I suppose I should attach to the above a slight "health warning".  I have no idea if this will actually fix your sound card issues, nor do I know for definite if this is the package that someone else has suggested you need.  Certainly adding that particular package won't hurt your system, but if it does you can easily purge it from your system.  On that basis you could "suck it and see" but I personally couldn't tell you whether this will work or not.

---

### Post by jet-san on 2009-11-08
I have installed package you said, but unfortunately nothing has changed:(
```

sudo apt-get install alsa-firmware-loaders 

```

I took some screenshots, maybe this can help:
[http://img156.imageshack.us/img156/7466/soundpreferencesb.png](http://img156.imageshack.us/img156/7466/soundpreferencesb.png)
There is a label on the top left hand side and those 0.00 dB doesn't change when I watch YouTube nor playing Rythmbox.
Sorry for quality of this picture, but GIMP is not so easy as Paint;]

---

### Post by Lateralis on 2009-11-08
Well, I said that it might not work... and it hasn't. =P  Unfortunately, I'm not so good at trying to diagnose and fix these sorts of problems, but I'll try and give you as much help as I can.  (This should be a short post!)

It looks like the correct module is being loaded (snd-hda-intel) but lets check!  Type the following into the command line:

```

lsmod | grep snd*

```

This command will see which kernel modules are running (list modules; lsmod) and then filter out only the results which have snd at the start. 

You should see a line that looks like ```
snd_hda_intel          31880  2
```

If you don't, it means the module isn't being loaded.  In which case you can use 

```
sudo modprobe snd-hda-intel
```

This will add the module snd-hda-intel to the kernel, but only for the current session.   

I don't think anything I have said so far will help, but I always think it is worth to check...!


The only other thing I can say is that I did have some Intel HDA sound card problems after I upgraded from 9.04 to 9.10.  Occassionally when I booted the sound would work, other times it wouldn't.  This problem has now cleared up and I don't know why.  I suspect it is the result of an update from the proposed repository but I couldn't tell you which update is responsible.  (Or if that is definitely the reason why my sound issues have cleared up.)   

Somebody else may be able to offer you some more (and better!) advice, but in the meantime I'll keep thinking. =)

---

### Post by jet-san on 2009-11-08
That's what I get
```
_@_:~$ lsmod | grep snd*
snd_ca0106             46368  0 
snd_hda_intel         559028  0 
snd_ac97_codec        133848  1 snd_ca0106
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99464  4 snd_ca0106,snd_hda_intel,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78920  11 snd_ca0106,snd_hda_intel,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac97_bus               10368  1 snd_ac97_codec
soundcore              16800  1 snd
snd_page_alloc         18704  3 snd_ca0106,snd_hda_intel,snd_pcm

```As u see I have this line, but different value.
Does it matter?

Did I say thanks for your help?
If not, Thanks a lot m8 for your time!

Regards
Jet

---

### Post by Lateralis on 2009-11-08
Aw, your thanks isn't necessary - I enjoy helping!  :P  But thanks!  

Somebody else in another thread has got something quite similar to you, but both of my computers which both use Intel HDA cards have the same entry which is different from yours.  Just out of interest, type in the following: 

```
uname -r
```

This will tell you what kernel you're using.  My kernel is 2.6.31-14-generic and updating to this from an older one seems to have cleared up some sound problems I experienced on my laptop.

---

### Post by jet-san on 2009-11-09
Here u go
```
_@_:~$ uname -r
2.6.28-16-generic

```

---

### Post by jet-san on 2009-11-10
Btw i use 64bit version, but it probably doesn't matter.
Anyway - help...

---

### Post by jet-san on 2009-11-12
Can anyone explain how to install "alsa-driver-1.0.21" please?
I read doc inside, but I can't understand it:/

---

### Post by roofnron on 2009-11-12
You can try this. I had problems with my audio as well after installing. It worked perfect prior to karmic. 

I uninstalled pulseaudio and install gnome-alsamixer. 

You won't have volume icon if you uninstall pulseaudio though, but I have easy to reach volume control on my speakers. 

You can try this by itself first. 

[http://www.ubuntugeek.com/fix-for-no-sound-sound-blaster-audigy-after-upgrading-from-ubuntu-9-04-to-9-10.html]("http://www.ubuntugeek.com/fix-for-no-sound-sound-blaster-audigy-after-upgrading-from-ubuntu-9-04-to-9-10.html")

---

### Post by jet-san on 2009-11-13
Thanks for ur help m8, but it didn't work as well:(
I removed pulseaudio and install gnome-alsamixer and this is what I get.
[http://img404.imageshack.us/img404/9753/82921750.jpg](http://img404.imageshack.us/img404/9753/82921750.jpg)
No tabs and of course no sound:/
Now I'm thinking about "downgrade" my Ubuntu back to previous version.

Regards
Jet

---

### Post by jet-san on 2009-11-14
I thought maybe I can try clean install for Ubuntu 9.10, but can't find 64 bit version which I have at the moment.
"ubuntu-9.10-desktop-amd64.iso.torrent" - Is this one alright for me?

Regards
Jet

My PC
Processor:  	Intel Core 2 Duo E8600
Memory:  	4GB (2 X 2GB) Kingston PC6400 800Mhz DDR2
PCI-E Graphics:  	512MB ATI HD4850
Sound Card:  	Creative PCI Audigy SE 7.1

---

### Post by jet-san on 2009-11-15
I've just downloaded "ubuntu-9.10-desktop-amd64.iso", burned it and this is how my installation going:
[http://img26.imageshack.us/img26/3448/screenshotlh.png](http://img26.imageshack.us/img26/3448/screenshotlh.png)
I'm unable to do a clean install, because I can't even see any partition.
This is just so sad...

---

### Post by jet-san on 2009-11-15
This might be a reason why it doesn't work properly:
[http://img694.imageshack.us/img694/617/s6003148.jpg](http://img694.imageshack.us/img694/617/s6003148.jpg)
[http://img109.imageshack.us/img109/8817/s6003151.jpg](http://img109.imageshack.us/img109/8817/s6003151.jpg)
Is it my fault?

Regards
Jet

---

### Post by efflandt on 2009-11-15
The reason your sound was not working was because you were booted into the old kernel 2.6.28-16-generic and the modules are not for that version.  The modules are for 2.6.31-14-generic which should have been the default at the top of grub menu after you updated.

It looks like you had a bad burn or scratch on your install CD.  Keep them clean.

---

### Post by jet-san on 2009-11-15
At the moment in my grub list I only have 2.6.28-14-generic, -15 and -16 on the top of the list.
How can I update my kernel to 2.6.31-14-generic then?
You think it may help with my sound issue?
That would be great!

I also thought it's something wrong with my install CD, so I downloaded (from different source) and burned again - same error.
I believe it's not my fault.

Cheers
Jet

---

### Post by SurferGTO on 2009-11-15
same problem on an HP  DV2000

---

### Post by jet-san on 2009-11-15
Now I have to spend most time on Win XP, cuz I can listen my mp3 here only...

Anyway, how can I update my kernel?

---

### Post by Lateralis on 2009-11-16
First check to see if the new kernel is in the boot directory.  (It almost certainly is.)  

```

ls /boot/ | grep vmlinuz

```

You should see *something like*, although probably not identical to,

```

vmlinuz-2.6.28-16-generic
vmlinuz-2.6.31-14-generic
vmlinuz-2.6.31-15-generic

```

The 2.6.31 kernel is what ships with Ubuntu 9.10 by default.  You can add this to your grub menu by typing 

```

sudo update-grub

```

This will initiate a script that will search */boot* folder for kernels and add the necessary lines to grub's *menu.lst* file.

---

### Post by jet-san on 2009-11-16
Huh, u were right m8!
```
_@_:~$ ls /boot/ | grep vmlinuz
vmlinuz-2.6.28-16-generic
vmlinuz-2.6.31-14-generic
-@_:~$

```
I haven't edited my grub list, so I have no idea what happened.
Anyway I'm gonna add it straight way.
Hopefully it'll give me sounds back:)

---

### Post by jet-san on 2009-11-16
Omfg, it works!!!!!!!!!!!

Thank you so much Lateralis and efflandt!

P.S.
Do you also install graphic card drivers after every kernel update?

---

### Post by SurferGTO on 2009-11-16
not for me! my grub is up to date and still no sound..

---

### Post by SurferGTO on 2009-11-16
code:

> ~$ lspci -vv
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 10
	Region 0: I/O ports at 3080 [size=64]
	Region 4: I/O ports at 3040 [size=64]
	Region 5: I/O ports at 3000 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at fc200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fc486000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fc489000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fc487000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 16
	Region 0: Memory at fc489400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f03c:30d6
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at 30c0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fc480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=64
	Memory behind bridge: fc100000-fc1fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 221
	Region 0: I/O ports at 30f0 [size=8]
	Region 1: I/O ports at 30e4 [size=4]
	Region 2: I/O ports at 30e8 [size=8]
	Region 3: I/O ports at 30e0 [size=4]
	Region 4: I/O ports at 30d0 [size=16]
	Region 5: Memory at fc484000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 220
	Region 0: Memory at fc488000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at 30f8 [size=8]
	Region 2: Memory at fc489c00 (32-bit, non-prefetchable) [size=256]
	Region 3: Memory at fc489800 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f8000000-fbffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	Memory behind bridge: fc000000-fc0fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f0000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at c2000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: nvidiafb

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at fc100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 10
	Region 0: Memory at fc100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

01:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at fc100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: Hewlett-Packard Company Device 30d6
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at fc101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Hewlett-Packard Company Device 137c
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at fc000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ndiswrapper
	Kernel modules: wl


---

### Post by Lateralis on 2009-11-17
Hmmm... it looks like you have an nVidia sound card, but are using the Intel HDA driver.  

```


**00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)**
Subsystem: Hewlett-Packard Company Device 30d6
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0 (500ns min, 1250ns max)
Interrupt: pin A routed to IRQ 20
Region 0: Memory at fc480000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
[B]Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel[/B]

```

I have no idea what driver should be used with your particular hardware, but it seems odd to me that your system is trying to use an Intel driver with an nVidia sound card!  You may want to have see if you have to enable any restricted drivers: System -> Administration -> Hardware Drivers.  I'm willing to guess that you won't have any restricted drivers, so I'm suggesting this purely as a stalling tactic until I can think of a proper suggestion or someone good and knowledgable comes along to show you the way!  

@ jet-san 

You are quite welcome!  I'm glad that you have your sound back and that you are enjoying Karmic! =)

---

### Post by tetzauh on 2009-11-27
Reading this thread I read Jet Sans's case and it described exactly what happens to me, but the solution did not work. I did hear some clicking noises on reboot, but that was it. By the way, my sound prferences window shows nothing on the hardware tab. 

What else could it be?

---

### Post by atoztoa on 2009-12-05
> **tetzauh said:**
> Reading this thread I read Jet Sans's case and it described exactly what happens to me, but the solution did not work. I did hear some clicking noises on reboot, but that was it. By the way, my sound prferences window shows nothing on the hardware tab. 

What else could it be?

Have you tried ```
alsamixer
```

Pressing 'm' will mute/unmute each section...

_ATOzTOA
[www.atoztoa.com](www.atoztoa.com)

---

### Post by Patch1234 on 2009-12-05
> **jet-san said:**
> Here u go
```
_@_:~$ uname -r
2.6.28-16-generic

```
I just read this from one of the post regarding Ubuntu 9.10 sound problem, It solved my sound proble with my 9.10 installation. Many thanks to the person that posted this!

this is so simple it's worth trying-
go to: System >>Preferences >>Sound >>Input
..and see if the volume slider is very low ,or at'mute',
-as mine was-and raise the volume!
wishingwell,azeite.

---

