---
title: "Audio Help"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by tesseract85 on 2008-02-05
Hello all,
   I have an Acer Ferrari 1000 and I would like to install Ubuntu and have the audio working to make this into a mobile audio creation suite. 
I have installed Sabayon linux in the past and have found that the audio does work with linux. 
I have attempted to follow the how to's in the forums for the other laptops that have similar audio and have found that they do not work. Please reply with the information you need, I will give it to you as soon as I get home from work.
I think that Ruurt's acer ferrari guide is mistaken, It does not work right out of the box. 
Thanks for the help in advance. 

Acer Ferrari 1000
amd64 ubuntu 7.10

---

### Post by tesseract85 on 2008-02-05
Specs as per acer: 

Specifications:
CPU: AMD Turion 64 X2 Mobile Technology TL-56 (1.8GHz, 2×512KB L2 Cache)
Chipset: ATI® Radeon® Xpress 1150
Front-side Bus:
Memory: DDR2 667MHz SDRAM
Memory Capacity: 1GB - 2GB (2 slots)

Graphics/Display:
Display: 12.1-inch Acer CrystalBrite
Resolution: 1280×800 WXGA
Touchscreen: No
Widescreen: Yes
Graphics Chipset: Integrated ATI® Radeon® Xpress 1150 graphics
Graphics Memory: Up to 512MB “Hypermemory”
Other: VGA, S-Video Out, Possibly HDMI

Storage:
Hard Drive: 160GB Serial ATA (SATA) Hard Drive (possibly another non-SATA option), 5400rpm
Optical: External Super-Multi DVD Writer (Possibly Firewire)
Other: - Acer® DASP (Disk Anti-Shock Protection)

Connectivity:
Wireless: Acer® InviLink 802.11n wireless LAN (Probably Broadcom based on past comments)
Modem: 56K V.92 Modem
Ethernet: 10/100/1000 Gigabit (Broadcom)
Bluetooth: Bluetooth® 2.0 + EDR (enhanced data rate) wireless PAN
Mobile Broadband: 

Input/Output:
Audio Chipset: Realtek High Definition Audio
Speakers: Integrated Microphone, Stereo Speakers
Audio I/O: Headphone-out (S/PDIF support), Microphone-in
USB: 4x USB 2.0
Firewire: 1x IEEE 1394
PC Card: 1x Type II PC Card
Flash/Memory Card Reader: 5-in-1 Card Reader - MultiMediaCard (MMC), Secure Digital card (SD), Memory Stick® (MS), Memory Stick PRO (MS Pro) or xD-Picture Card
Other: Acer OrbiCam webcam mounted in the top of the display, ezDock port/docking station, FIR (fast infrared) 

Security:
Biometric/Fingerprint:
Other: 

Software & Warranty:
Operating System: Microsoft Windows Vista Ultimate, Windows XP Professional
Other Software: Adobe Reader, Norton AntiVirus and CyberLink PowerDVD/CyberLink Power Producer, Acer GridVista and Acer Arcade Software Suite.
Warranty: 1 year Carry In (International travellers warranty - ITW) - 3 year coverage available through Acer Advantage service (covers accidental damage)
Drivers: AcerPanAm.com - North/South America Support

Battery:
Options: 3-cell and 6-cell
Battery Life: Some reviewers said just over 3 hours with 6-cell battery

Dimensions:
Width: 11.9 inches (302.3mm)
Depth: 8.7 inches (221.3mm)
Height: 0.8 - 1.4 inches (20.8mm - 34.5mm)
Weight: 4 pounds (1.8kg) with 6-cell battery, 3.7 pounds (1.7kg) with 3-cell battery

Again, I will let you know all that is needed when i get home from work about 4pm eastern standard time.

---

### Post by tesseract85 on 2008-02-06
lspci

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge

00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge

00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]

07:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)

08:04.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)

08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller

08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller

08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)



/etc/modprobe.d/alsa-base

# autoloader aliases

install sound-slot-0 /sbin/modprobe snd-card-0

install sound-slot-1 /sbin/modprobe snd-card-1

install sound-slot-2 /sbin/modprobe snd-card-2

install sound-slot-3 /sbin/modprobe snd-card-3

install sound-slot-4 /sbin/modprobe snd-card-4

install sound-slot-5 /sbin/modprobe snd-card-5

install sound-slot-6 /sbin/modprobe snd-card-6

install sound-slot-7 /sbin/modprobe snd-card-7



# Cause optional modules to be loaded above generic modules

install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }

install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }

install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }

install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }

# Cause optional modules to be loaded above sound card driver modules

install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }

install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }



# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)

install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }



# Load snd-seq for devices that don't have hardware midi;

#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for

#   non-Creative Labs PCI hardware

install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }

# Prevent abnormal drivers from grabbing index 0

options snd-bt87x index=-2

options cx88-alsa index=-2

options saa7134-alsa index=-2

options snd-atiixp-modem index=-2

options snd-intel8x0m index=-2

options snd-via82xx-modem index=-2

options snd-usb-audio index=-2

options snd-usb-usx2y index=-2

options snd-usb-caiaq index=-2

# Ubuntu #62691, enable MPU for snd-cmipci

options snd-cmipci mpu_port=0x330 fm_port=0x388

---

### Post by tesseract85 on 2008-02-10
Can anyone help me out? I would like to start recording on my laptop. Thanks.

---

### Post by Yellow Pasque on 2008-02-11
Try:
[http://ubuntuforums.org/showthread.php?t=451011](http://ubuntuforums.org/showthread.php?t=451011)

---

### Post by tesseract85 on 2008-02-12
I got it fixed. I jsut had to install ubuntu 6.06 lts. Now If i can get the gnome network scanner to work well with ndiswrapper

---

