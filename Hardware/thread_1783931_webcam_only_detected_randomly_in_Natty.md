---
title: "webcam only detected randomly in Natty"
date: 2011-06-16
forum: Hardware
---

### Post by misterglitch on 2011-06-16
I recently did a clean install of 11.04 desktop 32 bit with kernel 2.6.38-8-generic-pae on my laptop, a dell xps m1330.  Before I ran 8.04 with perfect webcam functionality.

On first boot the built-in webcam was working perfectly, but the next day it was no longer recognized: didn't appear in /dev/video0, no uvcvideo modules loaded, no appearance in either lspci or lsusb, and no flashing blue light to indicate cam is alive.  After searching the forums I found the suggestion that I manually reload the uvcmodules with
```

sudo modprobe -r uvcvideo
sudo modprobe uvcvideo

```
I did this, and it didn't seem to do anything.  Then I rebooted, and magically the blue light flashed and the cam worked: /dev/video0 there, modules loaded, skype/cheese working.  Cut to the next day and it's the same story.  On boot, the webcam isn't working.  This time the same tricks aren't working.  It would seem that perhaps the modprobe trick didn't really do anything, and that the hardware is just being randomly recognized on boot.

I've posted below the output from lsusb, lspci, and lsmod.  

Any ideas?  Help would be greatly appreciated!

Here's my lsusb:
```

Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Here's my lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```


Here's my lsmod:
```

Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
rfcomm                 38125  8 
sco                    17779  2 
snd_hda_codec_idt      60537  1 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
nvidia               7098106  38 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
iwlagn                284601  0 
iwlcore               148965  1 iwlagn
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17322  0 
r852                   17878  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              257001  2 iwlagn,iwlcore
nand_ecc               13070  1 nand
soundcore              12600  1 snd
mtd                    26530  2 sm_common,nand
cfg80211              156212  3 iwlagn,iwlcore,mac80211
psmouse                59039  0 
lp                     13349  0 
btusb                  18160  2 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
dell_laptop            13515  0 
dell_wmi               12601  0 
dcdbas                 14054  1 dell_laptop
video                  18951  0 
sparse_keymap          13666  1 dell_wmi
serio_raw              12990  0 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
crc_itu_t              12627  1 firewire_core
tg3                   131476  0 
sdhci                  22720  1 sdhci_pci
ahci                   21591  2 
libahci                25548  1 ahci

```

---

### Post by dredas on 2011-07-23
I am having the exact problem :( Once I installed Ubuntu (natty), the first time, webcam worked fine, and the nesxt time i rebooted I cannot launch my built-in-webcam. Error says:
 Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'

I researched much, but nothing helps.. :/ The only difference here, I see is that you have dell, i have asus. There is a bug with software, but nobody can offer a solution. Any help appreciated.

---

### Post by JDog2pt0 on 2011-07-31
I'm in the same boat as well with my Dell Inspiron 1525. Only thing is, those two commands do work for me, but I have to do it almost every reboot.

---

