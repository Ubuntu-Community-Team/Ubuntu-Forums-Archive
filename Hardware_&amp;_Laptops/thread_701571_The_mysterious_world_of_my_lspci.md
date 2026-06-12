---
title: "The mysterious world of my lspci"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by theinnercityhippy on 2008-02-19
Hello,

i posted a different thread earlier about getting my audio and hotkeys working but realised that I may have a bigger problem which would solve the lot. In short, when I view my lspci output (see below) I get a lot of unknown devices with anything related to Nvidia (I have clicked on the enable restricted drivers tab to get this to work) and I think this is all connected to not having the right drivers for my motherboard installed.

Is this normal or has anyone any idea how I can get this issue resolved? I have a HP Pavilion DV9605ea and whilst Ubuntu seems to work OK I'm hoping I can get better performance and sound quality if I can find the correct drivers,

Thanks again lovely people

jimdog@jimdogsbrain:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
jimdog@jimdogsbrain:~$

---

### Post by kidders on 2008-02-20
Hi there,

Lspci not recognising a device isn't a symptom of anything.

Lspci works by reading your PCI devices' vendor & product codes (two 4-digit hexadecimal numbers), and matching them against a database of friendlier names for the sake of readability. Nothing about its output implies anything about the presence/absence of suitable drivers, whether they're in use, whether your hardware is even working, and so on.

If lines like "Unknown device 0547" bother you, you could try updating your PCI ID database (**sudo update-pciids**) ... the latest version (assuming you don't already have it) may contain some or all of the English labels missing from your current one.

Just in case you're interested, running **sudo lspci -n** will show you the vendor/product codes, instead of the English names. "10de", for instance, means "Nvidia".

If you'd like to find out what drivers are in use, **lsmod** is a good place to start. Looking at the appropriate place in /sys/bus/pci/devices can give you more detailed information about what's driving the various bits of hardware lspci doesn't recognise.

---

### Post by theinnercityhippy on 2008-02-20
Thanks

Hangover from my windows days I think that if it says something is unknown I panic :-)

Read somewhere something about changing the bios settings for the pci bus latency from 32 to 64 in order to get the machine to recognise it (its an nVidia nforce MCP67 i think) but didn't want to try this without knowing what I'm doing. Any ideas what this might be referring to? I'll try and remember where the thread was and post the link.

---

### Post by dannyboy79 on 2008-02-20
> **theinnercityhippy said:**
> Thanks

Hangover from my windows days I think that if it says something is unknown I panic :-)

Read somewhere something about changing the bios settings for the pci bus latency from 32 to 64 in order to get the machine to recognise it (its an nVidia nforce MCP67 i think) but didn't want to try this without knowing what I'm doing. Any ideas what this might be referring to? I'll try and remember where the thread was and post the link.

you would want to add this line to your /etc/rc.local file. you'll need to know which pci bus you want to change to 64. according to all over the web, the hex value for 64 is 40. I have set my ide and sata controllers to latency of 176 using the following within rc.local (it's a mythtv thing due to the capture card)

setpci -v -s 00:0f.0 latency_timer=b0
setpci -v -s 00:0f.1 latency_timer=b0


example: looking at your lspci output if you wanted to change your ide controller pci latency you would put this

setpci -v -s 00:06.0 latency_timer=40

---

### Post by Yellow Pasque on 2008-02-20
Huh? What are you trying to get it to recognize? Did the update-pciids not work for you?

OH, your audio. It's a high-def audio chip, probably too new for ALSA 1.0.14 (version included with Gutsy) to recognize properly. Try this to update your ALSA version:
[http://ubuntuforums.org/showthread.php?t=700614](http://ubuntuforums.org/showthread.php?t=700614)

---

### Post by theinnercityhippy on 2008-02-20
OK did the sudo update-pciids and got the following so I'm halfway there. still not got a name for the pci bridge and a few others yet but it's a definite improvement. looking into tem's thread now:

jimdog@jimdogsbrain:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
jimdog@jimdogsbrain:~$

---

