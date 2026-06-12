---
title: "Dual Video Card Problems Ubuntu 12.10"
date: 2012-11-18
forum: Hardware
---

### Post by power.supply on 2012-11-18
Hey everyone,

I am trying to get a dual monitor set up working on my Dell Precision workstation using two monitors. Display settings doesn't recognise that I have a second monitor plugged in and doesn't give me an option to create a dual display. I've tryed the nvidia proprietry driver but it fails to load the desktop properly after installing it and still doesn't switch on my second screen.

lspci gives me this
```
aaron@precision-WorkStation-T3500:~$ sudo lspci
[sudo] password for aaron: 
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:14.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode]
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
02:00.0 VGA compatible controller: NVIDIA Corporation G96 [Quadro FX 580] (rev a1)
03:00.0 VGA compatible controller: NVIDIA Corporation G96 [Quadro FX 580] (rev a1)
05:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe (rev 10)
ff:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
ff:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
ff:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
ff:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
ff:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
ff:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
ff:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
ff:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
ff:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
ff:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
ff:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
ff:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
ff:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
ff:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
ff:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
ff:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)

```
So I know the system recognises the second video card.

Looking through the kernal log it gives me this:
```
aaron@precision-WorkStation-T3500:~$ sudo dmesg |grep drm
[   12.936899] [drm] Initialized drm 1.1.0 20060810
[   12.958314] [drm] nouveau 0000:02:00.0: Detected an NV50 generation card (0x096c80c1)
[   12.960787] [drm] nouveau 0000:02:00.0: Checking PRAMIN for VBIOS
[   13.040281] [drm] nouveau 0000:02:00.0: ... appears to be valid
[   13.040283] [drm] nouveau 0000:02:00.0: Using VBIOS from PRAMIN
[   13.040286] [drm] nouveau 0000:02:00.0: BIT BIOS found
[   13.040288] [drm] nouveau 0000:02:00.0: Bios version 62.94.63.00
[   13.040290] [drm] nouveau 0000:02:00.0: TMDS table version 2.0
[   13.043329] [drm] nouveau 0000:02:00.0: MXM: no VBIOS data, nothing to do
[   13.043332] [drm] nouveau 0000:02:00.0: DCB version 4.0
[   13.043334] [drm] nouveau 0000:02:00.0: DCB outp 00: 02000300 00000028
[   13.043336] [drm] nouveau 0000:02:00.0: DCB outp 01: 01000302 00020030
[   13.043337] [drm] nouveau 0000:02:00.0: DCB outp 02: 02021396 0f200020
[   13.043339] [drm] nouveau 0000:02:00.0: DCB outp 03: 02021332 00020020
[   13.043340] [drm] nouveau 0000:02:00.0: DCB outp 04: 040323b6 0f200020
[   13.043341] [drm] nouveau 0000:02:00.0: DCB outp 05: 04032342 00020020
[   13.043342] [drm] nouveau 0000:02:00.0: DCB conn 00: 00001030
[   13.043344] [drm] nouveau 0000:02:00.0: DCB conn 01: 0000a146
[   13.043345] [drm] nouveau 0000:02:00.0: DCB conn 02: 00050246
[   13.043349] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 0 at offset 0xD6A9
[   13.068471] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 1 at offset 0xDB26
[   13.071974] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 2 at offset 0xEAEF
[   13.071982] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 3 at offset 0xEC10
[   13.073057] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 4 at offset 0xEE8D
[   13.073059] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table at offset 0xEEF2
[   13.092878] [drm] nouveau 0000:02:00.0: 0xEEF2: Condition still not met after 20ms, skipping following opcodes
[   13.108100] [drm] nouveau 0000:02:00.0: Detected 512MiB VRAM (GDDR3)
[   13.108745] [drm] nouveau 0000:02:00.0: 512 MiB GART (aperture)
[   13.173476] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.173479] [drm] No driver support for vblank timestamp query.
[   13.208659] [drm] nouveau 0000:02:00.0: Detected monitoring device: adt7473
[   13.208767] [drm] nouveau 0000:02:00.0: 2 available performance level(s)
[   13.208771] [drm] nouveau 0000:02:00.0: 0: core 208MHz shader 416MHz memory 100MHz voltage 1000mV fanspeed 100%
[   13.208773] [drm] nouveau 0000:02:00.0: 3: core 450MHz shader 1125MHz memory 800MHz voltage 1100mV fanspeed 100%
[   13.208776] [drm] nouveau 0000:02:00.0: c: core 400MHz shader 800MHz memory 799MHz voltage 1000mV fanspeed 40%
[   13.253545] [drm] nouveau 0000:02:00.0: MM: using CRYPT for buffer copies
[   13.460183] [drm] nouveau 0000:02:00.0: allocated 1600x1200 fb: 0x2c0000, bo ffff8800688bc800
[   13.461029] drm: registered panic notifier
[   13.461053] [drm] Initialized nouveau 1.0.0 20120316 for 0000:02:00.0 on minor 0
[   13.461567] [drm] nouveau 0000:03:00.0: Detected an NV50 generation card (0x096c80c1)
[   13.463973] [drm] nouveau 0000:03:00.0: Checking PRAMIN for VBIOS
[   13.463979] [drm] nouveau 0000:03:00.0: ... BIOS signature not found
[   13.463980] [drm] nouveau 0000:03:00.0: Checking PROM for VBIOS
[   13.636889] [drm] nouveau 0000:03:00.0: ... appears to be valid
[   13.636891] [drm] nouveau 0000:03:00.0: Using VBIOS from PROM
[   13.636893] [drm] nouveau 0000:03:00.0: BIT BIOS found
[   13.636895] [drm] nouveau 0000:03:00.0: Bios version 62.94.63.00
[   13.636898] [drm] nouveau 0000:03:00.0: TMDS table version 2.0
[   13.654523] [drm] nouveau 0000:03:00.0: MXM: no VBIOS data, nothing to do
[   13.654527] [drm] nouveau 0000:03:00.0: DCB version 4.0
[   13.654530] [drm] nouveau 0000:03:00.0: DCB outp 00: 02000300 00000028
[   13.654531] [drm] nouveau 0000:03:00.0: DCB outp 01: 01000302 00020030
[   13.654533] [drm] nouveau 0000:03:00.0: DCB outp 02: 02021396 0f200020
[   13.654534] [drm] nouveau 0000:03:00.0: DCB outp 03: 02021332 00020020
[   13.654535] [drm] nouveau 0000:03:00.0: DCB outp 04: 040323b6 0f200020
[   13.654536] [drm] nouveau 0000:03:00.0: DCB outp 05: 04032342 00020020
[   13.654538] [drm] nouveau 0000:03:00.0: DCB conn 00: 00001030
[   13.654540] [drm] nouveau 0000:03:00.0: DCB conn 01: 0000a146
[   13.654541] [drm] nouveau 0000:03:00.0: DCB conn 02: 00050246
[   13.654547] [drm] nouveau 0000:03:00.0: Adaptor not initialised, running VBIOS init tables.
[   13.654549] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 0 at offset 0xD6A9
[   13.707992] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 1 at offset 0xDB26
[   13.764309] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 2 at offset 0xEAEF
[   13.764349] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 3 at offset 0xEC10
[   13.766105] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 4 at offset 0xEE8D
[   13.766106] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table at offset 0xEEF2
[   13.792904] [drm] nouveau 0000:03:00.0: Detected 512MiB VRAM (GDDR3)
[   13.793542] [drm] nouveau 0000:03:00.0: 512 MiB GART (aperture)
[   13.847267] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.847271] [drm] No driver support for vblank timestamp query.
[   13.881872] [drm] nouveau 0000:03:00.0: Detected monitoring device: adt7473
[   13.882006] [drm] nouveau 0000:03:00.0: 2 available performance level(s)
[   13.882009] [drm] nouveau 0000:03:00.0: 0: core 208MHz shader 416MHz memory 100MHz voltage 1000mV fanspeed 100%
[   13.882012] [drm] nouveau 0000:03:00.0: 3: core 450MHz shader 1125MHz memory 800MHz voltage 1100mV fanspeed 100%
[   13.882014] [drm] nouveau 0000:03:00.0: c: core 400MHz shader 800MHz memory 799MHz voltage 1000mV fanspeed 40%
[   13.993916] [drm] nouveau 0000:03:00.0: MM: using CRYPT for buffer copies
[   14.205828] [drm] nouveau 0000:03:00.0: allocated 1600x1200 fb: 0x2c0000, bo ffff880068aa9800
[   14.205943] [drm] Initialized nouveau 1.0.0 20120316 for 0000:03:00.0 on minor 1

```

