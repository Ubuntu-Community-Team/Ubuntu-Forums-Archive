---
title: "Cryptic output from lspci"
date: 2016-12-14
forum: Hardware
---

### Post by orthoducks on 2016-12-14
lspci says that my display adapter is an 'NVIDIA Corporation Device 1283 (rev a1) (prog-if 00 [VGA controller])'.

Wow. Who knew?

Does anyone know what a "Device 1283" is in English, or any other known language?

In general, what's the next step when lspci says something this cryptic?

---

### Post by vasa1 on 2016-12-14
> **orthoducks said:**
> ...
In general, what's the next step when lspci says something this cryptic?
Post the entire contents of *lspci* here between code tags and hope someone can help.

---

### Post by orthoducks on 2016-12-15
OK... but I'm puzzled. Most of lspci's output has nothing to do with the display adapter. What relevant information could it contain?
-----```

~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82G35 Express DRAM Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. 82G35 Express DRAM Controller
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82G35 Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fd000000-fe9fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f9ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at b800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at b880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at bc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fcfffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at fcff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: fa000000-fa3fffff
    Prefetchable memory behind bridge: 00000000fbf00000-00000000fbffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fa400000-fa5fffff
    Prefetchable memory behind bridge: 00000000fa600000-00000000fa7fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 00000000fa800000-00000000fa9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at b080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at b400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at b480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fcfff800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
    I/O ports at a000 [size=8]
    I/O ports at 9c00 [size=4]
    I/O ports at 9880 [size=8]
    I/O ports at 9800 [size=4]
    I/O ports at 9480 [size=16]
    I/O ports at 9400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
    Flags: medium devsel, IRQ 5
    Memory at fcfff400 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0400 [size=32]
    Kernel modules: i2c_i801

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. P5K PRO Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
    I/O ports at b000 [size=8]
    I/O ports at ac00 [size=4]
    I/O ports at a880 [size=8]
    I/O ports at a800 [size=4]
    I/O ports at a480 [size=16]
    I/O ports at a400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi

01:00.0 VGA compatible controller: NVIDIA Corporation Device 1283 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device 100b
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at f0000000 (64-bit, prefetchable) [size=128M]
    Memory at f8000000 (64-bit, prefetchable) [size=32M]
    I/O ports at cc00 [size=128]
    [virtual] Expansion ROM at fe000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau

01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)
    Subsystem: NVIDIA Corporation GK208 HDMI/DP Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe9fc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

02:00.0 Ethernet controller: Qualcomm Atheros Attansic L1 Gigabit Ethernet (rev b0)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at feac0000 (64-bit, non-prefetchable) [size=256K]
    Expansion ROM at feaa0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: atl1
    Kernel modules: atl1

03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. JMB368 IDE controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at dc00 [size=8]
    I/O ports at d880 [size=4]
    I/O ports at d800 [size=8]
    I/O ports at d480 [size=4]
    I/O ports at d400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron, pata_acpi

05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Motherboard
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at febff800 (32-bit, non-prefetchable) [size=2K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire_ohci
```

---

### Post by QIII on 2016-12-15
What is the nomenclature of the device you believe is installed?

If it is quite new, it may not be properly identified.

---

### Post by Yellow Pasque on 2016-12-15
```
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1283 (rev a1) (prog-if 00 [VGA controller])
...
01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)
```

It's obviously some sort of Nvidia GPU based on the GK208 core (used in low end GPU's like Geforce GT 720). The ID is 10de:1283, which I don't see in the database. Googling gives the name D15M2-10. *shrug*

```
In general, what's the next step when lspci says something this cryptic? 
```
Run this to update the latest copy of the PCI ID database and then look at lspci again. I don't think it will help in this case though.
```
sudo update-pciids
```

---

### Post by ajgreeny on 2016-12-15
Just my attempt to move this on a bit; do you have a display problem of any sort with the nouveau driver which is what you're using at the moment, and have you looked in Additional Drivers to see if there is any nvidia driver available to use which might be better than the nouveau?

---

### Post by orthoducks on 2016-12-15
QIII: If by "nomenclature" you mean what's printed on the board, there's nothing but "NVIDIA" and various alphanumeric strings that Google didn't find meaningful. It appears to be an NVIDIA board, not just a board with an NVIDIA GPU, but it has no printed identification. I've looked at a lot of NVIDIA boards, and none of them do.

It's likely to be old, but not new. It was headed for the recycler when I rescued it.

I updated pciids a whole 10 minutes before I ran lspci. Updating it again isn't likely to help! :)

