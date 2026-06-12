---
title: "No sound All-in-Wonder HD HDMI"
date: 2010-02-27
forum: Hardware
---

### Post by jweaver28 on 2010-02-27
I dual boot a HTPC system with an EVGA/NVidia MB (630i) with on-board HDMI. I like Ubuntu a lot, and appreciate its security, but sound problems have long prevented me from using it more, so I feel like a Noob and am posting in this forum.

I was unable to get sound under Intrepid if I used the HDMI output on the MB to connected to my TV/monitor, although this cabling worked well under the Vista boot. Liking Ubuntu, I used a DVI cord and a separate sound cord and an Hauppauge TV tuner for a year. However, that stopped working after a Vista upgrade (and it always had been awkward to view TV in Ubuntu), so I switched to an ATI All-in-Wonder HD. This tuner and video card combo connects to the MB with a PCIE interface and also has a 512 mb video capability via its own HDMI port. Once again, this cabling works great under Vista. However, again since I now have to use HDMI to view TV, no sound in Ubuntu (now Karmic). 

Over the past months, I tried many suggested solutions, including the Comprehensive Sound Guide at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449), but no luck. Although the link to Alsa supported cards in that post is now incorrect, I did google alsa supported hardware and found the card uses hda-intel architecture. But reinstalling the drivers from alsa-project still doesn't work. I'm following its suggestion to then post in the forums.

In terminal, asound still shows no devices, aplay shows the output below, and the system hangs if I try to call up System/Preferences/Sound. I noticed that a bug report has been filed concerning this card, but that poster was at least able to get half his sound working, whereas I have no sound at all in Ubuntu Karmic 9.10.


Thanks for any help you can offer.

J.

FYI: 
j@ubuntu:~$ aplay
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:7:0:Unexpected end of file
ALSA lib conf.c:2850:(snd_config_hook_load) /home/j/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
aplay: main:608: audio open error: Invalid argument

j@ubuntu:~$ /usr/bin/canberra-gtk-play --id="desktop-login"
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:7:0:Unexpected end of file
ALSA lib conf.c:2850:(snd_config_hook_load) /home/j/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
Failed to play sound: Invalid argument

j@ubuntu:~$ sudo alsa force-reload 
[sudo] password for j: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/j/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/j/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-hda-codec snd-hwdep snd-rawmidi snd-pcm-oss snd-mixer-oss snd-seq-midi-event snd-pcm snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-hda-codec snd-hwdep snd-rawmidi snd-pcm-oss snd-mixer-oss snd-seq-midi-event snd-pcm snd-seq snd-timer snd-seq-device snd-page-alloc.
j@ubuntu:~$ aplay -l
aplay: device_list:223: no soundcards found...
j@ubuntu:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
	Subsystem: nVidia Corporation Device cb73
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
	Subsystem: nVidia Corporation Device cb73
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
	Subsystem: nVidia Corporation Device cb73
	Flags: bus master, 66MHz, fast devsel, latency 0

00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at ff00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c80 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:03.3 Co-processor: nVidia Corporation MCP73 Co-processor (rev a2)
	Subsystem: nVidia Corporation Device cb73
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
	Memory at eff00000 (32-bit, non-prefetchable) [size=512K]

00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1) (prog-if 10)
	Subsystem: nVidia Corporation Device cb73
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at effff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1) (prog-if 20)
	Subsystem: nVidia Corporation Device cb73
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at efffe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: nVidia Corporation Device cb73
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
	Subsystem: nVidia Corporation MCP73 High Definition Audio
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at efff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: ef800000-ef8fffff
	Prefetchable memory behind bridge: efe00000-efefffff
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: efd00000-efdfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: efc00000-efcfffff
	Prefetchable memory behind bridge: 00000000efb00000-00000000efbfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: efa00000-efafffff
	Prefetchable memory behind bridge: 00000000ef900000-00000000ef9fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Device cb73
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 27
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at f700 [size=16]
	Memory at efffc000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at ef8ff000 (32-bit, non-prefetchable) [size=2K]
	Memory at ef8f8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series
	Subsystem: ATI Technologies Inc Device b383
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at efde0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at ef00 [size=256]
	[virtual] Expansion ROM at efd00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

02:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
	Subsystem: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at efdfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)
	Subsystem: Marvell Technology Group Ltd. Device 00ba
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at efcfc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at df00 [size=256]
	[virtual] Expansion ROM at efb00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

j@ubuntu:~$ sudo modprobe snd-
FATAL: Module snd_ not found.

---

### Post by gordintoronto on 2010-02-27
Posting the verbose version of lspci is more likely to put people off instead of being useful.

Do you have pulseaudio on your system? Since I removed it from mine, I have had no sound problems.

By the way, the Sound Guide you picked hasn't been updated for three years. There are better guides, try Google.

---

### Post by jweaver28 on 2010-03-02
Thanks for the info about verbose inclusions, gordintoronto, but I was hoping to jumpstart a solution. Frankly, I'm not sure how to include a less inclusive response (or put it in the little box as some people managed to do on [http://ubuntuforums.org/showthread.php?t=1312624&highlight=aplay&page=5](http://ubuntuforums.org/showthread.php?t=1312624&highlight=aplay&page=5)). It seemed that sound problems are so common in karmic and the respondents invariably ask for lspci. As a newbie, I'm not really sure why the sound card shows in some ways but not others. With Hardy and Intrepid (the latter on this very machine), at least I had a sound icon, too.

FYI, over the past months, I tried solutions from that admittedly old thread (which has now exceeded 175 pages!) and many similar ones, to no effect. Among the failed solutions was uninstalling pulseaudio, as well as reinstalling it per the link above from 2 weeks ago. As you probably know, pulseaudio is integrated into Karmic, unlike Jaunty, and uninstalling it (in addition to not solving my problem) also messes up other apps.

---

### Post by gordintoronto on 2010-03-03
I run Jaunty on "my" computer.  While my wife was on an extended trip to China, I replaced the hard drive on her computer and installed Karmic.  It worked fine, (with pulseaudio) within the limitations of the (slow) box. She has returned, so I no longer have Karmic available other than a LiveCD.

A simple "lspci" command with no parameters produces one-line-per-device output.  I didn't realize there are two sound devices on your computer until I went through the detail just now. Does Preferences/Sound show two devices? Can you select the ATI one? (Perhaps there is a BIOS setting to disable the nVidia one.)

I think you can make the little box by starting with (open square-bracket)code(close square-bracket) and ending with (open square-bracket)/code(close square-bracket).

---

### Post by jweaver28 on 2010-03-05
Thanks, Gordintoronto. Unfortunately, preferences/sound produces only a waiting message, probably because aplay lists no devices. It's frustrating, because even without the new ATI all-in-wonder card, I couldn't get sound if I used an HDMI connection, only a direct cable from the sound port, and another VGA/VGA.

---

