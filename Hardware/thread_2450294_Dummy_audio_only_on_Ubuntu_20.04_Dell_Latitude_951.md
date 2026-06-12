---
title: "Dummy audio only on Ubuntu 20.04 Dell Latitude 9510"
date: 2020-09-10
forum: Hardware
---

### Post by DrIdiot on 2020-09-10
Fresh install of 20.04 on a Dell Latitude 9510 has dummy audio only.  Things I've tried:

1) Force reloading alsa, reinstalling alsa and pulseaudio

2) The sound card appears to be detected:
```

harrison@lassen:~$ lspci -nnk | grep audio
00:1f.3 Multimedia audio controller [0401]: Intel Corporation Device [8086:02c8]

```

3) I ran alsamixer and the sound card shows up.  There are 5 S/PDIF boxes with 00 in them, but no mixers.

4) Tried the stuff in here: [https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html](https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html) and it didn't work.  Adding "options snd-hda-intel model=generic" did change the output to HDMI output but I don't have any HDMI attached and still no sound.

5) I've seen this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1874465](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1874465)  However, force reload does not work for me and I do not have Timidity running or installed'

6) Following the suggestions [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) here are some terminal outputs

```

harrison@lassen:~$ bash alsa-info.sh --stdout
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.65
!!################################

!!Script ran on: Thu Sep 10 20:42:54 UTC 2020


!!Linux Distribution
!!------------------

Ubuntu 20.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 20.04.1 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 20.04.1 LTS" HOME_URL="https://www.ubuntu.com/" SUPPORT_URL="https://help.ubuntu.com/" BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" UBUNTU_CODENAME=focal


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.
Product Name:      Latitude 9510
Product Version:   
Firmware Version:  1.2.2
Board Vendor:      Dell Inc.
Board Name:        0G0T42


!!ACPI Device Status Information
!!---------------

/sys/bus/acpi/devices/ACPI0003:00/status 	 15
/sys/bus/acpi/devices/ACPI000C:00/status 	 15
/sys/bus/acpi/devices/DELL08AF:00/status 	 15
/sys/bus/acpi/devices/DLLK0983:00/status 	 15
/sys/bus/acpi/devices/INT33A1:00/status 	 15
/sys/bus/acpi/devices/INT33D3:00/status 	 15
/sys/bus/acpi/devices/INT33D4:00/status 	 15
/sys/bus/acpi/devices/INT33D5:00/status 	 15
/sys/bus/acpi/devices/INT3400:00/status 	 15
/sys/bus/acpi/devices/INT3403:00/status 	 15
/sys/bus/acpi/devices/INT3403:01/status 	 15
/sys/bus/acpi/devices/INT3403:02/status 	 15
/sys/bus/acpi/devices/INT3403:03/status 	 15
/sys/bus/acpi/devices/INT3403:04/status 	 15
/sys/bus/acpi/devices/INT3403:05/status 	 15
/sys/bus/acpi/devices/INT3407:00/status 	 15
/sys/bus/acpi/devices/INT340E:00/status 	 15
/sys/bus/acpi/devices/INT34BB:00/status 	 15
/sys/bus/acpi/devices/INT3532:00/status 	 15
/sys/bus/acpi/devices/INT3F0D:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:01/status 	 1
/sys/bus/acpi/devices/LNXPOWER:02/status 	 15
/sys/bus/acpi/devices/LNXPOWER:04/status 	 1
/sys/bus/acpi/devices/LNXPOWER:05/status 	 1
/sys/bus/acpi/devices/LNXPOWER:06/status 	 1
/sys/bus/acpi/devices/LNXPOWER:07/status 	 1
/sys/bus/acpi/devices/MSFT0101:00/status 	 15
/sys/bus/acpi/devices/PNP0103:00/status 	 15
/sys/bus/acpi/devices/PNP0B00:00/status 	 15
/sys/bus/acpi/devices/PNP0C02:00/status 	 3
/sys/bus/acpi/devices/PNP0C02:02/status 	 3
/sys/bus/acpi/devices/PNP0C02:05/status 	 3
/sys/bus/acpi/devices/PNP0C09:00/status 	 15
/sys/bus/acpi/devices/PNP0C0A:00/status 	 31
/sys/bus/acpi/devices/PNP0C0F:00/status 	 9
/sys/bus/acpi/devices/PNP0C0F:01/status 	 9
/sys/bus/acpi/devices/PNP0C0F:02/status 	 9
/sys/bus/acpi/devices/PNP0C0F:03/status 	 9
/sys/bus/acpi/devices/PNP0C0F:04/status 	 9
/sys/bus/acpi/devices/PNP0C0F:05/status 	 9
/sys/bus/acpi/devices/PNP0C0F:06/status 	 9
/sys/bus/acpi/devices/PNP0C0F:07/status 	 9
/sys/bus/acpi/devices/PRP00001:00/status 	 11
/sys/bus/acpi/devices/USBC000:00/status 	 15
/sys/bus/acpi/devices/device:09/status 	 15


!!Kernel Information
!!------------------

Kernel release:    5.4.0-47-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k5.4.0-47-generic
Library version:    1.2.2
Utilities version:  1.2.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0x604b118000 irq 185


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.3 Multimedia audio controller [0401]: Intel Corporation Device [8086:02c8]
	DeviceName: Onboard - Sound


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
	dmic_detect : Y
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	pm_blacklist : Y
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 1
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : -1
	snoop : -1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Intel Kabylake HDMI
Address: 2
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x8086280b
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x06 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x07 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x08 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  8 Sep 10 16:40 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  7 Sep 10 16:40 /dev/snd/hwC0D2
crw-rw----+ 1 root audio 116,  6 Sep 10 16:41 /dev/snd/pcmC0D10p
crw-rw----+ 1 root audio 116,  2 Sep 10 16:41 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  3 Sep 10 16:41 /dev/snd/pcmC0D7p
crw-rw----+ 1 root audio 116,  4 Sep 10 16:41 /dev/snd/pcmC0D8p
crw-rw----+ 1 root audio 116,  5 Sep 10 16:41 /dev/snd/pcmC0D9p
crw-rw----+ 1 root audio 116,  1 Sep 10 16:40 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Sep 10 16:40 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Sep 10 16:40 .
drwxr-xr-x 3 root root 240 Sep 10 16:40 ..
lrwxrwxrwx 1 root root  12 Sep 10 16:40 pci-0000:00:1f.3 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****

!!Amixer output
!!-------------

!!-------Mixer controls for card PCH

Card hw:0 'PCH'/'HDA Intel PCH at 0x604b118000 irq 185'
  Mixer name	: 'Intel Kabylake HDMI'
  Components	: 'HDA:8086280b,80860101,00100000'
  Controls      : 35
  Simple ctrls  : 5
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',3
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',4
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
state.PCH {
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
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
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
		iface CARD
		name 'HDMI/DP,pcm=7 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.8 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 1
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.9 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 1
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.10 {
		iface MIXER
		name 'IEC958 Playback Default'
		index 1
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.11 {
		iface MIXER
		name 'IEC958 Playback Switch'
		index 1
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.12 {
		iface PCM
		device 7
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.13 {
		iface CARD
		name 'HDMI/DP,pcm=8 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.14 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 2
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.15 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 2
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.16 {
		iface MIXER
		name 'IEC958 Playback Default'
		index 2
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.17 {
		iface MIXER
		name 'IEC958 Playback Switch'
		index 2
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.18 {
		iface PCM
		device 8
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.19 {
		iface CARD
		name 'HDMI/DP,pcm=9 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.20 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 3
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.21 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 3
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.22 {
		iface MIXER
		name 'IEC958 Playback Default'
		index 3
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.23 {
		iface MIXER
		name 'IEC958 Playback Switch'
		index 3
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.24 {
		iface PCM
		device 9
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.25 {
		iface CARD
		name 'HDMI/DP,pcm=10 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.26 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 4
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.27 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 4
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.28 {
		iface MIXER
		name 'IEC958 Playback Default'
		index 4
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.29 {
		iface MIXER
		name 'IEC958 Playback Switch'
		index 4
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.30 {
		iface PCM
		device 10
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.31 {
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
	control.32 {
		iface PCM
		device 7
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
	control.33 {
		iface PCM
		device 8
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
	control.34 {
		iface PCM
		device 9
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
	control.35 {
		iface PCM
		device 10
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
--endcollapse--


!!All Loaded Modules
!!------------------

ac97_bus
acpi_pad
acpi_thermal_rel
aesni_intel
af_alg
algif_hash
algif_skcipher
autofs4
bluetooth
bnep
btbcm
btintel
btrtl
btusb
ccm
cfg80211
cmac
coretemp
crc32_pclmul
crct10dif_pclmul
cros_ec
cros_ec_ishtp
cryptd
crypto_simd
dcdbas
dell_laptop
dell_rbtn
dell_smbios
dell_smm_hwmon
dell_wmi
dell_wmi_descriptor
dptf_power
drm
drm_kms_helper
ecc
ecdh_generic
fb_sys_fops
ghash_clmulni_intel
glue_helper
hid
hid_generic
hid_multitouch
hid_sensor_accel_3d
hid_sensor_als
hid_sensor_custom
hid_sensor_gyro_3d
hid_sensor_hub
hid_sensor_iio_common
hid_sensor_trigger
i2c_algo_bit
i2c_hid
i2c_i801
i915
idma64
industrialio
industrialio_triggered_buffer
input_leds
int3400_thermal
int3403_thermal
int340x_thermal_zone
intel_cstate
intel_hid
intel_ish_ipc
intel_ishtp
intel_ishtp_hid
intel_ishtp_loader
intel_lpss
intel_lpss_pci
intel_powerclamp
intel_rapl_common
intel_rapl_msr
intel_soc_dts_iosf
intel_wmi_thunderbolt
ip_tables
iwlmvm
iwlwifi
joydev
kfifo_buf
kvm
kvm_intel
ledtrig_audio
libarc4
lp
mac80211
mac_hid
mc
mei
mei_hdcp
mei_me
memstick
nls_iso8859_1
nvme
nvme_core
parport
parport_pc
pinctrl_cannonlake
pinctrl_intel
ppdev
processor_thermal_device
psmouse
rfcomm
rtsx_pci
rtsx_pci_ms
rtsx_pci_sdmmc
sch_fq_codel
serio_raw
snd
snd_compress
snd_hda_codec
snd_hda_codec_hdmi
snd_hda_core
snd_hda_ext_core
snd_hda_intel
snd_hwdep
snd_intel_dspcfg
snd_pcm
snd_pcm_dmaengine
snd_rawmidi
snd_seq
snd_seq_device
snd_seq_midi
snd_seq_midi_event
snd_soc_acpi
snd_soc_acpi_intel_match
snd_soc_core
snd_soc_hdac_hda
snd_sof
snd_sof_intel_byt
snd_sof_intel_hda
snd_sof_intel_hda_common
snd_sof_intel_ipc
snd_sof_pci
snd_sof_xtensa_dsp
snd_timer
soundcore
sparse_keymap
syscopyarea
sysfillrect
sysimgblt
thunderbolt
typec
typec_ucsi
ucsi_acpi
uvcvideo
video
videobuf2_common
videobuf2_memops
videobuf2_v4l2
videobuf2_vmalloc
videodev
virt_dma
wmi
wmi_bmof
x86_pkg_temp_thermal
x_tables


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D2/init_pin_configs:
0x05 0x18560010
0x06 0x18560010
0x07 0x18560010

/sys/class/sound/hwC0D2/driver_pin_configs:

/sys/class/sound/hwC0D2/user_pin_configs:

/sys/class/sound/hwC0D2/init_verbs:

/sys/class/sound/hwC0D2/hints:


!!ALSA/HDA dmesg
!!--------------

[    0.280267] ACPI: Added _OSI(Linux-Dell-Video)
[    0.280267] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.280267] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
--
[    3.095060] intel_rapl_common: Found RAPL domain dram
[    3.102260] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
[    3.106473] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    3.130310] iwlwifi 0000:00:14.3: base HW address: 9c:29:76:70:af:da
--
[    3.140341] USB Video Class driver (1.1.1)
[    3.141891] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    3.144609] thermal thermal_zone9: failed to read out thermal zone (-61)
--
[    3.151323] hid-multitouch 0018:0488:120A.0001: input,hidraw0: I2C HID v1.00 Mouse [DELL08AF:00 0488:120A] on i2c-DELL08AF:00
[    3.170838] snd_hda_intel 0000:00:1f.3: Unknown capability 0
[    3.188507] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input18
[    3.188552] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input19
[    3.188591] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input20
[    3.188628] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input21
[    3.188720] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input22
[    3.214397] fbcon: i915drmfb (fb0) is primary device


!!Packages installed
!!--------------------

ii  alsa-topology-conf                         1.2.2-1                               all          ALSA topology configuration files
ii  alsa-ucm-conf                              1.2.2-1ubuntu0.2                      all          ALSA Use Case Manager configuration files
ii  alsa-utils                                 1.2.2-1ubuntu1                        amd64        Utilities for configuring and using ALSA

```