AJ: There's no problem at all with the board. The "problem" is with lspci and other diagnostic software in/for Ubuntu: I'm trying to learn to use the tools effectively, and my installed display adapter seemed like a logical place to start.

---

### Post by Yellow Pasque on 2016-12-15
> **orthoducks said:**
> It's likely to be old, but not new. It was headed for the recycler when I rescued it.

If it really is a GK208-based GPU, then it's likely not original to the system since the Asus P5K boards are about 2008, and GK208 products debuted around 2013-2014.
I think the next place I'd look for a clue is the /var/log/Xorg.0.log
Maybe the Video BIOS strings will give more information.

---

### Post by orthoducks on 2016-12-15
I can guarantee that it's not original to the system, because I assembled the "system" from components over the past few weeks. Mobo/CPU/RAM, case/PSU, HDD, DVD, and display adapter probably never met each other until I introduced them.

---

### Post by Yellow Pasque on 2016-12-15
So you found a card, had little idea what it was and stuck it in your system? LOL "It's got a VGA/DVI port(s), so it's probably a video card."
Anyway, did you look at the Xorg log? Please share it (with code tags) if you want further help. Quite honestly, I don't think you're going to get anything more specific than what we've told you.
If you can't tell from looking at list of Geforce 600/700 series, Nvidia loves to play rebadging games with model numbers, especially with their lower end products, to confuse consumers: [https://en.wikipedia.org/wiki/List_of_Nvidia_graphics_processing_units](https://en.wikipedia.org/wiki/List_of_Nvidia_graphics_processing_units)

---

### Post by orthoducks on 2016-12-16
Temujin, I have several display adapters on hand, and I intentionally chose a basic one. Given my objective, which is to learn more about Linux and the supporting hardware, I think it was a good choice. It gave me occasion to ask some questions that you could answer, and I learned something from that. It also gave me occasion to ask some questions that you couldn't answer, and you could learn something from that.

I haven't heard of the xorg log before. I looked it up, but askubuntu.com says it's in ~/.local/share/xorg, and my system has no log file there. This information may be useful in the future, but it doesn't appear to be immediately relevant.

The list of NVIDIA cards you provided will definitely be useful in the future, and I appreciate it. It would be more useful if it had pictures, though. Since I don't have a meaningful model number, I haven't got much information to search for.

I'm going to try other display adapters and see what I can learn. Perhaps I'll have more luck getting assistance if lspci says something cryptic about a higher-end card.

---

