---
title: "sounds driver installed."
date: 2018-02-06
forum: Hardware
---

### Post by rick-fvwc on 2018-02-06
My sounds driver did not install. NO sound
When I go to sounds settings the profile says: "Analog Stereo Output" with nothing else to select.
When I test speakers there is no sound.

-PCI Devices-
Host bridge		: Advanced Micro Devices, Inc. [AMD] Device 1576
IOMMU		        : Advanced Micro Devices, Inc. [AMD] Device 1577
VGA compatible controller		: Advanced Micro Devices, Inc. [AMD/ATI] Carrizo (rev ca) (prog-if 00 [VGA controller])
Audio device		: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
Host bridge		: Advanced Micro Devices, Inc. [AMD] Device 157b
PCI bridge		: Advanced Micro Devices, Inc. [AMD] Device 157c (prog-if 00 [Normal decode])
PCI bridge		: Advanced Micro Devices, Inc. [AMD] Device 157c (prog-if 00 [Normal decode])
PCI bridge		: Advanced Micro Devices, Inc. [AMD] Device 157c (prog-if 00 [Normal decode])
Host bridge		: Advanced Micro Devices, Inc. [AMD] Device 157b
PCI bridge		: Advanced Micro Devices, Inc. [AMD] Device 157c (prog-if 00 [Normal decode])
Encryption controller		: Advanced Micro Devices, Inc. [AMD] Device 1578
Host bridge		: Advanced Micro Devices, Inc. [AMD] Device 157d
Audio device		: Advanced Micro Devices, Inc. [AMD] Device 157a
USB controller		: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 20) (prog-if 30 [XHCI])
SATA controller		: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 49) (prog-if 01 [AHCI 1.0])
USB controller		: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 49) (prog-if 20 [EHCI])
SMBus		        : Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 4a)
ISA bridge		: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
Host bridge		: Advanced Micro Devices, Inc. [AMD] Device 1570
Host bridge		: Advanced Micro Devices, Inc. [AMD] Device 1571
Host bridge		: Advanced Micro Devices, Inc. [AMD] Device 1572
Host bridge		: Advanced Micro Devices, Inc. [AMD] Device 1573
Host bridge		: Advanced Micro Devices, Inc. [AMD] Device 1574
Host bridge		: Advanced Micro Devices, Inc. [AMD] Device 1575

---

### Post by Yellow Pasque on 2018-02-06
First off, this will make your lspci output easier to read:
```
sudo update-pciids
```

