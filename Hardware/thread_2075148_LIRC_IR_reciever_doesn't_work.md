---
title: "LIRC IR reciever doesn't work"
date: 2012-10-23
forum: Hardware
---

### Post by nuk28 on 2012-10-23
I am trying to get the IR receiver built into my HP Pavilion dv6700 working with Banshee. However, no matter what I do I cannot get anything to happen when I press buttons on my external remote. 

I would like to use my remote from our DVD player, where I got a config file from [here]("http://lirc.sourceforge.net/remotes/toshiba/SE-R0047"). If that is not possible, a remote also came with my computer whose config file can be found [here](http://lirc.sourceforge.net/remotes/hp/RC1762302-00).

Using input from [http://ubuntuforums.org/showthread.php?p=9637920]("http://ubuntuforums.org/showthread.php?p=9637920"), [http://ubuntuforums.org/showthread.php?t=643479]("http://ubuntuforums.org/showthread.php?t=643479"), and maybe a few other places that didn't seem quite as helpful, I did the following.

I've tried getting output from irw, xev, and "sudo mode2 -d /dev/lirc0". They all showed nothing when pressing buttons on the remote, no matter what I tried. 

First I simply tried installing lirc and lirc-x, but that didn't work at all. Then I tried "sudo apt-get purge lirc" and followed the instructions [here]("http://amodjaltade.blogspot.sg/2009/05/hp-remote-control-in-ubuntu.html"). Then when I tried running "sudo /etc/init.d/lirc start" I got

```
 * Loading LIRC modules                                                                                        [ OK ] 
find: `/sys/class/rc/*/': No such file or directory
 * Starting remote control daemon(s) : LIRC                                                                    [ OK ]
```

After some googling and whatnot, I eventually decided that I had no clue what /sys/class/rc/ is supposed to refer to. I opened it with Nautilus, and there is definitely nothing in there, not even hidden files.

A few people on other threads suggested various methods of finding out how the IR device was attached:

"ps -ef | grep lirc" gives
```
root      3577     1  0 17:27 ?        00:00:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --driver=default
micah    14882 21525  0 17:57 pts/12   00:00:00 grep --color=auto lirc

```

"dmesg | grep input" gives
```
[    0.293613] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.293658] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.293706] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.294090] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.835443] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.937216] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5
[   22.150398] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input6
[   22.189756] input: HP WMI hotkeys as /devices/virtual/input/input7
[   22.204410] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   22.204585] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   23.192130] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[15597.663054] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[15597.664714] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[15597.666739] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[15597.674924] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 4
[15597.677200] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1

```

"dmesg | grep IR" gives
```
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.186528] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.186576] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.186623] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.186668] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.186715] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.186763] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.186809] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.186858] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.187408] PCI: Using ACPI for IRQ routing
[    0.198997] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.250741] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.250757] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.250770] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.252055] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.252085] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.252119] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.252170] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.252198] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.252226] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.252256] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.314533] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.729368] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.730287] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.731728] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.748228] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.768255] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.768542] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.768826] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.769100] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.769380] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.353212] r8169 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.354241] r8169 0000:06:00.0: eth0: RTL8101e at 0xf8416000, 00:1e:68:19:39:25, XID 94200000 IRQ 44
[    1.387065] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.416354] sdhci-pci 0000:07:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.420802] firewire_ohci 0000:07:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.484091] firewire_ohci: Added fw-ohci device 0000:07:09.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[   21.876419] iwl4965 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.960444] r592 0000:07:09.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   21.966729] r852 0000:07:09.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   22.131991] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 3392.496049] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3392.499473] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 3392.499521] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 3392.499558] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 3392.499669] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 3392.499717] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 3392.499764] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 3392.499813] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 3392.499862] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 3392.501996] sdhci-pci 0000:07:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 6973.491802] lirc_dev: IR Remote Control driver registered, major 250 
[ 6973.567693] IR NEC protocol handler initialized
[ 6973.581875] IR RC5(x) protocol handler initialized
[ 6973.601372] IR RC6 protocol handler initialized
[ 6973.621332] IR JVC protocol handler initialized
[ 6973.623060] IR Sony protocol handler initialized
[ 6973.713038] IR MCE Keyboard/mouse protocol handler initialized
[ 6973.726416] IR LIRC bridge handler initialized
[15387.899476] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[15387.903514] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[15387.903565] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[15387.903601] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[15387.903711] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[15387.903757] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[15387.903806] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[15387.903855] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[15387.903903] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[15387.905292] sdhci-pci 0000:07:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[21201.419466] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[21201.423498] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[21201.423548] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[21201.423585] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[21201.423696] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[21201.423743] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[21201.423791] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[21201.423841] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[21201.423889] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[21201.425276] sdhci-pci 0000:07:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21

```

lspci gives
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
micah@micah-HP-Pavilion:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

lsusb gives
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 006 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 001 Device 005: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 002 Device 006: ID 0781:5530 SanDisk Corp. Cruzer

```



These were supposed to aid in finding where my IR device actually was located, but the only lines I see potentially pertaining to IR are ```
[ 6973.491802] lirc_dev: IR Remote Control driver registered, major 250 
[ 6973.567693] IR NEC protocol handler initialized
[ 6973.581875] IR RC5(x) protocol handler initialized
[ 6973.601372] IR RC6 protocol handler initialized
[ 6973.621332] IR JVC protocol handler initialized
[ 6973.623060] IR Sony protocol handler initialized
[ 6973.713038] IR MCE Keyboard/mouse protocol handler initialized
[ 6973.726416] IR LIRC bridge handler initialized
``` and those don't give a location. There was some point in the installation process where it asked which serial port my device was connected to (tty01 or tty02 or something like that). I didn't know, so I selected the first choice (tty01 if my memory serves), assuming I could always reinstall and select the second option. After re-installation, though, that does not reappear.

Someone else said to run "lsmod | grep lirc". I forget what it was used for, but here's the output in case it's at all helpful:
```
lirc_serial            18619  0 
ir_lirc_codec          12739  0 
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,mceusb
lirc_dev               18700  2 lirc_serial,ir_lirc_codec

```

According to [https://wiki.archlinux.org/index.php/Lirc](https://wiki.archlinux.org/index.php/Lirc), entering dmesg | grep tty should tell you what all the problems are. All it tells me is 
```
[    0.000000] console [tty0] enabled
```

I'm not really sure what to do. I'm almost positive the problem lies with /etc/lirc/hardware.conf. I've tried several different variations in there, but it still doesn't seem to work. I've spent several hours and haven't made much progress.

---

### Post by nuk28 on 2012-11-07
bump. I guess I can add that I don't really care about actually getting it to work with Banshee at the moment. Right now I just want output to occur when I run irw.

---

### Post by nuk28 on 2012-11-12
</a>">OK, so my remote is working now. I think maybe it's because I tried using it in Vista (where it also worked). But it keeps working if I stop the lirc process, so apparently there's something built into the kernel that supports some sort of IR.

The only problem now is that, since it's not using lirc, I don't know how to get the buttons doing anything special. The cursor, media playback, and power keys automatically do the right thing. But there's three buttons at the top (in Vista, they would start Quickplay, Quickplay DVD, and WMC) that don't do anything. I would like to allow them to open up the video pane of the dash and expand My Videos (keyboard sequence would be SUPER+V -> DOWN -> DOWN -> DOWN -> ENTER). Since it's not using lirc, then is there any way to recognize these not-standard inputs? I think in lirc the first two would be recognized as KEY_DVD and KEY_MEDIA. I don't know what the WMC button would be recognized as. lirc still isn't working, so I can't really test it. Any suggestions?

And sorry, but I just installed [My Global Ponies]("http://www.reddit.com/r/mylittlepony/comments/t9u9x/my_little_scripts_2_the_scriptpocalypse_guide_to/"). I hope it works. [](/flutteryay)

---