### Post by deadflowr on 2016-12-16
Your xorg log can be found in 
```
/var/log/Xorg.0.log
```
It can get pretty fat so you might consider posting it to pastebin, rather than try posting it directly in thread.
See [https://help.ubuntu.com/community/Pastebinit]("https://help.ubuntu.com/community/Pastebinit")
for how to setup for pastebin on Ubuntu.

---

### Post by nothingspecial on 2016-12-16
> **orthoducks said:**
>  There's no problem at all with the board. The "problem" is with lspci and other diagnostic software in/for Ubuntu: I'm trying to learn to use the tools effectively, and my installed display adapter seemed like a logical place to start.

It depends on what sort of user you are.

If you are just and end user then, to diagnose problems with hardware, lspci is a good tool.

If you have a problem you use that utility to discover what linux recognizes your hardware as and you paste it into a search engine.
Hopefully someone else has had the same problem and there is a solution or a workaround.
If you have no luck then you file a bug report.

Then, hopefully, in time, it gets fixed and the next person who has your issue finds the answer with a search engine.

To fix the actual linux drivers yourself is a whole other thing.

---

### Post by Yellow Pasque on 2016-12-17
> **orthoducks said:**
> Temujin, I have several display adapters on hand, and I intentionally chose a basic one. Given my objective, which is to learn more about Linux and the supporting hardware, I think it was a good choice. It gave me occasion to ask some questions that you could answer, and I learned something from that. It also gave me occasion to ask some questions that you couldn't answer, and you could learn something from that.

I realize my previous post may have been perceived as a bit condescending, and I apologize if that's the case. It's not how I meant it. I find it interesting that you have a device that's not formally named in the PCI ID database, and would like to see the Xorg log, so that perhaps we can contribute meaningful information to the PCI ID database to give this device a name. It's like finding a new star in the sky... or something.

> I haven't heard of the xorg log before. I looked it up, but askubuntu.com says it's in ~/.local/share/xorg
It's /var/log/Xorg.0.log, as I pointed out in post #8, and as deadflowr pointed out.

> Since I don't have a meaningful model number, I haven't got much information to search for.
I think "GK208" is about as meaningful as you're going to get at this point given Nvidia's model number games (and they're not the only company guilty of this kind of flimflammery).

---

### Post by orthoducks on 2016-12-19
Temujin, your explanation is accepted, with no hard feelings.

I've posted the log to pastebin (neat tool, I didn't know about it although I've done the equivalent with my own hosted site). The URL is [http://paste.ubuntu.com/23657061/](http://paste.ubuntu.com/23657061/).

"GK208" is pretty uninformative. It's kind of like: What kind of car do you drive? "It's a Ford." But what *kind* of Ford? "A sedan." I hope the log says more, but I'm not very hopeful; I looked in the vicinity of every instance of NVIDIA, and I didn't find anything informative. I gather that Ubuntu tried to load a driver, or something driver-like, that it couldn't find; if I install that, perhaps it will tell me more.

---

### Post by orthoducks on 2017-02-16
I'm back, with a more muscular video card to ask questions about. (I've been *very* busy since I was last here... just not busy with video cards.)

This is a double-width, half-length card with two DVI connectors and two HDMI connectors. It has a fan (!) and an 8-pin power connector. The silkscreening assures me that it was made by NVIDIA, but does not disclose a model number. According to lspci and lshw, it's an NVIDIA GeForce GTX 760.

But all of the 760's that I've seen on the web are full length cards. I think it might be a 750, but the 750's I've seen have one DVI connector, not two.

Here's what lshw says about the card:

```
  *-display               
       description: VGA compatible controller
       product: GK104 [GeForce GTX 760]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
        resources: irq:28 memory:fd000000-fdffffff memory:f0000000-f7ffffff  memory:f8000000-f9ffffff ioport:cc00(size=128) memory:fe000000-fe07ffff
```

I'd  like to get more information, or more comprehensible information; I  really don't know what the last three lines mean. I'd like to know how  much RAM is installed, for example. And I'd like to know what model the  card really is.

I found references to a utility named "NVIDIA  Inspector" that provides a lot more information, in a GUI, no less.  Alas, it only runs under Windows.

---

### Post by efflandt on 2017-02-18
Nvidia manufactures the chips, but not most of the cards (unless a Master series), so they may have different video outputs.

The GTX 750 (and 750 Ti) is a newer card than the other 7xx series and was one of the first ones (along with GTX 970 & 980) to have the new efficient Maxwell chip. The GTX 750's only use 60 watts max (hardware regulated), so they usually do not have an external power connector (since PCI Express slot spec should provide 75 watts). The MSI Twin Frozr Gaming GTX 750 Ti OC that I have has 1-DVI, 1-VGA, and 1-HDMI output.

So it is quite possible that the card you have is correctly identified by lspci as a GTX 760. Earlier cards like a GTX 550 Ti that I have with 2-DVI ports (and 1-miniHDMI) were DVI-I which had both digital and analog pins, so they could do DVI to VGA with a simple adapter or cable, but I do not know if one or both of your DVI ports do that.

Once you install an nvidia driver package (which you can do from Additional Drivers), there is nvidia-smi command which can tell much more about the card (especially with -q), but this is the brief output for a GTX 1060:```
efflandt@msata512-1610:~$ nvidia-smi
Sat Feb 18 18:03:40 2017       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 378.09                 Driver Version: 378.09                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 106...  Off  | 0000:01:00.0      On |                  N/A |
| 28%   27C    P8     8W / 120W |    336MiB /  3012MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0     26226    G   /usr/lib/xorg/Xorg                             193MiB |
|    0     26973    G   /usr/bin/compiz                                141MiB |
+-----------------------------------------------------------------------------+
```For example this one shows 8W being used and 120W cap. If yours shows more than 60W cap it is definitely not a GTX 750 (or Ti). GTX 760 would be capped at 170W. So you can see the efficiency improvement going from GTX 760 to newer GTX 1060 (faster using 50 less watts).

---

### Post by orthoducks on 2017-02-21
efflandt, thank you for pointing out the NVIDIA driver package. Because Ubuntu supports NVIDIA adapters out of the (virtual) box, I didn't know there was a separate driver package, and didn't look for one. That will probably solve my problem completely, since most of the cards I need to test will be from NVIDIA. I'll report back after I've had a chance to experiment with the package.

As a side note, when I said that "the silkscreening assures me that it was made by NVIDIA," I was referring to silkscreening on the circuit board, not the chips. Consequently I think we can rule out the possibility that the card was made by another company using NVIDIA chips. It's very unlikely that another manufacturer would want to put NVIDIA's name on its own product, or that NVIDIA would let it.

---

### Post by orthoducks on 2017-02-22
I opened Additional Drivers. It offered me an X.Org X-server-Nouveau display driver (initially selected) and two different versions of the "NVIDIA binary driver." I selected the one of the NVIDIA drivers that the application described as "tested." It installed the driver, then let me reboot, and when Ubuntu came up again, nvidia-smi was there.

All of this sounds easy, but it had some bothersome aspects. Additional Drivers gave me no clue which driver was the better one for this adapter, or whether either one would even work. The one I selected turned out to work OK, but I don't know whether that's because any NVIDIA driver works at least OK with any NVIDIA card, or because I got insanely lucky.

I wonder what will happen when I insert other NVIDIA adapters in the machine. Will this driver work with all of them, or will I have to install different drivers for different adapters? If this driver works with all adapters (or even with many), will nvidia-smi also work, or will it malfunction if the driver is wrong for the card? If nvidia-smi malfunctions, will it do so obviously or non-obviously? If I need different drivers for different adapters, can I avoid having to install a driver for each adapter I test by grouping adapters into families that use the same driver, and if I can do that, how?

I'm asking all of these questions to give you an idea what kinds of uncertainty I'm dealing with. I don't expect you to answer each one (although I'll be delighted if you do); I hope you can give me some general advice that will help me become familiar with the territory I'm entering.