Then, get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by rick-fvwc on 2018-02-06
[http://www.alsa-project.org/db/?f=f0be93e965db351f1a2a366a6ce0410e0a930bfa](http://www.alsa-project.org/db/?f=f0be93e965db351f1a2a366a6ce0410e0a930bfa)



[FONT=Ubuntu Mono, monospace][COLOR=#000000]
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Tue Feb  6 22:33:17 UTC 2018


!!Linux Distribution
!!------------------

Ubuntu 17.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 17.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 17.10" HOME_URL="https://www.ubuntu.com/" SUPPORT_URL="https://help.ubuntu.com/" BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" UBUNTU_CODENAME=artful


!!DMI Information
!!---------------

Manufacturer:      HP
Product Name:      HP Pavilion Laptop 15-cd0xx
Product Version:    
Firmware Version:  F.04
Board Vendor:      HP
Board Name:        8354


!!ACPI Device Status Information
!!---------------

/sys/bus/acpi/devices/ACPI0003:00/status 	 15
/sys/bus/acpi/devices/ASD0001:00/status 	 15
/sys/bus/acpi/devices/BCM2F25:00/status 	 15
/sys/bus/acpi/devices/BCM4752:00/status 	 15
/sys/bus/acpi/devices/ETD072E:00/status 	 15
/sys/bus/acpi/devices/HPQ6001:00/status 	 15
/sys/bus/acpi/devices/HPQ6007:00/status 	 15
/sys/bus/acpi/devices/HPQ8001:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:00/status 	 1
/sys/bus/acpi/devices/LNXPOWER:01/status 	 1
/sys/bus/acpi/devices/LNXVIDEO:00/status 	 15
/sys/bus/acpi/devices/MSFT0101:00/status 	 15
/sys/bus/acpi/devices/PNP0103:00/status 	 15
/sys/bus/acpi/devices/PNP0A08:00/status 	 15
/sys/bus/acpi/devices/PNP0C01:00/status 	 15
/sys/bus/acpi/devices/PNP0C02:02/status 	 15
/sys/bus/acpi/devices/PNP0C0A:00/status 	 31
/sys/bus/acpi/devices/PNP0C0C:00/status 	 11
/sys/bus/acpi/devices/PNP0C0F:00/status 	 11
/sys/bus/acpi/devices/PNP0C0F:01/status 	 11
/sys/bus/acpi/devices/PNP0C0F:02/status 	 11
/sys/bus/acpi/devices/PNP0C0F:03/status 	 11
/sys/bus/acpi/devices/PNP0C0F:04/status 	 11
/sys/bus/acpi/devices/PNP0C0F:05/status 	 11
/sys/bus/acpi/devices/PNP0C0F:06/status 	 11
/sys/bus/acpi/devices/PNP0C0F:07/status 	 11
/sys/bus/acpi/devices/SMB0001:00/status 	 15
/sys/bus/acpi/devices/device:27/status 	 15


!!Kernel Information
!!------------------

Kernel release:    4.13.0-32-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.13.0-32-generic
Library version:    1.1.3
Utilities version:  1.1.3


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfeb64000 irq 45
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeb60000 irq 46


!!PCI Soundcards installed in the system
!!--------------------------------------

00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:09.2 Audio device: Advanced Micro Devices, Inc. [AMD] Device 157a


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:01.1 0403: 1002:9840
	Subsystem: 103c:8354
--
00:09.2 0403: 1022:157a
	Subsystem: 103c:8354


!!Modprobe options (Sound related)
!!--------------------------------

snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : -1
	snoop : -1

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : -1
	snoop : -1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100700
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=1, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x02
Node 0x04 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x08 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x09 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Codec: Realtek ALC295
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0295
Subsystem Id: 0x103c8354
Revision Id: 0x100002
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 D3cold CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x57 0x57]
  Converter: stream=5, channel=0
  PCM:
    rates [0x60]: 44100 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC295 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=5, channel=0
  PCM:
    rates [0x60]: 44100 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x40]: 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x07 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x97 0x97]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x40]: 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC295 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x3d 0x3d]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x97 0x97]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0xb7a60130: [Fixed] Mic at Oth Mobile-In
    Conn = Digital, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40000000: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x02
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 2
     0x02* 0x03
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 3
     0x02* 0x03 0x06