```

harrison@lassen:~$ cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; ls -l /usr/share/pulseaudio/alsa-mixer/paths/; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd; find /lib/modules/`uname -r` | grep snd ;cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; pacmd list-sinks; aplay -l; sudo alsa force-reload; ubuntu-support-status || ubuntu-security-status ; sudo lshw -C sound
Advanced Linux Sound Architecture Driver Version k5.4.0-47-generic.
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0x604b118000 irq 185
  1:        : sequencer
  2: [ 0- 3]: digital audio playback
  3: [ 0- 7]: digital audio playback
  4: [ 0- 8]: digital audio playback
  5: [ 0- 9]: digital audio playback
  6: [ 0-10]: digital audio playback
  7: [ 0- 2]: hardware dependent
  8: [ 0]   : control
 33:        : timer
00-02: HDA Codec 2
00-03: HDMI 0 : HDMI 0 : playback 1
00-07: HDMI 1 : HDMI 1 : playback 1
00-08: HDMI 2 : HDMI 2 : playback 1
00-09: HDMI 3 : HDMI 3 : playback 1
00-10: HDMI 4 : HDMI 4 : playback 1
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
total 176
-rw-r--r-- 1 root root  1415 Aug 13 06:53 analog-input-aux.conf
-rw-r--r-- 1 root root  2056 Aug 13 06:53 analog-input.conf
-rw-r--r-- 1 root root  5769 Aug 13 06:53 analog-input.conf.common
-rw-r--r-- 1 root root  2185 Aug 13 06:53 analog-input-dock-mic.conf
-rw-r--r-- 1 root root  1420 Aug 13 06:53 analog-input-fm.conf
-rw-r--r-- 1 root root  2196 Aug 13 06:53 analog-input-front-mic.conf
-rw-r--r-- 1 root root  2298 Aug 13 06:53 analog-input-headphone-mic.conf
-rw-r--r-- 1 root root  2521 Aug 13 06:53 analog-input-headset-mic.conf
-rw-r--r-- 1 root root  2797 Aug 13 06:53 analog-input-internal-mic-always.conf
-rw-r--r-- 1 root root  3155 Aug 13 06:53 analog-input-internal-mic.conf
-rw-r--r-- 1 root root  2609 Aug 13 06:53 analog-input-linein.conf
-rw-r--r-- 1 root root  2797 Aug 13 06:53 analog-input-mic.conf
-rw-r--r-- 1 root root  1330 Aug 13 06:53 analog-input-mic.conf.common
-rw-r--r-- 1 root root  1457 Aug 13 06:53 analog-input-mic-line.conf
-rw-r--r-- 1 root root  2185 Aug 13 06:53 analog-input-rear-mic.conf
-rw-r--r-- 1 root root  1425 Aug 13 06:53 analog-input-tvtuner.conf
-rw-r--r-- 1 root root  1385 Aug 13 06:53 analog-input-video.conf
-rw-r--r-- 1 root root  1929 Aug 13 06:53 analog-output.conf
-rw-r--r-- 1 root root 11566 Aug 13 06:53 analog-output.conf.common
-rw-r--r-- 1 root root  2139 Aug 13 06:53 analog-output-headphones-2.conf
-rw-r--r-- 1 root root  3339 Aug 13 06:53 analog-output-headphones.conf
-rw-r--r-- 1 root root  3963 Aug 13 06:53 analog-output-lineout.conf
-rw-r--r-- 1 root root  1993 Aug 13 06:53 analog-output-mono.conf
-rw-r--r-- 1 root root  3949 Aug 13 06:53 analog-output-speaker-always.conf
-rw-r--r-- 1 root root  4824 Aug 13 06:53 analog-output-speaker.conf
-rw-r--r-- 1 root root   181 Aug 13 06:53 hdmi-output-0.conf
-rw-r--r-- 1 root root   183 Aug 13 06:53 hdmi-output-1.conf
-rw-r--r-- 1 root root   183 Aug 13 06:53 hdmi-output-2.conf
-rw-r--r-- 1 root root   183 Aug 13 06:53 hdmi-output-3.conf
-rw-r--r-- 1 root root   183 Aug 13 06:53 hdmi-output-4.conf
-rw-r--r-- 1 root root   183 Aug 13 06:53 hdmi-output-5.conf
-rw-r--r-- 1 root root   183 Aug 13 06:53 hdmi-output-6.conf
-rw-r--r-- 1 root root   183 Aug 13 06:53 hdmi-output-7.conf
-rw-r--r-- 1 root root   789 Aug 13 06:53 iec958-stereo-input.conf
-rw-r--r-- 1 root root   712 Aug 13 06:53 iec958-stereo-output.conf
-rw-r--r-- 1 root root  1072 Aug 13 06:53 steelseries-arctis-output-chat-common.conf
-rw-r--r-- 1 root root  1064 Aug 13 06:53 steelseries-arctis-output-game-common.conf
-rw-r--r-- 1 root root  1273 Aug 13 06:53 usb-gaming-headset-input.conf
-rw-r--r-- 1 root root  1262 Aug 13 06:53 usb-gaming-headset-output-mono.conf
-rw-r--r-- 1 root root  1350 Aug 13 06:53 usb-gaming-headset-output-stereo.conf
rm: cannot remove '/etc/asound.conf': No such file or directory
rm: cannot remove '/home/harrison/.pulse': No such file or directory
rm: cannot remove '/home/harrison/.asound*': No such file or directory
rm: cannot remove '/home/harrison/.pulse-cookie': No such file or directory
Hit:1 http://us.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease                                           
Hit:3 http://security.ubuntu.com/ubuntu focal-security InRelease                                            
Ign:4 http://linux.dropbox.com/ubuntu disco InRelease                                                       
Hit:5 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease
Hit:6 http://linux.dropbox.com/ubuntu disco Release
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  aptitude-common libcgi-fast-perl libcgi-pm-perl libclass-accessor-perl libcwidget4 libfcgi-perl libio-string-perl
  libparse-debianchangelog-perl libxapian30
Suggested packages:
  aptitude-doc-en | aptitude-doc apt-xapian-index debtags tasksel libcwidget-dev libhtml-template-perl libxml-simple-perl
  xapian-tools
The following NEW packages will be installed:
  aptitude aptitude-common libcgi-fast-perl libcgi-pm-perl libclass-accessor-perl libcwidget4 libfcgi-perl libio-string-perl
  libparse-debianchangelog-perl libxapian30
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,313 kB of archives.
After this operation, 19.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 aptitude-common all 0.8.12-1ubuntu4 [1,711 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 libcwidget4 amd64 0.5.18-5build1 [306 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 libxapian30 amd64 1.4.14-2 [661 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 aptitude amd64 0.8.12-1ubuntu4 [1,323 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu focal/main amd64 libcgi-pm-perl all 4.46-1 [186 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu focal/main amd64 libfcgi-perl amd64 0.79-1 [33.1 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu focal/main amd64 libcgi-fast-perl all 1:2.15-1 [10.5 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 libclass-accessor-perl all 0.51-1 [21.2 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu focal/main amd64 libio-string-perl all 1.08-3 [11.1 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 libparse-debianchangelog-perl all 1.2.0-13 [49.7 kB]
Fetched 4,313 kB in 1s (6,099 kB/s)                       
Selecting previously unselected package aptitude-common.
(Reading database ... 308254 files and directories currently installed.)
Preparing to unpack .../0-aptitude-common_0.8.12-1ubuntu4_all.deb ...
Unpacking aptitude-common (0.8.12-1ubuntu4) ...
Selecting previously unselected package libcwidget4:amd64.
Preparing to unpack .../1-libcwidget4_0.5.18-5build1_amd64.deb ...
Unpacking libcwidget4:amd64 (0.5.18-5build1) ...
Selecting previously unselected package libxapian30:amd64.
Preparing to unpack .../2-libxapian30_1.4.14-2_amd64.deb ...
Unpacking libxapian30:amd64 (1.4.14-2) ...
Selecting previously unselected package aptitude.
Preparing to unpack .../3-aptitude_0.8.12-1ubuntu4_amd64.deb ...
Unpacking aptitude (0.8.12-1ubuntu4) ...
Selecting previously unselected package libcgi-pm-perl.
Preparing to unpack .../4-libcgi-pm-perl_4.46-1_all.deb ...
Unpacking libcgi-pm-perl (4.46-1) ...
Selecting previously unselected package libfcgi-perl.
Preparing to unpack .../5-libfcgi-perl_0.79-1_amd64.deb ...
Unpacking libfcgi-perl (0.79-1) ...
Selecting previously unselected package libcgi-fast-perl.
Preparing to unpack .../6-libcgi-fast-perl_1%3a2.15-1_all.deb ...
Unpacking libcgi-fast-perl (1:2.15-1) ...
Selecting previously unselected package libclass-accessor-perl.
Preparing to unpack .../7-libclass-accessor-perl_0.51-1_all.deb ...
Unpacking libclass-accessor-perl (0.51-1) ...
Selecting previously unselected package libio-string-perl.
Preparing to unpack .../8-libio-string-perl_1.08-3_all.deb ...
Unpacking libio-string-perl (1.08-3) ...
Selecting previously unselected package libparse-debianchangelog-perl.
Preparing to unpack .../9-libparse-debianchangelog-perl_1.2.0-13_all.deb ...
Unpacking libparse-debianchangelog-perl (1.2.0-13) ...
Setting up libxapian30:amd64 (1.4.14-2) ...
Setting up libcgi-pm-perl (4.46-1) ...
Setting up libio-string-perl (1.08-3) ...
Setting up libcwidget4:amd64 (0.5.18-5build1) ...
Setting up aptitude-common (0.8.12-1ubuntu4) ...
Setting up aptitude (0.8.12-1ubuntu4) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode
Setting up libfcgi-perl (0.79-1) ...
Setting up libclass-accessor-perl (0.51-1) ...
Setting up libcgi-fast-perl (1:2.15-1) ...
Setting up libparse-debianchangelog-perl (1.2.0-13) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9) ...
No candidate version found for paman     
Unable to apply some actions, aborting
H/W path           Device    Class          Description
=======================================================
                             system         Latitude 9510 (0983)
/0                           bus            0G0T42
/0/0                         memory         64KiB BIOS
/0/1c                        memory         16GiB System Memory
/0/1c/0                      memory         8GiB Row of chips LPDDR3 Synchronous 2133 MHz (0.5 ns)
/0/1c/1                      memory         8GiB Row of chips LPDDR3 Synchronous 2133 MHz (0.5 ns)
/0/40                        memory         384KiB L1 cache
/0/41                        memory         1536KiB L2 cache
/0/42                        memory         12MiB L3 cache
/0/43                        processor      Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz
/0/100                       bridge         Intel Corporation
/0/100/2           /dev/fb0  display        Intel Corporation
/0/100/4                     generic        Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
/0/100/8                     generic        Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture 
/0/100/12                    generic        Comet Lake Thermal Subsytem
/0/100/13                    communication  Comet Lake Integrated Sensor Solution
/0/100/14                    bus            Intel Corporation
/0/100/14/0        usb1      bus            xHCI Host Controller
/0/100/14/0/7                multimedia     Integrated_Webcam_HD
/0/100/14/0/a                communication  Bluetooth wireless interface
/0/100/14/1        usb2      bus            xHCI Host Controller
/0/100/14.2                  memory         RAM memory
/0/100/14.3        wlo1      network        Wireless-AC 9462
/0/100/15                    bus            Serial IO I2C Host Controller
/0/100/15.1                  bus            Comet Lake Serial IO I2C Host Controller
/0/100/16                    communication  Comet Lake Management Engine Interface
/0/100/19                    bus            Intel Corporation
/0/100/1c                    bridge         Intel Corporation
/0/100/1c/0                  generic        RTS525A PCI Express Card Reader
/0/100/1d                    bridge         Intel Corporation
/0/100/1d/0                  bridge         JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
/0/100/1d/0/0                bridge         JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
/0/100/1d/0/0/0              generic        JHL7540 Thunderbolt 3 NHI [Titan Ridge 4C 2018]
/0/100/1d/0/1                bridge         JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
/0/100/1d/0/2                bridge         JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
/0/100/1d/0/2/0              bus            JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 4C 2018]
/0/100/1d/0/2/0/0  usb3      bus            xHCI Host Controller
/0/100/1d/0/2/0/1  usb4      bus            xHCI Host Controller
/0/100/1d/0/4                bridge         JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
/0/100/1d.4                  bridge         Intel Corporation
/0/100/1d.4/0                storage        KIOXIA Corporation
/0/100/1f                    bridge         Intel Corporation
/0/100/1f.3                  multimedia     Intel Corporation
/0/100/1f.4                  bus            Intel Corporation
/0/100/1f.5                  bus            Comet Lake SPI (flash) Controller
/0/1                         system         PnP device PNP0c02
/0/2                         system         PnP device PNP0c02
/0/3                         system         PnP device PNP0b00
/0/4                         generic        PnP device INT3f0d
/0/5                         input          PnP device PNP0303
/0/6                         generic        PnP device DLL0983
/0/7                         system         PnP device PNP0c02
/0/8                         system         PnP device PNP0c02
/0/9                         system         PnP device PNP0c02
/0/a                         system         PnP device PNP0c02
/1                           power          DELL 8NFC706
total 0
crw-rw----+  1 root audio 116, 33 Sep 10 16:40 timer
crw-rw----+  1 root audio 116,  1 Sep 10 16:40 seq
crw-rw----+  1 root audio 116,  7 Sep 10 16:40 hwC0D2
crw-rw----+  1 root audio 116,  8 Sep 10 16:40 controlC0
drwxr-xr-x   2 root root       60 Sep 10 16:40 by-path
drwxr-xr-x   3 root root      240 Sep 10 16:40 .
crw-rw----+  1 root audio 116,  2 Sep 10 16:41 pcmC0D3p
crw-rw----+  1 root audio 116,  3 Sep 10 16:41 pcmC0D7p
crw-rw----+  1 root audio 116,  4 Sep 10 16:41 pcmC0D8p
crw-rw----+  1 root audio 116,  5 Sep 10 16:41 pcmC0D9p
crw-rw----+  1 root audio 116,  6 Sep 10 16:41 pcmC0D10p
drwxr-xr-x  20 root root     4960 Sep 10 16:46 ..
/lib/modules/5.4.0-47-generic/kernel/sound/soc/sof/snd-sof-acpi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/sof/snd-sof-pci.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/sof/xtensa/snd-sof-xtensa-dsp.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/sof/intel/snd-sof-intel-byt.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/sof/intel/snd-sof-intel-ipc.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/sof/intel/snd-sof-intel-hda-common.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/sof/intel/snd-sof-intel-hda.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/sof/snd-sof.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/snd-soc-acpi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/amd/snd-soc-acp-da7219mx98357-mach.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/amd/snd-soc-acp-rt5645-mach.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/amd/renoir/snd-acp3x-rn.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/amd/renoir/snd-acp3x-pdm-dma.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/amd/renoir/snd-rn-pci-acp3x.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/amd/raven/snd-acp3x-pcm-dma.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/amd/raven/snd-pci-acp3x.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm3168a-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-max98088.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8741.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-es7241.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs4271-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-da7219.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-inno-rk3036.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm186x.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-sigmadsp.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ssm2602-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8985.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ak5558.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ssm2602-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-hdmi-codec.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic31xx.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs42l51-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ak4118.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8962.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tas5720.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-adau1761.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-mt6358.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-msm8916-analog.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt5663.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tas2552.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm179x-codec.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt298.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8524.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8904.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cx2072x.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-spdif-tx.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt5514.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt286.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-adau7002.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-alc5623.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt5677-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-sigmadsp-regmap.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-adau17x1.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs4271-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm3060-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt5645.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm1789-codec.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm1789-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs35l32.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-adau1761-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-hdac-hdmi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-es7134.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm179x-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs43130.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tscs42xx.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm3168a.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8804.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-es8328-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tas6424.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs42xx8-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ssm2305.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs42l42.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm186x-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt5670.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-max9867.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-es8328-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-es8316.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-gtm601.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-spdif-rx.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tda7419.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tfa9879.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic32x4-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ssm4567.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ak5386.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs42l73.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-adau1761-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm186x-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs42xx8.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-si476x.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs35l35.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-adau-utils.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic32x4.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt5616.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs4271.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs42l51.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-sta350.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm512x.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm3060-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ak4554.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wcd9335.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-da7213.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8804-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt5631.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt5640.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tas5086.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-es8328.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-bd28623.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs4265.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tscs454.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs42l56.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-hdac-hda.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ac97.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-max9860.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-nau8822.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cros-ec-codec.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs42l52.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ak4613.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-nau8810.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-max98090.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs35l36.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-nau8825.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-mt6351.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm512x-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt5660.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8782.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-nau8540.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ak4458.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-bt-sco.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-simple-amplifier.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rk3328.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-max98927.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8804-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-msm8916-digital.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-zx-aud96p22.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-sta32x.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8737.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8974.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rl6347a.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm3168a-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs4341.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs35l34.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-dmic.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt5677.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-sigmadsp-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-max98373.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm3060.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-adau1701.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-max98357a.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt5651.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-sgtl5000.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs53l30.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-max98504.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-uda1334.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs4349.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-cs35l33.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt5514-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8770.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm512x-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm179x-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-nau8824.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-sti-sas.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-ts3a227e.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-max9759.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rl6231.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic32x4-spi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-tas571x.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-rt5682.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/codecs/snd-soc-pcm1681.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/xtensa/snd-soc-xtfpga-i2s.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/xilinx/snd-soc-xlnx-i2s.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/xilinx/snd-soc-xlnx-spdif.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/xilinx/snd-soc-xlnx-formatter-pcm.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/fsl/snd-soc-fsl-audmix.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/fsl/snd-soc-imx-audmux.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/fsl/snd-soc-fsl-ssi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/fsl/snd-soc-fsl-asrc.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/fsl/snd-soc-fsl-micfil.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/fsl/snd-soc-fsl-sai.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/fsl/snd-soc-fsl-esai.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/fsl/snd-soc-fsl-spdif.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/generic/snd-soc-simple-card.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/generic/snd-soc-simple-card-utils.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/haswell/snd-soc-sst-haswell-pcm.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/common/snd-soc-sst-dsp.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/common/snd-soc-sst-acpi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/common/snd-soc-acpi-intel-match.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/common/snd-soc-sst-firmware.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/common/snd-soc-sst-ipc.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-byt-cht-da7213.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-kbl_rt5663_max98927.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-byt-cht-es8316.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-bytcr-rt5651.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-kbl_rt5660.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-rt5645.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-haswell.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-kbl_da7219_max98357a.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-max98090_ti.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-bxt-rt298.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-bytcr-rt5640.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-nau8824.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-glk-rt5682_max98357a.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-byt-cht-cx2072x.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-kbl_da7219_max98927.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sof_rt5682.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-skl_nau88l25_ssm4567.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-skl_nau88l25_max98357a.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-bxt-da7219_max98357a.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-skl_hda_dsp.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-bdw-rt5677-mach.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-kbl_rt5663_rt5514_max98927.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-broadwell.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-skl_rt286.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-rt5672.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/atom/snd-soc-sst-atom-hifi2-platform.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/atom/sst/snd-intel-sst-pci.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/atom/sst/snd-intel-sst-core.ko
/lib/modules/5.4.0-47-generic/kernel/sound/soc/intel/atom/sst/snd-intel-sst-acpi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/5.4.0-47-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/5.4.0-47-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/5.4.0-47-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/5.4.0-47-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/5.4.0-47-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/5.4.0-47-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/hiface/snd-usb-hiface.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/line6/snd-usb-variax.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/line6/snd-usb-toneport.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/line6/snd-usb-line6.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/line6/snd-usb-podhd.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/line6/snd-usb-pod.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/bcd2000/snd-bcd2000.ko
/lib/modules/5.4.0-47-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/5.4.0-47-generic/kernel/sound/x86/snd-hdmi-lpe-audio.ko
/lib/modules/5.4.0-47-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/5.4.0-47-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/5.4.0-47-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/5.4.0-47-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/5.4.0-47-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/5.4.0-47-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/5.4.0-47-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/5.4.0-47-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/5.4.0-47-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/5.4.0-47-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/5.4.0-47-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/5.4.0-47-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/snd-timer.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/snd-compress.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/snd-seq-device.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/snd.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/5.4.0-47-generic/kernel/sound/core/snd-pcm-dmaengine.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-codec-generic.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/5.4.0-47-generic/kernel/sound/firewire/fireworks/snd-fireworks.ko
/lib/modules/5.4.0-47-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/5.4.0-47-generic/kernel/sound/firewire/fireface/snd-fireface.ko
/lib/modules/5.4.0-47-generic/kernel/sound/firewire/tascam/snd-firewire-tascam.ko
/lib/modules/5.4.0-47-generic/kernel/sound/firewire/dice/snd-dice.ko
/lib/modules/5.4.0-47-generic/kernel/sound/firewire/motu/snd-firewire-motu.ko
/lib/modules/5.4.0-47-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/5.4.0-47-generic/kernel/sound/firewire/oxfw/snd-oxfw.ko
/lib/modules/5.4.0-47-generic/kernel/sound/firewire/bebob/snd-bebob.ko
/lib/modules/5.4.0-47-generic/kernel/sound/firewire/digi00x/snd-firewire-digi00x.ko
/lib/modules/5.4.0-47-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/5.4.0-47-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/5.4.0-47-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/5.4.0-47-generic/kernel/sound/hda/ext/snd-hda-ext-core.ko
/lib/modules/5.4.0-47-generic/kernel/sound/hda/snd-intel-dspcfg.ko
/lib/modules/5.4.0-47-generic/kernel/sound/hda/snd-hda-core.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/5.4.0-47-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/5.4.0-47-generic/kernel/sound/xen/snd_xen_front.ko
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:9b51]
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:9bca] (rev 04)
00:04.0 Signal processing controller [1180]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [8086:1903]
00:08.0 System peripheral [0880]: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model [8086:1911]
00:12.0 Signal processing controller [1180]: Intel Corporation Comet Lake Thermal Subsytem [8086:02f9]
00:13.0 Serial controller [0700]: Intel Corporation Comet Lake Integrated Sensor Solution [8086:02fc]
00:14.0 USB controller [0c03]: Intel Corporation Device [8086:02ed]
00:14.2 RAM memory [0500]: Intel Corporation Device [8086:02ef]
00:14.3 Network controller [0280]: Intel Corporation Wireless-AC 9462 [8086:02f0]
00:15.0 Serial bus controller [0c80]: Intel Corporation Serial IO I2C Host Controller [8086:02e8]
00:15.1 Serial bus controller [0c80]: Intel Corporation Comet Lake Serial IO I2C Host Controller [8086:02e9]
00:16.0 Communication controller [0780]: Intel Corporation Comet Lake Management Engine Interface [8086:02e0]
00:19.0 Serial bus controller [0c80]: Intel Corporation Device [8086:02c5]
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:02b8] (rev f0)
00:1d.0 PCI bridge [0604]: Intel Corporation Device [8086:02b0] (rev f0)
00:1d.4 PCI bridge [0604]: Intel Corporation Device [8086:02b4] (rev f0)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:0284]
00:1f.3 Multimedia audio controller [0401]: Intel Corporation Device [8086:02c8]
00:1f.4 SMBus [0c05]: Intel Corporation Device [8086:02a3]
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake SPI (flash) Controller [8086:02a4]
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader [10ec:525a] (rev 01)
02:00.0 PCI bridge [0604]: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018] [8086:15ea] (rev 06)
03:00.0 PCI bridge [0604]: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018] [8086:15ea] (rev 06)
03:01.0 PCI bridge [0604]: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018] [8086:15ea] (rev 06)
03:02.0 PCI bridge [0604]: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018] [8086:15ea] (rev 06)
03:04.0 PCI bridge [0604]: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018] [8086:15ea] (rev 06)
04:00.0 System peripheral [0880]: Intel Corporation JHL7540 Thunderbolt 3 NHI [Titan Ridge 4C 2018] [8086:15eb] (rev 06)
38:00.0 USB controller [0c03]: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 4C 2018] [8086:15ec] (rev 06)
6d:00.0 Non-Volatile memory controller [0108]: KIOXIA Corporation Device [1e0f:0001]
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0c45:6726 Microdia Integrated_Webcam_HD
Bus 001 Device 003: ID 8087:0026 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
/usr/sbin/alsactl
Specified filename /dev/dsp does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  harrison   1353 F.... pulseaudio
dpkg-query: no path found matching pattern *bin/slmodemd*
[    0.000000] x86/fpu: Supporting XSAVE feature 0x008: 'MPX bounds registers'
[    0.015809] No NUMA configuration found
[    0.276101] audit: initializing netlink subsys (disabled)
[    0.276111] audit: type=2000 audit(1599770451.064:1): state=initialized audit_enabled=0 res=1
[    0.280267] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.484718] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.187613] pnp: PnP ACPI: found 10 devices
[    1.419701] tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling instead
[    1.438013] libphy: Fixed MDIO Bus: probed
[    1.440303] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.04
[    1.440469] hub 1-0:1.0: USB hub found
[    1.447089] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.04
[    1.447798] hub 2-0:1.0: USB hub found
[    1.452594] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.04
[    1.452987] hub 3-0:1.0: USB hub found
[    1.454763] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.04
[    1.454994] hub 4-0:1.0: USB hub found
[    1.506505] ima: No architecture policies found
[    1.579976] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    1.639594] wmi_bus wmi_bus-PNP0C14:03: WQBC data block query control method not found
[    1.664452] idma64 idma64.0: Found Intel integrated DMA 64-bit
[    1.904651] idma64 idma64.1: Found Intel integrated DMA 64-bit
[    1.943072] usb 1-7: New USB device found, idVendor=0c45, idProduct=6726, bcdDevice= 1.22
[    2.126081] i2c_hid i2c-DELL08AF:00: i2c-DELL08AF:00 supply vdd not found, using dummy regulator
[    2.126091] i2c_hid i2c-DELL08AF:00: i2c-DELL08AF:00 supply vddl not found, using dummy regulator
[    2.226866] usb 1-10: New USB device found, idVendor=8087, idProduct=0026, bcdDevice= 0.02
[    2.622002] systemd[1]: Created slice system-modprobe.slice.
[    2.622620] systemd[1]: Listening on Journal Audit Socket.
[    2.640651] systemd[1]: modprobe@drm.service: Succeeded.
[    2.643602] lp: driver loaded but no devices found
[    2.913021] uvcvideo: Found UVC 1.00 device Integrated_Webcam_HD (0c45:6726)
[    2.924828] Bluetooth: hci0: Firmware revision 0.0 build 128 week 11 2020
[    2.937793] intel_rapl_common: Found RAPL domain package
[    2.937795] intel_rapl_common: Found RAPL domain dram
[    2.940173] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-50.ucode failed with error -2
[    2.940192] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-49.ucode failed with error -2
[    2.941596] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[    2.941597] iwlwifi 0000:00:14.3: Found debug configuration: 0
[    2.941835] iwlwifi 0000:00:14.3: loaded firmware version 48.4fa0041f.0 op_mode iwlmvm
[    2.973119] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_04.bin (v1.4)
[    2.976710] uvcvideo: Found UVC 1.00 device Integrated_Webcam_HD (0c45:6726)
[    2.984385] iwlwifi 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor.
[    3.095056] intel_rapl_common: Found RAPL domain package
[    3.095058] intel_rapl_common: Found RAPL domain core
[    3.095059] intel_rapl_common: Found RAPL domain uncore
[    3.095060] intel_rapl_common: Found RAPL domain dram
[    3.102260] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
[    3.106473] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    3.141891] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    3.170838] snd_hda_intel 0000:00:1f.3: Unknown capability 0
[    3.188507] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input18
[    3.188552] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input19
[    3.188591] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input20
[    3.188628] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input21
[    3.188720] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input22
[    3.517221] audit: type=1400 audit(1599770454.504:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-xpdfimport" pid=601 comm="apparmor_parser"
[    3.517375] audit: type=1400 audit(1599770454.504:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lsb_release" pid=606 comm="apparmor_parser"
[    3.517918] audit: type=1400 audit(1599770454.504:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=602 comm="apparmor_parser"
[    3.517921] audit: type=1400 audit(1599770454.504:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=602 comm="apparmor_parser"
[    3.517924] audit: type=1400 audit(1599770454.504:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=602 comm="apparmor_parser"
[    3.518128] audit: type=1400 audit(1599770454.504:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=605 comm="apparmor_parser"
[    3.518132] audit: type=1400 audit(1599770454.504:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=605 comm="apparmor_parser"
[    3.518261] audit: type=1400 audit(1599770454.504:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=608 comm="apparmor_parser"
[    3.518688] audit: type=1400 audit(1599770454.504:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="ippusbxd" pid=614 comm="apparmor_parser"
[   23.850911] kauditd_printk_skb: 28 callbacks suppressed
[   23.850912] audit: type=1400 audit(1599770474.836:39): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/snapd/8790/usr/lib/snapd/snap-confine" pid=2554 comm="apparmor_parser"
[   23.851042] audit: type=1400 audit(1599770474.836:40): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/snapd/8790/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=2554 comm="apparmor_parser"
[   24.250998] audit: type=1400 audit(1599770475.236:41): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.snap-store" pid=2557 comm="apparmor_parser"
[   24.257130] audit: type=1400 audit(1599770475.244:42): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.snap-store.ubuntu-software" pid=2562 comm="apparmor_parser"
[   24.257289] audit: type=1400 audit(1599770475.244:43): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.snap-store.ubuntu-software-local-file" pid=2563 comm="apparmor_parser"
[   24.257426] audit: type=1400 audit(1599770475.244:44): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.snap-store.snap-store" pid=2561 comm="apparmor_parser"
[   25.680760] audit: type=1400 audit(1599770476.668:45): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/snap/snapd/8790/usr/lib/snapd/snap-confine" pid=2634 comm="apparmor_parser"
[   25.716535] audit: type=1400 audit(1599770476.708:46): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/snap/snapd/8790/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=2634 comm="apparmor_parser"
[   26.045856] audit: type=1400 audit(1599770477.032:47): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.snap-store" pid=2636 comm="apparmor_parser"
[   26.051819] audit: type=1400 audit(1599770477.036:48): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.snap-store.snap-store" pid=2638 comm="apparmor_parser"
sudo: /etc/init.d/sl-modem-daemon: command not found
/etc/modprobe.d/alsa-base.conf:#options snd-hda-intel model=auto
	Release Date: 07/16/2020
		Serial services are supported (int 14h)
	Manufacturer: Dell Inc.
	Product Name: Latitude 9510
	Serial Number: 8J9XL63
	Manufacturer: Dell Inc.
	Product Name: 0G0T42
	Serial Number: /8J9XL63/CNCMK000950014/
	Manufacturer: Dell Inc.
	Serial Number: 8J9XL63
	Manufacturer: Samsung
	Serial Number: Not Specified
	Module Manufacturer ID: Bank 1, Hex 0xCE
	Module Product ID: Unknown
	Memory Subsystem Controller Manufacturer ID: Unknown
	Memory Subsystem Controller Product ID: Unknown
	Manufacturer: Samsung
	Serial Number: Not Specified
	Module Manufacturer ID: Bank 1, Hex 0xCE
	Module Product ID: Unknown
	Memory Subsystem Controller Manufacturer ID: Unknown
	Memory Subsystem Controller Product ID: Unknown
	Manufacturer: Intel(R) Corporation
	Serial Number:  
	Manufacturer: LG
	Manufacture Date: 06/09/2020
	Serial Number: 807E
		Debug Use USB(Disabled:Serial)
snd_seq_dummy          16384  0
snd_sof_pci            20480  0
snd_sof_intel_hda_common    69632  1 snd_sof_pci
snd_hda_codec_hdmi     61440  1
snd_soc_hdac_hda       24576  1 snd_sof_intel_hda_common
snd_sof_intel_hda      20480  1 snd_sof_intel_hda_common
snd_sof_intel_byt      20480  1 snd_sof_pci
snd_sof_intel_ipc      20480  1 snd_sof_intel_byt
snd_sof               106496  4 snd_sof_pci,snd_sof_intel_hda_common,snd_sof_intel_byt,snd_sof_intel_ipc
snd_sof_xtensa_dsp     16384  1 snd_sof_pci
snd_hda_ext_core       28672  3 snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_soc_acpi_intel_match    32768  2 snd_sof_pci,snd_sof_intel_hda_common
snd_soc_acpi           16384  2 snd_sof_pci,snd_soc_acpi_intel_match
snd_soc_core          245760  3 snd_sof,snd_sof_intel_hda_common,snd_soc_hdac_hda
snd_compress           24576  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hda_intel          53248  1
snd_intel_dspcfg       24576  3 snd_hda_intel,snd_sof_pci,snd_sof_intel_hda_common
snd_hda_codec         131072  3 snd_hda_codec_hdmi,snd_hda_intel,snd_soc_hdac_hda
snd_hda_core           90112  7 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_hwdep              20480  1 snd_hda_codec
ledtrig_audio          16384  2 snd_sof,dell_laptop
snd_pcm               106496  8 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_sof,snd_sof_intel_hda_common,snd_soc_core,snd_hda_core,snd_pcm_dmaengine
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                69632  3 snd_seq_midi,snd_seq_midi_event,snd_seq_dummy
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
btusb                  57344  0
btrtl                  24576  1 btusb
btbcm                  16384  1 btusb
btintel                24576  1 btusb
bluetooth             581632  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
snd                    90112  13 snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
1 sink(s) available.
  * index: 0
	name: <auto_null>
	driver: <module-null-sink.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE
	priority: 1000
	volume: front-left: 41944 /  64% / -11.63 dB,   front-right: 41944 /  64% / -11.63 dB
	        balance 0.00
	base volume: 65536 / 100% / 0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max request: 344 KiB
	max rewind: 344 KiB
	monitor source: 0
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
	module: 14
	properties:
		device.description = "Dummy Output"
		device.class = "abstract"
		device.icon_name = "audio-card"
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Unloading ALSA sound driver modules: snd-seq-dummy snd-sof-pci snd-sof-intel-hda-common snd-hda-codec-hdmi snd-soc-hdac-hda snd-sof-intel-hda snd-sof-intel-byt snd-sof-intel-ipc snd-sof snd-sof-xtensa-dsp snd-hda-ext-core snd-soc-acpi-intel-match snd-soc-acpi snd-soc-core snd-compress snd-pcm-dmaengine snd-hda-intel snd-intel-dspcfg snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-intel snd-intel-dspcfg snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer).
Loading ALSA sound driver modules: snd-seq-dummy snd-sof-pci snd-sof-intel-hda-common snd-hda-codec-hdmi snd-soc-hdac-hda snd-sof-intel-hda snd-sof-intel-byt snd-sof-intel-ipc snd-sof snd-sof-xtensa-dsp snd-hda-ext-core snd-soc-acpi-intel-match snd-soc-acpi snd-soc-core snd-compress snd-pcm-dmaengine snd-hda-intel snd-intel-dspcfg snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.
ubuntu-support-status: command not found
1918 packages installed, of which:
1676 receive package updates with LTS until 4/2025
 239 could receive security updates with ESM Apps until 4/2030
   1 package is from a third party
   2 packages are no longer available for download

Packages from third parties are not provided by the official Ubuntu
archive, for example packages from Personal Package Archives in
Launchpad.
For more information on the packages, run 'ubuntu-security-status
--thirdparty'.

Packages that are not available for download may be left over from a
previous release of Ubuntu, may have been installed directly from a
.deb file, or are from a source which has been disabled.
For more information on the packages, run 'ubuntu-security-status
--unavailable'.

Enable Extended Security Maintenance (ESM Apps) to get 0 security
updates (so far) and enable coverage of 239 packages.

This machine is not attached to an Ubuntu Advantage subscription.
See https://ubuntu.com/advantage
  *-usb:0                   
       description: Video
       product: Integrated_Webcam_HD
       vendor: CN049KJV8LG00056B3XJA00
       physical id: 7
       bus info: usb@1:7
       version: 1.22
       capabilities: usb-2.01
       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
  *-multimedia
       description: Multimedia audio controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1f.3
       bus info: pci@0000:00:1f.3
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=32
       resources: iomemory:600-5ff iomemory:600-5ff irq:185 memory:604b118000-604b11bfff memory:604b000000-604b0fffff

```