This line:
```
[   13.654547] [drm] nouveau 0000:03:00.0: Adaptor not initialised, running VBIOS init tables.

```
tells me that the adapto is not initialised. I'm assuming that is what I need to do to get it to work but have no idea how.

Any help would be great.

Thanks,
Aaron.

---

### Post by oldfred on 2012-11-19
I do not have dual displays. But until I installed the Linux headers, I could not get nVidia to install correctly.

I installed nvidia-current-updates and that worked. Some real new video cards may need the experimental version.
       
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot

   May want nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

    Fix for nVidia with 12.10 missing kernel dpkg reconfigure:
[http://ubuntuforums.org/showthread.php?t=2072862](http://ubuntuforums.org/showthread.php?t=2072862)

    
I do not know if this applies to nVidia or not:
       ARandR Screen Layout Editor 0.1.4 - Dual screens
[http://christian.amsuess.com/tools/arandr/](http://christian.amsuess.com/tools/arandr/)

---

### Post by power.supply on 2012-11-19
Thanks for your reply. I'm a little skeptical about using the nvidia driver again after what happened here:

[http://ubuntuforums.org/showthread.php?t=2085472](http://ubuntuforums.org/showthread.php?t=2085472)

Is there another way I could do this? Maybe fiddling with it manually? (like you use to be able to with xorg.conf)

Thanks again.

---