Node 0x18 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x19 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x03a11040: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1a [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00013734: IN OUT EAPD Detect
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 2
     0x02* 0x03
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40600001: [N/A] Modem Line at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1e [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=104
Node 0x21 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x03211020: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 2
     0x02 0x03*
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 5
     0x19 0x1a 0x1b 0x1d 0x13
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x00 0x00]
  Connection: 5
     0x19 0x1a 0x1b 0x1d 0x12
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x12* 0x13 0x18
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  2 Feb  6 12:21 /dev/snd/controlC0
crw-rw----  1 root audio 116,  5 Feb  6 12:21 /dev/snd/controlC1
crw-rw----  1 root audio 116,  4 Feb  6 12:21 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  8 Feb  6 12:21 /dev/snd/hwC1D0
crw-rw----  1 root audio 116,  3 Feb  6 12:21 /dev/snd/pcmC0D3p
crw-rw----  1 root audio 116,  7 Feb  6 12:21 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116,  6 Feb  6 17:23 /dev/snd/pcmC1D0p
crw-rw----  1 root audio 116,  1 Feb  6 12:21 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Feb  6 12:21 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Feb  6 12:21 .
drwxr-xr-x 3 root root 240 Feb  6 12:21 ..
lrwxrwxrwx 1 root root  12 Feb  6 12:21 pci-0000:00:01.1 -> ../controlC0
lrwxrwxrwx 1 root root  12 Feb  6 12:21 pci-0000:00:09.2 -> ../controlC1


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC295 Analog [ALC295 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: Generic [HD-Audio Generic], device 0: ALC295 Analog [ALC295 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [HDMI]

Card hw:0 'HDMI'/'HDA ATI HDMI at 0xfeb64000 irq 45'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100700'
  Controls      : 7
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [Generic]

Card hw:1 'Generic'/'HD-Audio Generic at 0xfeb60000 irq 46'
  Mixer name	: 'Realtek ALC295'
  Components	: 'HDA:10ec0295,103c8354,00100002'
  Controls      : 18
  Simple ctrls  : 8
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 0 [0%] [-65.25dB] [off]
  Front Right: Playback 0 [0%] [-65.25dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 63
  Front Left: Capture 61 [97%] [28.50dB] [on]
  Front Right: Capture 61 [97%] [28.50dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]


!!Alsactl output
!!--------------

--startcollapse--
state.HDMI {
	control.1 {
		iface CARD
		name 'HDMI/DP,pcm=3 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.5 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface PCM
		device 3
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.7 {
		iface PCM
		device 3
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access 'read write'
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
}
state.Generic {
	control.1 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 -6525
			dbvalue.1 -6525
		}
	}
	control.2 {
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 87
		value.1 87
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.4 {
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.5 {
		iface MIXER
		name 'Auto-Mute Mode'
		value Enabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.6 {
		iface MIXER
		name 'Capture Volume'
		value.0 61
		value.1 61
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 63'
			dbmin -1725
			dbmax 3000
			dbvalue.0 2850
			dbvalue.1 2850
		}
	}
	control.7 {
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.8 {
		iface MIXER
		name 'Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.9 {
		iface MIXER
		name 'Internal Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.10 {
		iface MIXER
		name 'Master Playback Volume'
		value 87
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 0
		}
	}
	control.11 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.12 {
		iface CARD
		name 'Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.13 {
		iface CARD
		name 'Internal Mic Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.14 {
		iface CARD
		name 'Headphone Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.15 {
		iface CARD
		name 'Speaker Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.16 {
		iface PCM
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.17 {
		iface PCM
		name 'Capture Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.18 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ccm
rfcomm
cmac
bnep
nls_iso8859_1
edac_mce_amd
kvm
irqbypass
crct10dif_pclmul
crc32_pclmul
ghash_clmulni_intel
uvcvideo
pcbc
arc4
videobuf2_vmalloc
aesni_intel
aes_x86_64
crypto_simd
glue_helper
videobuf2_memops
cryptd
videobuf2_v4l2
videobuf2_core
btusb
btrtl
videodev
iwlmvm
media
btbcm
btintel
joydev
mac80211
hp_wmi
input_leds
wmi_bmof
bluetooth
serio_raw
sparse_keymap
ecdh_generic
iwlwifi
fam15h_power
k10temp
i2c_piix4
cfg80211
rtsx_pci_ms
memstick
snd_hda_codec_realtek
snd_hda_codec_generic
snd_hda_codec_hdmi
snd_hda_intel
snd_hda_codec
snd_hda_core
snd_hwdep
hp_accel
i2c_scmi
lis3lv02d
input_polldev
snd_pcm
hp_wireless
snd_seq_midi
tpm_crb
snd_seq_midi_event
rfkill_gpio
snd_rawmidi
8250_dw
snd_seq
mac_hid
snd_seq_device
snd_timer
snd
soundcore
shpchp
parport_pc
ppdev
lp
parport
ip_tables
x_tables
autofs4
amdkfd
amd_iommu_v2
amdgpu
i2c_algo_bit
ttm
drm_kms_helper
rtsx_pci_sdmmc
syscopyarea
sysfillrect
sysimgblt
fb_sys_fops
ahci
psmouse
libahci
r8169
drm
mii
rtsx_pci
wmi
i2c_hid
video
hid


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x185600f0
0x05 0x585600f0
0x07 0x585600f0
0x09 0x585600f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:

/sys/class/sound/hwC1D0/init_pin_configs:
0x12 0xb7a60130
0x13 0x40000000
0x14 0x90170110
0x16 0x411111f0
0x17 0x411111f0
0x18 0x411111f0
0x19 0x03a11040
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x40600001
0x1e 0x411111f0
0x21 0x03211020

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC1D0/hints:


!!ALSA/HDA dmesg
!!--------------

[    2.218212] [drm] Connector 1:
[    2.218213] [drm]   HDMI-A-1
[    2.218213] [drm]   HPD2
--
[   14.061013] lis3lv02d: 8 bits 3DC sensor found
[   14.072793] snd_hda_intel 0000:00:01.1: enabling device (0000 -> 0002)
[   14.072935] snd_hda_intel 0000:00:01.1: Force to non-snoop mode
[   14.073167] snd_hda_intel 0000:00:09.2: enabling device (0004 -> 0006)
[   14.082528] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input9
[   14.089930] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC295: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   14.089934] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   14.089936] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   14.089937] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[   14.089938] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[   14.089940] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x19
[   14.089941] snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x12
[   14.092449] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input10
[   14.164072] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:09.2/sound/card1/input11
[   14.164138] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:09.2/sound/card1/input12
[   14.212755] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[/COLOR][/FONT][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]
[/FONT]

!!################################
!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Tue Feb  6 22:33:17 UTC 2018




!!Linux Distribution
!!------------------


Ubuntu 17.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 17.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 17.10" HOME_URL="https://www.ubuntu.com/" SUPPORT_URL="https://help.ubuntu.com/" BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" UBUNTU_CODENAME=artful




!!DMI Information
!!---------------


Manufacturer:      HP
Product Name:      HP Pavilion Laptop 15-cd0xx
Product Version:    
Firmware Version:  F.04
Board Vendor:      HP
Board Name:        8354




!!ACPI Device Status Information
!!---------------


/sys/bus/acpi/devices/ACPI0003:00/status 	 15
/sys/bus/acpi/devices/ASD0001:00/status 	 15
/sys/bus/acpi/devices/BCM2F25:00/status 	 15
/sys/bus/acpi/devices/BCM4752:00/status 	 15
/sys/bus/acpi/devices/ETD072E:00/status 	 15
/sys/bus/acpi/devices/HPQ6001:00/status 	 15
/sys/bus/acpi/devices/HPQ6007:00/status 	 15
/sys/bus/acpi/devices/HPQ8001:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:00/status 	 1
/sys/bus/acpi/devices/LNXPOWER:01/status 	 1
/sys/bus/acpi/devices/LNXVIDEO:00/status 	 15
/sys/bus/acpi/devices/MSFT0101:00/status 	 15
/sys/bus/acpi/devices/PNP0103:00/status 	 15
/sys/bus/acpi/devices/PNP0A08:00/status 	 15
/sys/bus/acpi/devices/PNP0C01:00/status 	 15
/sys/bus/acpi/devices/PNP0C02:02/status 	 15
/sys/bus/acpi/devices/PNP0C0A:00/status 	 31
/sys/bus/acpi/devices/PNP0C0C:00/status 	 11
/sys/bus/acpi/devices/PNP0C0F:00/status 	 11
/sys/bus/acpi/devices/PNP0C0F:01/status 	 11
/sys/bus/acpi/devices/PNP0C0F:02/status 	 11
/sys/bus/acpi/devices/PNP0C0F:03/status 	 11
/sys/bus/acpi/devices/PNP0C0F:04/status 	 11
/sys/bus/acpi/devices/PNP0C0F:05/status 	 11
/sys/bus/acpi/devices/PNP0C0F:06/status 	 11
/sys/bus/acpi/devices/PNP0C0F:07/status 	 11
/sys/bus/acpi/devices/SMB0001:00/status 	 15
/sys/bus/acpi/devices/device:27/status 	 15




!!Kernel Information
!!------------------


Kernel release:    4.13.0-32-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     k4.13.0-32-generic
Library version:    1.1.3
Utilities version:  1.1.3




!!Loaded ALSA modules
!!-------------------


snd_hda_intel
snd_hda_intel




!!Sound Servers on this system
!!----------------------------


Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes




!!Soundcards recognised by ALSA
!!-----------------------------


 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfeb64000 irq 45
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeb60000 irq 46




!!PCI Soundcards installed in the system
!!--------------------------------------


00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:09.2 Audio device: Advanced Micro Devices, Inc. [AMD] Device 157a




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:01.1 0403: 1002:9840
	Subsystem: 103c:8354
--
00:09.2 0403: 1022:157a
	Subsystem: 103c:8354




!!Modprobe options (Sound related)
!!--------------------------------


snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2




!!Loaded sound module options
!!---------------------------


!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : -1
	snoop : -1


!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : -1
	snoop : -1




!!HDA-Intel Codec information
!!---------------------------
--startcollapse--


Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100700
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=1, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x02
Node 0x04 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x08 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x09 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Codec: Realtek ALC295
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0295
Subsystem Id: 0x103c8354
Revision Id: 0x100002
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 D3cold CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x57 0x57]
  Converter: stream=5, channel=0
  PCM:
    rates [0x60]: 44100 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC295 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=5, channel=0
  PCM:
    rates [0x60]: 44100 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x40]: 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x07 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x97 0x97]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x40]: 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC295 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x3d 0x3d]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x97 0x97]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0xb7a60130: [Fixed] Mic at Oth Mobile-In
    Conn = Digital, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40000000: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x02
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 2
     0x02* 0x03
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 3
     0x02* 0x03 0x06