7) Possibly relevant but input is also not found

Any ideas would be appreciated!

---

### Post by DrIdiot on 2020-09-12
(deleted)

---

### Post by DrIdiot on 2020-09-12
I cross-posted here:
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/692857](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/692857)

I think I can refine the problem a little bit. ALSA/Pulseaudio is only detecting the HDMI output on my sound card, but not the analog output. I tried running

harrison@lassen:~$ pactl load-module module-detect
Failure: Module initialization failed

When I plug an HDMI output into the laptop, the sound will play from there, which confirms this.  Only these outputs appear on alsamixer.
[https://drive.google.com/drive/folders/1MCPBKK7YsEH8hwoBNiTQQ8ckO-5u6J1A?usp=sharing](https://drive.google.com/drive/folders/1MCPBKK7YsEH8hwoBNiTQQ8ckO-5u6J1A?usp=sharing)

When I ran pactl list it gave the following output (the audio output is suspended?)
```



Sink #1
 State: SUSPENDED
 Name: alsa_output.pci-0000_00_1f.3.hdmi-stereo-extra1
 Description: Built-in Audio Digital Stereo (HDMI 2)
 Driver: module-alsa-card.c
 Sample Specification: s16le 2ch 44100Hz
 Channel Map: front-left,front-right
 Owner Module: 7
 Mute: no
 Volume: front-left: 65733 / 100% / 0.08 dB, front-right: 65733 / 100% / 0.08 dB
         balance 0.00
 Base Volume: 65536 / 100% / 0.00 dB
 Monitor Source: alsa_output.pci-0000_00_1f.3.hdmi-stereo-extra1.monitor
 Latency: 0 usec, configured 0 usec
 Flags: HARDWARE DECIBEL_VOLUME LATENCY SET_FORMATS
 Properties:
  alsa.resolution_bits = "16"
  device.api = "alsa"
  device.class = "sound"
  alsa.class = "generic"
  alsa.subclass = "generic-mix"
  alsa.name = "HDMI 1"
  alsa.id = "HDMI 1"
  alsa.subdevice = "0"
  alsa.subdevice_name = "subdevice #0"
  alsa.device = "7"
  alsa.card = "0"
  alsa.card_name = "HDA Intel PCH"
  alsa.long_card_name = "HDA Intel PCH at 0x604b118000 irq 185"
  alsa.driver_name = "snd_hda_intel"
  device.bus_path = "pci-0000:00:1f.3"
  sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
  device.bus = "pci"
  device.vendor.id = "8086"
  device.vendor.name = "Intel Corporation"
  device.product.id = "02c8"
  device.form_factor = "internal"
  device.string = "hdmi:0,1"
  device.buffering.buffer_size = "65536"
  device.buffering.fragment_size = "32768"
  device.access_mode = "mmap+timer"
  device.profile.name = "hdmi-stereo-extra1"
  device.profile.description = "Digital Stereo (HDMI 2)"
  device.description = "Built-in Audio Digital Stereo (HDMI 2)"
  module-udev-detect.discovered = "1"
  device.icon_name = "audio-card-pci"
 Ports:
  hdmi-output-1: HDMI / DisplayPort 2 (priority: 5800, available)
 Active Port: hdmi-output-1
 Formats:
  pcm

Source #1
 State: SUSPENDED
 Name: alsa_output.pci-0000_00_1f.3.hdmi-stereo-extra1.monitor
 Description: Monitor of Built-in Audio Digital Stereo (HDMI 2)
 Driver: module-alsa-card.c
 Sample Specification: s16le 2ch 44100Hz
 Channel Map: front-left,front-right
 Owner Module: 7
 Mute: no
 Volume: front-left: 65536 / 100% / 0.00 dB, front-right: 65536 / 100% / 0.00 dB
         balance 0.00
 Base Volume: 65536 / 100% / 0.00 dB
 Monitor of Sink: alsa_output.pci-0000_00_1f.3.hdmi-stereo-extra1
 Latency: 0 usec, configured 0 usec
 Flags: DECIBEL_VOLUME LATENCY
 Properties:
  device.description = "Monitor of Built-in Audio Digital Stereo (HDMI 2)"
  device.class = "monitor"
  alsa.card = "0"
  alsa.card_name = "HDA Intel PCH"
  alsa.long_card_name = "HDA Intel PCH at 0x604b118000 irq 185"
  alsa.driver_name = "snd_hda_intel"
  device.bus_path = "pci-0000:00:1f.3"
  sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
  device.bus = "pci"
  device.vendor.id = "8086"
  device.vendor.name = "Intel Corporation"
  device.product.id = "02c8"
  device.form_factor = "internal"
  device.string = "0"
  module-udev-detect.discovered = "1"
  device.icon_name = "audio-card-pci"
 Formats:
  pcm

```

---

### Post by DrIdiot on 2020-09-12
There's something that's confusing me now. The specs for this laptop (which I confirmed using the serial number):
[https://topics-cdn.dell.com/pdf/latitude-15-9510-2-in-1-laptop_owners-manual5_en-us.pdf](https://topics-cdn.dell.com/pdf/latitude-15-9510-2-in-1-laptop_owners-manual5_en-us.pdf)
say the audio controller and speakers are supposed to be
 Realtek ALC711-CG (controller)
 Realtek ALC1309D (speaker)

However, I'm only finding two devices:
 Intel Kabylake HDMI (0806:280b)
 Multimedia audio controller (0806:02c8)

I suppose this could mean either it's using the wrong driver (i.e. cannot properly detect the device) or the above two are some other devices on the motherboard and the audio card is not being detected. Anyway, I feel like I'm narrowing the problem down a bit but still not sure what to do...

---

### Post by Yellow Pasque on 2020-09-13
Unfortunately, there does not seem to be a quick fix:
Similar Comet Lake "cAVS" chipset audio device with Realtek 711/1308 on Dell: [https://bugzilla.opensuse.org/show_bug.cgi?id=1176200](https://bugzilla.opensuse.org/show_bug.cgi?id=1176200)

> say the audio controller and speakers are supposed to be
Realtek ALC711-CG (controller)
Realtek ALC1309D (speaker)

However, I'm only finding two devices:
Intel Kabylake HDMI (0806:280b)
Multimedia audio controller (0806:02c8)

The PCI ID does not list the codec name. For example, my motherboard has Realtek ALC1220 codec, but it is listed as: 
"Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller"

> the audio output is suspended?

That is your HDMI audio. If nothing is using it, "suspended" would make sense, especially if you're not using an external monitor.

---

### Post by webgrafia on 2020-09-14
Exactly my same problem!

---

### Post by m4nu85 on 2020-09-16
Hello,

Having trouble with the internal microphone?


In my DELL with Ubuntu 20.04 installed, it does not detect the microphone

Please, have some fix or solutions?

---

### Post by gohrner on 2020-10-16
I just ran into a very similar sounding issue after my recent Ubuntu upgrade (from 18.04 to 20.04).

In my case, it was caused by timidity - who would have guessed or expected that?!?

I found a hint here: [https://askubuntu.com/a/1234906](https://askubuntu.com/a/1234906)

There are also some (surprisingly old) bugs on Launchpad discussing this, like [https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/1793640](https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/1793640) - so apparently it was introduced in Ubuntu 18.10 and still hasn't been fixed properly. Apparently, timidity is poorly maintained, and fortunately probably not necessary for the majority of users...

For those for whom it is, some workaround seem to exist, mentioned in the referenced bug and further reading, which I haven't tested so far.


(Note that the OP seems to have a different issue, but maybe some of the other commenters here who experience "the same" symptoms are affected by the timidity issue.)

---

