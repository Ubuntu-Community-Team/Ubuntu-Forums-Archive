---
title: "how to reinstall audio driver?"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by pearlygate on 2009-04-10
Hi,
my audio does not work in ubuntu. I just replaced my mobo to asus m3a78. I used gigabyte mobo before and gigabyte use realtek chipset whereas asus uses VIA chipset I think. 

Is there a way to reconfigure the audio, I bet there's a driver conflict somewhere but if I can restart the audio configuration process (without reformatting and re-installing ubuntu), ubuntu will "know" which driver to use automatically. 

Can anyone help?

Thank you

---

### Post by neu2buntu on 2009-04-10
paste the output of these commands from the terminal ```
aplay -l && arecord -l
``` ```
lspci -vvv
``` ```
lsmod
``` this should give a better insight as to what is going on here.

---

### Post by markbuntu on 2009-04-10
The best thing to do would be to remove alsa and reinstall it. The same thing happened to me when I switched mobos and this fixed it.

(1) Remove the ALSA packages

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall the same packages

sudo apt-get install linux-sound-base alsa-base alsa-utils

Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:

sudo apt-get install gdm ubuntu-desktop

If you are using xubuntu this will also happen to you

sudo apt-get install gdm xubuntu-desktop

(3) Reboot.

---

### Post by neu2buntu on 2009-04-10
markbuntu,s idea seems a lot simpler than my method!!!!  have to say a big up for markbuntu on your post [[COLOR=Red]here[COLOR=Black] [/COLOR][/COLOR]]("http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack").this has got my sound working perfect with jack and pulseaudio for everything audio....thanks!!!!:guitar:

---

### Post by markbuntu on 2009-04-10
> **neu2buntu said:**
> markbuntu,s idea seems a lot simpler than my method!!!!  have to say a big up for markbuntu on your post [[COLOR=Red]here[COLOR=Black] [/COLOR][/COLOR]]("http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack").this has got my sound working perfect with jack and pulseaudio for everything audio....thanks!!!!:guitar:

Are you running ubuntustudio/jack on your aspire one?
I have an aspire one and am thinking of making it a portable ubuntustudio after jaunty release.

---

### Post by neu2buntu on 2009-04-10
oh yes and it runs very smooth, other than the odd vst crashing lmms ardour and rosegarden. when an app crashes i need to reload pulseaudio (as in your tut) .. but it is definately a good notepad for ubuntu-studio..... i also upgraded the ram to 1.5gb(this is the max capable) myself.... ram cost £12 on ebay. .. i have uploaded a few basic demos on youtube some done on the aa1 ,so you could always look at them...... the url is on my profile(i think)

---

### Post by markbuntu on 2009-04-10
Ok, thanks. I will give it a try. 

Sorry to highjack your post pearlygate do you need anymore help?

---

### Post by neu2buntu on 2009-04-10
:lolflag::lolflag:yeah we kind of hijacked the post...:lolflag::lolflag:

the only  2 things i cant do an the acer that i can do on 
my "advent k4000-laptop"  it boot the realtime kernel and boot backtrack!!! hmmm and i also flashed the bios to the latest version(as a result of a usb error had to this,had the black screen of death on bootup after doing a "cat" on my pendrive!?!) , although i have added the script to the "security" for realtime audio pref,i still think i need the rt-kernel though!!! , think this might be down to the bios only allocating 8mb vid ram at boot time(not changable) im not sure.......will post this 1 up if i cant find the answers!!!

[COLOR=Lime]once again sorry for "hijacking" the post,but we will help with the audio problem(god i cant imagine my lappy withoput sound)):P[/COLOR]

---

### Post by markbuntu on 2009-04-10
Let's move this to one of my threads

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Or we should start a new one "ubuntustudio on aspire one" or something in the multimedia production forum.

---

### Post by neu2buntu on 2009-04-10
:lolflag:im not sure hmmmm probably a new thread would be better.
 you can kick start it (im the noob here ,remember!!!...lol) maybe a title "acer aspire one audio-studio" or something to that effect.... 
                      there are a lot of aa1 users and im sure they would be interested to make the most of their "netbooks"...   i know i push mine to the limit,but it hasnt went cold turkey yet (switched off through overheating or something)  anyway how long have you been using ubuntu(linux) for markbuntu? you do really know your stuff,especially audio!!! i found ubuntu after being infected by ms viruses that even attacked the bios or bootloader(not sure), but will not be going back... would like to solve the rt-kernel prob though as i think 1.5gb is enough to run it???   ....ooooppppsss sorry for ranting .,im on the alcohol tonight...:lolflag::redface:

---