Node 0x18 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x19 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x03a11040: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1a [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00013734: IN OUT EAPD Detect
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 2
     0x02* 0x03
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40600001: [N/A] Modem Line at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1e [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=104
Node 0x21 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x03211020: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 2
     0x02 0x03*
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 5
     0x19 0x1a 0x1b 0x1d 0x13
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x00 0x00]
  Connection: 5
     0x19 0x1a 0x1b 0x1d 0x12
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x12* 0x13 0x18
--endcollapse--




!!ALSA Device nodes
!!-----------------


crw-rw----  1 root audio 116,  2 Feb  6 12:21 /dev/snd/controlC0
crw-rw----  1 root audio 116,  5 Feb  6 12:21 /dev/snd/controlC1
crw-rw----  1 root audio 116,  4 Feb  6 12:21 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  8 Feb  6 12:21 /dev/snd/hwC1D0
crw-rw----  1 root audio 116,  3 Feb  6 12:21 /dev/snd/pcmC0D3p
crw-rw----  1 root audio 116,  7 Feb  6 12:21 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116,  6 Feb  6 17:23 /dev/snd/pcmC1D0p
crw-rw----  1 root audio 116,  1 Feb  6 12:21 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Feb  6 12:21 /dev/snd/timer


/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Feb  6 12:21 .
drwxr-xr-x 3 root root 240 Feb  6 12:21 ..
lrwxrwxrwx 1 root root  12 Feb  6 12:21 pci-0000:00:01.1 -> ../controlC0
lrwxrwxrwx 1 root root  12 Feb  6 12:21 pci-0000:00:09.2 -> ../controlC1




!!Aplay/Arecord output
!!--------------------


APLAY


**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC295 Analog [ALC295 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ARECORD


**** List of CAPTURE Hardware Devices ****
card 1: Generic [HD-Audio Generic], device 0: ALC295 Analog [ALC295 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


!!Amixer output
!!-------------


!!-------Mixer controls for card 0 [HDMI]


Card hw:0 'HDMI'/'HDA ATI HDMI at 0xfeb64000 irq 45'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100700'
  Controls      : 7
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


!!-------Mixer controls for card 1 [Generic]


Card hw:1 'Generic'/'HD-Audio Generic at 0xfeb60000 irq 46'
  Mixer name	: 'Realtek ALC295'
  Components	: 'HDA:10ec0295,103c8354,00100002'
  Controls      : 18
  Simple ctrls  : 8
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 0 [0%] [-65.25dB] [off]
  Front Right: Playback 0 [0%] [-65.25dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 63
  Front Left: Capture 61 [97%] [28.50dB] [on]
  Front Right: Capture 61 [97%] [28.50dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]




!!Alsactl output
!!--------------


--startcollapse--
state.HDMI {
	control.1 {
		iface CARD
		name 'HDMI/DP,pcm=3 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.5 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface PCM
		device 3
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.7 {
		iface PCM
		device 3
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access 'read write'
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
}
state.Generic {
	control.1 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 -6525
			dbvalue.1 -6525
		}
	}
	control.2 {
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 87
		value.1 87
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.4 {
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.5 {
		iface MIXER
		name 'Auto-Mute Mode'
		value Enabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.6 {
		iface MIXER
		name 'Capture Volume'
		value.0 61
		value.1 61
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 63'
			dbmin -1725
			dbmax 3000
			dbvalue.0 2850
			dbvalue.1 2850
		}
	}
	control.7 {
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.8 {
		iface MIXER
		name 'Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.9 {
		iface MIXER
		name 'Internal Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.10 {
		iface MIXER
		name 'Master Playback Volume'
		value 87
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 0
		}
	}
	control.11 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.12 {
		iface CARD
		name 'Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.13 {
		iface CARD
		name 'Internal Mic Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.14 {
		iface CARD
		name 'Headphone Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.15 {
		iface CARD
		name 'Speaker Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.16 {
		iface PCM
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.17 {
		iface PCM
		name 'Capture Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.18 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
}
--endcollapse--




!!All Loaded Modules
!!------------------


Module
ccm
rfcomm
cmac
bnep
nls_iso8859_1
edac_mce_amd
kvm
irqbypass
crct10dif_pclmul
crc32_pclmul
ghash_clmulni_intel
uvcvideo
pcbc
arc4
videobuf2_vmalloc
aesni_intel
aes_x86_64
crypto_simd
glue_helper
videobuf2_memops
cryptd
videobuf2_v4l2
videobuf2_core
btusb
btrtl
videodev
iwlmvm
media
btbcm
btintel
joydev
mac80211
hp_wmi
input_leds
wmi_bmof
bluetooth
serio_raw
sparse_keymap
ecdh_generic
iwlwifi
fam15h_power
k10temp
i2c_piix4
cfg80211
rtsx_pci_ms
memstick
snd_hda_codec_realtek
snd_hda_codec_generic
snd_hda_codec_hdmi
snd_hda_intel
snd_hda_codec
snd_hda_core
snd_hwdep
hp_accel
i2c_scmi
lis3lv02d
input_polldev
snd_pcm
hp_wireless
snd_seq_midi
tpm_crb
snd_seq_midi_event
rfkill_gpio
snd_rawmidi
8250_dw
snd_seq
mac_hid
snd_seq_device
snd_timer
snd
soundcore
shpchp
parport_pc
ppdev
lp
parport
ip_tables
x_tables
autofs4
amdkfd
amd_iommu_v2
amdgpu
i2c_algo_bit
ttm
drm_kms_helper
rtsx_pci_sdmmc
syscopyarea
sysfillrect
sysimgblt
fb_sys_fops
ahci
psmouse
libahci
r8169
drm
mii
rtsx_pci
wmi
i2c_hid
video
hid




!!Sysfs Files
!!-----------


/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x185600f0
0x05 0x585600f0
0x07 0x585600f0
0x09 0x585600f0


/sys/class/sound/hwC0D0/driver_pin_configs:


/sys/class/sound/hwC0D0/user_pin_configs:


/sys/class/sound/hwC0D0/init_verbs:


/sys/class/sound/hwC0D0/hints:


/sys/class/sound/hwC1D0/init_pin_configs:
0x12 0xb7a60130
0x13 0x40000000
0x14 0x90170110
0x16 0x411111f0
0x17 0x411111f0
0x18 0x411111f0
0x19 0x03a11040
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x40600001
0x1e 0x411111f0
0x21 0x03211020


/sys/class/sound/hwC1D0/driver_pin_configs:


/sys/class/sound/hwC1D0/user_pin_configs:


/sys/class/sound/hwC1D0/init_verbs:


/sys/class/sound/hwC1D0/hints:




!!ALSA/HDA dmesg
!!--------------


[    2.218212] [drm] Connector 1:
[    2.218213] [drm]   HDMI-A-1
[    2.218213] [drm]   HPD2
--
[   14.061013] lis3lv02d: 8 bits 3DC sensor found
[   14.072793] snd_hda_intel 0000:00:01.1: enabling device (0000 -> 0002)
[   14.072935] snd_hda_intel 0000:00:01.1: Force to non-snoop mode
[   14.073167] snd_hda_intel 0000:00:09.2: enabling device (0004 -> 0006)
[   14.082528] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input9
[   14.089930] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC295: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   14.089934] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   14.089936] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   14.089937] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[   14.089938] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[   14.089940] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x19
[   14.089941] snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x12
[   14.092449] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input10
[   14.164072] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:09.2/sound/card1/input11
[   14.164138] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:09.2/sound/card1/input12
[   14.212755] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0

---

### Post by Yellow Pasque on 2018-02-07
Everything looks okay there. The correct driver is installed/used for onboard and HDMI audio devices. Maybe it is a pulseaudio problem?
```
pactl list sinks
```

Which device are you trying to use? If you don't want analog stereo output, wich output do you want?

---

### Post by rick-fvwc on 2018-02-07
Didn't do anything but send the info you asked for and suddenly sound is working. Thanks for helping. Not sure what happened.

---

### Post by rick-fvwc on 2018-02-08
Now sound is not working again...

and to add to that the terminal will not let me copy the text output on it now so I can paste it in here.

---

### Post by rick-fvwc on 2018-02-08
ok, so i discovered that when i close the lid to the laptop, wait a moment and then reopen and log back in the audio works. Rebooting kills whatever that fixes.

---

### Post by rick-fvwc on 2018-02-08
ok, so i discovered that when i close the lid to the laptop, wait a moment and then reopen and log back in the audio works. Rebooting kills whatever that fixes.

---