I'll conclude by reproducing the information that nvidia-smi gave me. Beyond the obvious (this adapter is at least nominally a GTX 760), I'm not sure what is significant. Any comments, hints, etc. are welcome.

I entered nvidia-smi -h and got a list of command line options (which I'll study), but I didn't see anything about how to interpret the output. I found a man page on NVIDIA's developer site, and it has a lot of information about the output, but it seems to be organized so that it's hard to understand unless you already understand it.

I'm particularly puzzled by the value of 0 under "GPU." Is it saying that this card has no GPUs (or that for some reason no GPUs are functioning)? If so, what does that mean?
```
~$ nvidia-smi
Tue Feb 21 22:25:44 2017       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 367.57                 Driver Version: 367.57                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 760     Off  | 0000:01:00.0     N/A |                  N/A |
| 30%   30C    P0    N/A /  N/A |    224MiB /  1997MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0                  Not Supported                                         |
+-----------------------------------------------------------------------------+
```

---

### Post by wildmanne39 on 2017-02-22
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Yellow Pasque on 2017-02-22
> **orthoducks said:**
> All of this sounds easy, but it had some bothersome aspects. Additional Drivers gave me no clue which driver was the better one for this adapter, or whether either one would even work.

It would not offer you drivers not known to work with your GPU.

> I wonder what will happen when I insert other NVIDIA adapters in the machine. Will this driver work with all of them, or will I have to install different drivers for different adapters? If this driver works with all adapters (or even with many), will nvidia-smi also work, or will it malfunction if the driver is wrong for the card? If nvidia-smi malfunctions, will it do so obviously or non-obviously? If I need different drivers for different adapters, can I avoid having to install a driver for each adapter I test by grouping adapters into families that use the same driver, and if I can do that, how?

[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

If you've got the correct driver installed, nvidia-smi should work (assuming you're using an nvidia proprietary driver).

> I'll conclude by reproducing the information that nvidia-smi gave me. Beyond the obvious (this adapter is at least nominally a GTX 760), I'm not sure what is significant. Any comments, hints, etc. are welcome. I'm particularly puzzled by the value of 0 under "GPU." Is it saying that this card has no GPUs (or that for some reason no GPUs are functioning)? If so, what does that mean?

It's a GTX 760 with 2GB of memory. What more are you looking for?
The 0 just means the GPU numbered 0 (computer geeks like to start counting at 0). If you had run nvidia-smi with sudo/root privs, you would actually see the processes belonging to GPU #0 listed.

---

### Post by orthoducks on 2017-02-23
> What more are you looking for?

I'm looking for the things that I don't know I should look for. I'm trying to avoid the too-common habit of assuming that because I don't know much about a subject, there isn't much to know!

It sounds like there are no precious Easter eggs hidden in this tool, though, so I'll let it be. When I find time I'll read through the man page, and when my eyes uncross again I'll probably be a lot better informed.

---

### Post by orthoducks on 2017-03-01
I'm back, with a somewhat different kind of question. Now that I know how to identify video cards, how reliable are the results?

I'm asking because I just tested a card which nvidia-smi calls a Quadro K5000. In case you aren't on intimate terms with the K5000, it's a double-wide card with two DVI outputs and two DisplayPorts, intended for professional modeling, animation, etc. It is selling new for $600 to $850, and used on eBay for $300 to $400.

But this card looks nothing like the pictures of the K5000 I've found. The bracket layout is right, but that's about all. The K5000 is shown as a full length card with a black plastic shell and a turbine-bladed fan near the front end. This card is about 3/4 length, with no shell, and a 9-blade fan that is closer to the back. (If it were as far forward as the ones in the pictures, it would be hanging off the end of the card.)

I thought I might have a K5000 whose shell had been removed, but the fan makes that impossible; this is really a differently designed card.

I have two theories: nvidia-smi could be misidentifying the card, or it could be some kind of prototype. I don't like either theory much. The first one seems inherently unlikely; its only virtue is that it explains the card. The second one demands an answer to the question: Why would anyone produce a prototype card that looks so different from the final product? (And why would a prototype have various machine printed tags with a part number, a ROM version number, "Made in China," and "EMC Certification Pending"?)

I wanted to run a benchmark to see if the card is about as fast as a K5000, but I haven't found a graphics benchmark program for Linux for which results from a genuine K5000 are available.

Comments on any aspect of this are welcome: either of my theories, your own theory, or where to find suitable benchmarking software (and/or benchmark results).

---

### Post by Yellow Pasque on 2017-03-01
> Now that I know how to identify video cards, how reliable are the results?

The PCI ID database is usually accurate, but no one's going to give you a 100% guarantee that it's infallible, and it feels like that's what you're looking for.

> I thought I might have a K5000 whose shell had been removed, but the fan makes that impossible

Why? If someone removed the blower ("shell"), they would have to put another fan on it.

> But this card looks nothing like the pictures of the K5000 I've found.

Not every manufacturer follows the Nvidia reference design, and of course, someone could have put a different cooler on it (maybe the old one was too long or the fan died).

> various machine printed tags with a part number, a ROM version number
Did you try googling them?

> or it could be some kind of prototype.
It's not impossible, but it seems like a significant leap logically.

---

### Post by orthoducks on 2017-03-01
>>Now that I know how to identify video cards, how reliable are the results?
>The PCI ID database is usually accurate, but no one's going to  give you a 100% guarantee that it's infallible, 
>and it feels like that's  what you're looking for.

Not really. I've encountered an anomalous situation, and I'm seeking information about probability that one of its elements is misinformation. I do not see how recognizing the possibility of error, and seeking information about risk, implies a demand for infallability.

 	 		>> I thought I might have a K5000 whose shell had been removed, but the fan makes that impossible 			 		

 	
 
> Why? If someone removed the blower ("shell"), they would have to put another fan on it.

I've already ruled out the "shell removed" theory on other grounds, so it's moot. But since you ask, I thought that because there _is_ a fan on the card, and (although I didn't say so) it doesn't look like it was patched on after assembly. My impression is that a "real" K5000 also has a fan mounted on the board, and the shell could be removed without affecting it, but I can't verify that without finding a "real" K5000 and taking it apart, which isn't likely to happen.

 	 		>> But this card looks nothing like the pictures of the K5000 I've found. 			 		

 	
 
> Not every manufacturer follows the Nvidia reference design, and of  course, someone could have put a different cooler on it (maybe the old  one was too long or the fan died).

The card is an NVIDIA card, with the NVIDIA name printed on the circuit board, not just on the chips. Virtually all of the cards I'm testing are NVIDIA cards, so if I had a question about some other brand of card it would be the exception, and I'd mention it. I'm sorry I didn't make this explicit in my last message, although I mentioned it earlier in the thread.

>Did you try googling them?

No; that might be informative, and I'll try it tonight. I'll post again after I do.

---

### Post by Yellow Pasque on 2017-03-01
EDIT: nvm

---

### Post by orthoducks on 2017-03-05
Temujin, I use many different forums with different conventions. Most of them have a "quote" feature, but they all work differently, with different icons in different places on the toolbar. I do not have time to keep track of them all. Instead I usually follow Internet conventions, which are inelegant but universally understood.

I may liken myself to a trader visiting a multitude of tiny islands in the South Pacific. Rather than try to learn each island's dialect I use pidgin English, which may sound crude but is understood. If some islanders refuse to deal with me because I do not speak as they do, that will not lead me to master their speech. If they make things too difficult for rne, it I will stop visiting that island.

I need to clarify the question I asked earlier. When I asked "how accurate are the results?" I was asking a broader question than "how accurate is the database?" I meant, "How accurate is the program, the data it acquires, and the database it uses, taken as a whole?" The database might be perfectly accurate and still yield incorrect results because the acquired data is not detailed enough, and/or the program makes inferences from it that are misleadingly specific. If the whole not always accurate (thus explaining why this mystery card is nailed as an NVIDIA K5000), the causes of the inaccuracy are of interest, but are secondary to the fact of inaccuracy.

---