### Post by neu2buntu on 2009-04-10
[COLOR=Red]r[COLOR=Orange]i[COLOR=Yellow]g[COLOR=Lime]g[COLOR=Cyan]h[COLOR=DeepSkyBlue]t [COLOR=DarkOrchid]n[COLOR=Red]o [COLOR=Orange]m[COLOR=Yellow]o[COLOR=Lime]r[COLOR=Cyan]e[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR] [COLOR=Purple]post [COLOR=Red]stealing!!! [COLOR=Lime]anyway ,to the original poster ,.... let us know how you get on with your audio!!! [COLOR=Purple]we are here to help!!![/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by Valley Star Techs on 2009-04-10
This is what I was looking for. Thanks

---

### Post by neu2buntu on 2009-04-10
> **Re: how to reinstall audio driver?**             
                                                                This is what I was looking for. Thanks
                                                                                               __________________
                [http://www.valleystartechs.com]("http://www.valleystartechs.com/")what were you looking for? ... was it about the acer aspire 1 ? or about reinstalling your audio driver?.... this post has kind of lost it:lolflag::lolflag::lolflag::lolflag:


or was it about spamming your site(this will not be looked upon kindly)...hope not!!!!

---

### Post by pearlygate on 2009-04-12
> **neu2buntu said:**
> paste the output of these commands from the terminal ```
aplay -l && arecord -l
``` ```
lspci -vvv
``` ```
lsmod
``` this should give a better insight as to what is going on here.

Hi neu, thanks for your response. This is the output of 
aplay -l && arecord -l

```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: U0x46d0x8ad [USB Device 0x46d:0x8ad], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -vvv

```

00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
	Subsystem: ASUSTeK Computer Inc. Device 8353
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: ati-agp

00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f8000000-fbefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: 00000000f6f00000-00000000f6ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: I/O ports at c000 [size=8]
	Region 1: I/O ports at b000 [size=4]
	Region 2: I/O ports at a000 [size=8]
	Region 3: I/O ports at 9000 [size=4]
	Region 4: I/O ports at 8000 [size=16]
	Region 5: Memory at f7fff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f7ffe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f7ffd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at f7fff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f7ffc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f7ffb000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at f7ffa800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort+ <MAbort- >SERR+ <PERR+ INTx-
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at ff00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 8345
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at f7ff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: fff00000-000fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at f7ff9000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

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

01:00.0 VGA compatible controller: nVidia Corporation Device 05e2 (rev a1)
	Subsystem: eVga.com. Corp. Device 1257
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at fbe80000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 82c6
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 221
	Region 0: I/O ports at e800 [size=256]
	Region 2: Memory at fbfff000 (64-bit, non-prefetchable) [size=4K]
	Region 4: Memory at f6ff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fbfc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169


```

this is lsmod

```

Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18944  1 
fat                    57376  1 vfat
ipv6                  263972  14 
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44560  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15748  0 
powernow_k8            22148  1 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
video                  25232  0 
output                 11008  1 video
pci_slot               12680  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
ieee1394               96324  1 sbp2
lp                     17156  0 
snd_usb_audio          89728  1 
snd_usb_lib            24192  1 snd_usb_audio
snd_hwdep              15236  1 snd_usb_audio
usb_storage            82624  1 
snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
evdev                  17696  6 
snd_seq_dummy          10884  0 
pcspkr                 10624  0 
k8temp                 12416  0 
libusual               30356  1 usb_storage
usblp                  20480  0 
snd_seq_oss            38528  0 
usbhid                 35840  0 
gspca_zc3xx            55936  0 
hid                    50560  1 usbhid
gspca_main             29312  1 gspca_zc3xx
videodev               41344  1 gspca_main
snd_seq_midi           14336  0 
v4l1_compat            22404  1 videodev
nvidia               6909268  38 
parport_pc             39332  1 
snd_rawmidi            29824  2 snd_usb_lib,snd_seq_midi
parport                42604  3 ppdev,lp,parport_pc
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  19 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              16144  0 
wmi                    14504  0 
button                 14224  0 
soundcore              15328  1 snd
i2c_core               31892  2 nvidia,i2c_piix4
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ati_agp                14988  0 
agpgart                42184  2 nvidia,ati_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  5 
crc_t10dif              9984  1 sd_mod
pata_atiixp            12800  0 
pata_acpi              12160  0 
sg                     39732  0 
ata_generic            12932  0 
ehci_hcd               43788  0 
ohci_hcd               32016  0 
usbcore               149488  11 snd_usb_audio,snd_usb_lib,usb_storage,libusual,usblp,usbhid,gspca_zc3xx,gspca_main,ehci_hcd,ohci_hcd
ahci                   37132  2 
r8169                  36100  0 
mii                    13440  1 r8169
libata                178208  4 pata_atiixp,pata_acpi,ata_generic,ahci
scsi_mod              155212  6 sbp2,usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

> **markbuntu said:**
> The best thing to do would be to remove alsa and reinstall it. The same thing happened to me when I switched mobos and this fixed it.

(1) Remove the ALSA packages

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall the same packages

sudo apt-get install linux-sound-base alsa-base alsa-utils

Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:

sudo apt-get install gdm ubuntu-desktop

If you are using xubuntu this will also happen to you

sudo apt-get install gdm xubuntu-desktop

(3) Reboot.

Hi Mark, I tried your method but it did not work. Though after doing all that, my automatic login (where I don't have to fill in my username/password) now become manual. Is there a way to reset it back to what it was.

Thanks for your help guys.

---

### Post by neu2buntu on 2009-04-12
its possible you might have to edit this file **/etc/modprobe.d/alsa-base** and change or add to the "options" follow this post [COLOR=Red]**[here]("http://ubuntuforums.org/showthread.php?t=616845") **[/COLOR][COLOR=Black]for how to do this[/COLOR]... i have had to do this to bring in headphone support ,but it seems a lot of people have solved no sound by doing this!!!!  i also see that you have a usb soundcard but it looks like it is only capable of recording...am i right?   also another thing to note when looking at the "alsa-base" -is index=   for the soundcard driver as priority works like index=0 is higher priority than index=1.  

   so say for example if it is your usb soundcard driver is index=0 but you want the internal soundcard to be top priority you will have to swap the values here...):P):P

---

### Post by markbuntu on 2009-04-12
> **pearlygate said:**
> Hi neu, thanks for your response. This is the output of 
aplay -l && arecord -l

```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: U0x46d0x8ad [USB Device 0x46d:0x8ad], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -vvv

```

00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
	Subsystem: ASUSTeK Computer Inc. Device 8353
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: ati-agp

00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f8000000-fbefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: 00000000f6f00000-00000000f6ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: I/O ports at c000 [size=8]
	Region 1: I/O ports at b000 [size=4]
	Region 2: I/O ports at a000 [size=8]
	Region 3: I/O ports at 9000 [size=4]
	Region 4: I/O ports at 8000 [size=16]
	Region 5: Memory at f7fff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f7ffe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f7ffd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at f7fff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f7ffc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f7ffb000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at f7ffa800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort+ <MAbort- >SERR+ <PERR+ INTx-
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at ff00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 8345
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at f7ff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: fff00000-000fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at f7ff9000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

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

01:00.0 VGA compatible controller: nVidia Corporation Device 05e2 (rev a1)
	Subsystem: eVga.com. Corp. Device 1257
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at fbe80000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 82c6
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 221
	Region 0: I/O ports at e800 [size=256]
	Region 2: Memory at fbfff000 (64-bit, non-prefetchable) [size=4K]
	Region 4: Memory at f6ff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fbfc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169


```

this is lsmod

```

Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18944  1 
fat                    57376  1 vfat
ipv6                  263972  14 
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44560  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15748  0 
powernow_k8            22148  1 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
video                  25232  0 
output                 11008  1 video
pci_slot               12680  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
ieee1394               96324  1 sbp2
lp                     17156  0 
snd_usb_audio          89728  1 
snd_usb_lib            24192  1 snd_usb_audio
snd_hwdep              15236  1 snd_usb_audio
usb_storage            82624  1 
snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
evdev                  17696  6 
snd_seq_dummy          10884  0 
pcspkr                 10624  0 
k8temp                 12416  0 
libusual               30356  1 usb_storage
usblp                  20480  0 
snd_seq_oss            38528  0 
usbhid                 35840  0 
gspca_zc3xx            55936  0 
hid                    50560  1 usbhid
gspca_main             29312  1 gspca_zc3xx
videodev               41344  1 gspca_main
snd_seq_midi           14336  0 
v4l1_compat            22404  1 videodev
nvidia               6909268  38 
parport_pc             39332  1 
snd_rawmidi            29824  2 snd_usb_lib,snd_seq_midi
parport                42604  3 ppdev,lp,parport_pc
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  19 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              16144  0 
wmi                    14504  0 
button                 14224  0 
soundcore              15328  1 snd
i2c_core               31892  2 nvidia,i2c_piix4
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ati_agp                14988  0 
agpgart                42184  2 nvidia,ati_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  5 
crc_t10dif              9984  1 sd_mod
pata_atiixp            12800  0 
pata_acpi              12160  0 
sg                     39732  0 
ata_generic            12932  0 
ehci_hcd               43788  0 
ohci_hcd               32016  0 
usbcore               149488  11 snd_usb_audio,snd_usb_lib,usb_storage,libusual,usblp,usbhid,gspca_zc3xx,gspca_main,ehci_hcd,ohci_hcd
ahci                   37132  2 
r8169                  36100  0 
mii                    13440  1 r8169
libata                178208  4 pata_atiixp,pata_acpi,ata_generic,ahci
scsi_mod              155212  6 sbp2,usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```



Hi Mark, I tried your method but it did not work. Though after doing all that, my automatic login (where I don't have to fill in my username/password) now become manual. Is there a way to reset it back to what it was.



Thanks for your help guys.

GDM was reinstalled so you need to go back into System/Administration/Login to change that back. btw I think automatic login is a really really bad idea. I had autologin set and then had an x server problem that was just a nightmare to fix without having change session/gnome safe mode available in the login screen. timed login is definitely worth the extra 10 seconds.

It looks like you sound card is recognized and the proper driver loaded. You can go here for basic to extreme troubleshooting help.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

