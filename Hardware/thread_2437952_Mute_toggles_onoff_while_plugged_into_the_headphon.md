---
title: "Mute toggles on/off while plugged into the headphone/speaker jack (19.04+)"
date: 2020-03-03
forum: Hardware
---

### Post by ktaherig on 2020-03-03
I'm on an HP Pavilion dv9000 ([https://www.cnet.com/products/hp-pavilion-dv9000/specs/](https://www.cnet.com/products/hp-pavilion-dv9000/specs/)) built many years ago. 


Whenever I'm using any distro that's based on Ubuntu which was published from Version 19.04 onwards, I've been having a major issue with the mute button toggling on and off whenever I have something plugged into the audio out jack. I know that it's not the fault of XFCE, because I also use the latest version of Manjaro with XFCE on this same computer, and it works fine. I also know it's not any Red Hat-based distro, because I use Stella (which is a remix of CentOS 6) also on this exact same computer, and it also works fine. Qubes, Mageia, and Fedora 31 also work perfectly fine and don't have this issue.


I've uploaded a short video of the problem that I recorded with my phone here:
[https://www.youtube.com/watch?v=GXaHXQA-5uQ](https://www.youtube.com/watch?v=GXaHXQA-5uQ)


The problem appears with Kali 2019 and 2020, Peppermint 19.04, Lubuntu 19.04, Xubuntu 19.04, and Sparky 5.10 and 2020.02.


I've checked pretty much everything I can think of. There's a log for my ALSA help diagnostics results on my current computer (which works properly with 18.04) at:
[http://alsa-project.org/db/?f=4859b85cd7fc32e7f01f8df63591b5a43dbf6829](http://alsa-project.org/db/?f=4859b85cd7fc32e7f01f8df63591b5a43dbf6829)


the result output of *lspci* is:
```
00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: NVIDIA Corporation MCP51 PMU (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev f1)
00:0f.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4311 802.11b/g WLAN (rev 01)
05:00.0 VGA compatible controller: NVIDIA Corporation G73M [GeForce Go 7600] (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

and my output for *arecord -l* is:
```
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CX20549 Analog [CX20549 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I've tried reinstalling both PulseAudio and ALSA Mixer, and nothing works. I'm completely lost for ideas. What can I do to solve the problem? Can anybody please help?

---

### Post by Yellow Pasque on 2020-03-04
Try disabling Auto-Mute in alsamixer. Does the problem still occur?

---

### Post by ktaherig on 2020-03-09
Unfortunately, no, that didn't solve matters. I went into Alsa-Mixer and turned that off (why it's set to On as the default, I have no idea, but I tried), and it still causes the muting-on-and-off toggle to persist while I have something plugged into the Line-Out jack.

---

### Post by leespa on 2020-03-23
+1 also seeing same issue on multiple machines...very annoying. Headphone jack muted whenever unplugged/plug new device in and also on a shutdown.

I have Alsamixer open with Auto-mute Disabled...unplug, replug the headphone jack and it mutes itself.

---

