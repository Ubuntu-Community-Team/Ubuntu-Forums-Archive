---
title: "Asus K53U-SX071D without sound"
date: 2012-01-21
forum: Hardware
---

### Post by Wowo1050 on 2012-01-21
Hello,

last week I got the Asus and installed Lubuntu 11.10

Everything works fine except for the sound.

The following chip makes problems:

"ATI SBx00 Azalia (Intel HDA)"

Surprisingly, the driver is installed...

How can I solve it?

---

### Post by marinara on 2012-01-22
What is the error, please?

---

### Post by Wowo1050 on 2012-01-22
Code:
wowo@wowo-K53U:~$ sudo hwinfo --sound 
> hal.1: read hal dataprocess 3591: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280. 
This is normally a bug in some application using the D-Bus library. 
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files 
10: PCI 01.1: 0403 Audio device                                  
  [Created at pci.318] 
  Unique ID: mnDB.B0GU5m+GLk2 
  SysFS ID: /devices/pci0000:00/0000:00:01.1 
  SysFS BusID: 0000:00:01.1 
  Hardware Class: sound 
  Model: "ATI Audio device" 
  Vendor: pci 0x1002 "ATI Technologies Inc" 
  Device: pci 0x1314 
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc." 
  SubDevice: pci 0x104c 
  Driver: "HDA Intel" 
  Driver Modules: "snd_hda_intel" 
  Memory Range: 0xfeb44000-0xfeb47fff (rw,non-prefetchable) 
  IRQ: 42 (31 events) 
  Module Alias: "pci:v00001002d00001314sv00001043sd0000104Cbc04sc03i00" 
  Driver Info #0: 
    Driver Status: snd_hda_intel is active 
    Driver Activation Cmd: "modprobe snd_hda_intel" 
  Config Status: cfg=new, avail=yes, need=no, active=unknown 

19: PCI 14.2: 0403 Audio device 
  [Created at pci.318] 
  Unique ID: 5Dex.A+ePiMTMSY6 
  SysFS ID: /devices/pci0000:00/0000:00:14.2 
  SysFS BusID: 0000:00:14.2 
  Hardware Class: sound 
  Model: "ATI SBx00 Azalia (Intel HDA)" 
  Vendor: pci 0x1002 "ATI Technologies Inc" 
  Device: pci 0x4383 "SBx00 Azalia (Intel HDA)" 
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc." 
  SubDevice: pci 0x104c 
  Revision: 0x40 
  Driver: "HDA Intel" 
  Driver Modules: "snd_hda_intel" 
  Memory Range: 0xfeb40000-0xfeb43fff (rw,non-prefetchable) 
  IRQ: 16 (379 events) 
  Module Alias: "pci:v00001002d00004383sv00001043sd0000104Cbc04sc03i00" 
  Driver Info #0: 
    Driver Status: snd_hda_intel is active 
    Driver Activation Cmd: "modprobe snd_hda_intel" 
  Config Status: cfg=new, avail=yes, need=no, active=unknown"

---

### Post by Wowo1050 on 2012-01-22
P.S.:

What I want to add:

I tried Linux Mint 12 on it, and the sound worked perfectly.

---

### Post by Wowo1050 on 2012-01-23
Is it impossible? :-(:-(:-(:-(

---

### Post by Wowo1050 on 2012-01-23
Is it really impossible to solve? :oops:

---

### Post by Wowo1050 on 2012-01-24
I cannot believe that there is no help possible...:cry:

---

### Post by Perfect Storm on 2012-01-25
Moved to Hardware section. Properly the asus support forum is less crowded.

---

### Post by Wowo1050 on 2012-01-25
Oh, now I saw it.

I cannot believe that there is no solution here...:frown:

---

### Post by MoreOrLess on 2012-01-25
Did you check that nothing was muted in alsamixer?
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Wowo1050 on 2012-01-25
> **MoreOrLess said:**
> Did you check that nothing was muted in alsamixer?
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Do you think it might work then? :?

---

### Post by MoreOrLess on 2012-01-25
Is that a yes or no? Also, you didn't post the link to your info...

---

### Post by Wowo1050 on 2012-01-26
Hallo,

it does not work, look:


wowo@wowo-K53U:~$ bash
wowo@wowo-K53U:~$ cd ~/
wowo@wowo-K53U:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -0 alsa-info.sh && bash alsa-info.sh
wget: Ungültige Option -- 0
Syntax: wget [OPTION]... [URL]...

»wget --help« gibt weitere Informationen.


What do you mean by a link?

---

### Post by Wowo1050 on 2012-01-26
What I want to add:

The sound icon does not appear on the panel!!

---

### Post by Wowo1050 on 2012-01-26
Am I the only one with this laptop and Lubuntu on this planet?

---

### Post by MoreOrLess on 2012-01-26
Try again: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

I want the link to your info that the script gives you, not a repost of commands you use to get the info. I'm not sure how to make it clearer..

---

### Post by Wowo1050 on 2012-01-26
I pressed Alt+F2, entered bash, and the terminal disappeared....

---

### Post by MoreOrLess on 2012-01-26
I have no idea what you're doing. I don't think I can help you.

---

### Post by Wowo1050 on 2012-01-27
It worked now.
I got the following files and send the content now.

1st file "alsacards.tmp"

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeb44000 irq 41
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfeb40000 irq 16

---

### Post by Wowo1050 on 2012-01-27
2ND file "alsactl.tmp"


state.Generic {
	control.1 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
}
state.SB {
	control.1 {
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
	control.2 {
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
	control.3 {
		iface MIXER
		name 'Headphone Playback Volume'
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
		name 'Headphone Playback Switch'
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
		name 'Internal Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3600
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.7 {
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
			dbmax 3600
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.8 {
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
	control.9 {
		iface MIXER
		name 'Capture Volume'
		value.0 19
		value.1 19
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -1650
			dbmax 3000
			dbvalue.0 1200
			dbvalue.1 1200
		}
	}
	control.10 {
		iface MIXER
		name 'Master Playback Volume'
		value 60
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 -2025
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
}

---

### Post by Wowo1050 on 2012-01-27
3rd file "alsa-hda-intel"


Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x02
Codec: Realtek ALC269VB
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0269
Subsystem Id: 0x1043104c
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC269VB Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x8b 0x8b]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC269VB Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x13 0x13]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x18 0x19 0x1a 0x1b 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x00]
  Connection: 2
     0x02 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x40000b: Stereo Amp-In
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x99a30920: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x16 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x17 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00001734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x04a11830: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=08, enabled=1
  Connection: 1
     0x0d
Node 0x19 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40079a2d: [N/A] Line Out at Ext N/A
    Conn = Analog, Color = Pink
    DefAssociation = 0x2, Sequence = 0xd
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=25
Node 0x21 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0421101f: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 2
     0x0c 0x0d*
Node 0x22 [Audio Selector] wcaps 0x30010b: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Connection: 7
     0x18 0x19 0x1a 0x1b 0x1d 0x0b 0x12*
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b

---

### Post by Wowo1050 on 2012-01-27
4th file "alsa-info.txt"


upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Fri Jan 27 10:40:30 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 11.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.10"


!!DMI Information
!!---------------

Manufacturer:      ASUSTeK Computer Inc.
Product Name:      K53U 
Product Version:   1.0


!!Kernel Information
!!------------------

Kernel release:    3.0.0-15-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         athlon
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeb44000 irq 41
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfeb40000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:01.1 Audio device: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310]
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:01.1 0403: 1002:1314
	Subsystem: 1043:104c
--
00:14.2 0403: 1002:4383 (rev 40)
	Subsystem: 1043:104c


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 1
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 1
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x02
Codec: Realtek ALC269VB
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0269
Subsystem Id: 0x1043104c
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC269VB Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x8b 0x8b]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC269VB Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x13 0x13]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x18 0x19 0x1a 0x1b 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x00]
  Connection: 2
     0x02 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x40000b: Stereo Amp-In
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x99a30920: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x16 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x17 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00001734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x04a11830: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=08, enabled=1
  Connection: 1
     0x0d
Node 0x19 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40079a2d: [N/A] Line Out at Ext N/A
    Conn = Analog, Color = Pink
    DefAssociation = 0x2, Sequence = 0xd
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=25
Node 0x21 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0421101f: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 2
     0x0c 0x0d*
Node 0x22 [Audio Selector] wcaps 0x30010b: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Connection: 7
     0x18 0x19 0x1a 0x1b 0x1d 0x0b 0x12*
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  4 Jan 27 11:33 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  8 Jan 27 11:33 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  3 Jan 27 11:33 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  7 Jan 27 11:33 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  2 Jan 27 11:33 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  6 Jan 27 11:33 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  5 Jan 27 11:33 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  1 Jan 27 11:33 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jan 27 11:33 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Jan 27 11:33 .
drwxr-xr-x 3 root root 240 Jan 27 11:33 ..
lrwxrwxrwx 1 root root  12 Jan 27 11:33 pci-0000:00:01.1 -> ../controlC0
lrwxrwxrwx 1 root root  12 Jan 27 11:33 pci-0000:00:14.2 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: SB [HDA ATI SB], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Generic]

Card hw:0 'Generic'/'HD-Audio Generic at 0xfeb44000 irq 41'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100200'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [SB]

Card hw:1 'SB'/'HDA ATI SB at 0xfeb40000 irq 16'
  Mixer name	: 'Realtek ALC269VB'
  Components	: 'HDA:10ec0269,1043104c,00100100'
  Controls      : 11
  Simple ctrls  : 7
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 60 [69%] [-20.25dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 19 [61%] [12.00dB] [on]
  Front Right: Capture 19 [61%] [12.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]


!!Alsactl output
!!-------------

--startcollapse--
state.Generic {
	control.1 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
}
state.SB {
	control.1 {
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
	control.2 {
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
	control.3 {
		iface MIXER
		name 'Headphone Playback Volume'
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
		name 'Headphone Playback Switch'
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
		name 'Internal Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3600
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.7 {
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
			dbmax 3600
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.8 {
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
	control.9 {
		iface MIXER
		name 'Capture Volume'
		value.0 19
		value.1 19
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -1650
			dbmax 3000
			dbvalue.0 1200
			dbvalue.1 1200
		}
	}
	control.10 {
		iface MIXER
		name 'Master Playback Volume'
		value 60
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 -2025
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
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
bnep
bluetooth
parport_pc
ppdev
vesafb
snd_hda_codec_realtek
snd_hda_codec_hdmi
arc4
ath9k
snd_hda_intel
mac80211
snd_hda_codec
snd_hwdep
ath9k_common
ath9k_hw
snd_pcm
uvcvideo
videodev
snd_seq_midi
snd_rawmidi
ath
joydev
snd_seq_midi_event
fglrx
sp5100_tco
snd_seq
cfg80211
snd_timer
asus_nb_wmi
asus_wmi
sparse_keymap
psmouse
serio_raw
snd_seq_device
i2c_piix4
snd
k10temp
video
soundcore
snd_page_alloc
wmi
lp
parport
ums_realtek
usb_storage
uas
r8169
pata_atiixp
ahci
libahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x12 0x99a30920
0x14 0x99130110
0x17 0x411111f0
0x18 0x04a11830
0x19 0x411111f0
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x40079a2d
0x1e 0x411111f0
0x21 0x0421101f

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   10.550769] USB Video Class driver (v1.1.0)
[   11.053061] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   11.053174] HDA Intel 0000:00:01.1: irq 41 for MSI/MSI-X
[   11.053226] HDA Intel 0000:00:01.1: setting latency timer to 64
[   11.079199] ath9k 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
--
[   11.186627] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8140000, irq=17
[   11.415300] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   11.415580] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input9
[   11.416153] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.585398] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
--
[   11.585459] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.937934] hda_codec: ALC269VB: BIOS auto-probing.
[   11.947804] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input10
[   11.947996] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input11
[   12.693784] type=1400 audit(1327660435.020:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=548 comm="apparmor_parser"

---

### Post by Wowo1050 on 2012-01-27
5th file "alsamodules.tmp"

snd_hda_intel
snd_hda_intel

---

### Post by Wowo1050 on 2012-01-27
6th file "device_id.tmp"


1314
4383

---

### Post by Wowo1050 on 2012-01-27
7th file "lspci.tmp"

00:01.1 Audio device: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310]
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

---

### Post by Wowo1050 on 2012-01-27
7th file "vendor_id.tmp"

1002
1002

---

### Post by Wowo1050 on 2012-01-27
Anything to get out of it?

---

### Post by Wowo1050 on 2012-01-27
useless?

---

### Post by GregA on 2012-01-28
Of course it's not useless.   You already know sound works in Linux, for your specific laptop, if using Mint 12.

So,, two things to do: 

1.   Use your live Mint media (cd or flash stick), start the desktop, and open a Terminal.  Just type "alsamixer", and take a screen capture of the settings.   Save the file to external media (flash, SD card, etc.).

2.   Do the same as step 1 but using (Ubuntu or Lubuntu?). 

Then print the two files (landscape mode, to enhance readability).   Compare the two and note which settings you need to change. 

Most of the time it's one of the settings being incorrect (muted, or even the opposite - open, when the setting should be mute).

Be sure you read how to navigate and change the settings before you start.

Also, check to see if you have the same version of "alsa" installed in Ubuntu as in Mint.

---

### Post by Wowo1050 on 2012-01-28
Many thanks for the answer.
For I am a layman, a friend of mine will help me next month. I will post the result then here.

But even as a layman I, too, believe that it must be a small problem, because Mint und Lubuntu architecture is same.

---

### Post by GregA on 2012-01-28
Herr Wowo:

Many times, just one small adjustment can make fix the issue.   

See the below info (from Alsa forum):
...........................................
My ALSA modules seem to be loaded fine but I hear no sound. Why's that?

"Play around with alsamixer. The relevant audio channels are probably just muted and/or set to zero or a very quiet volume-level.

On some platforms, particularly the IBM Thinkpad T40 series, [COLOR="Magenta"]_the Headphone Jack and/or Line Jack inputs need to be muted in order to hear sound at all._[/COLOR] The alsamixer app can do this for you by using the 'm' toggle to mute/unmute. On my system the Headphone Jack appears as the 4th control from the left and is titled "Headphon", the same as the title for the 3rd control (the title is truncated). 
............................................

As another poster said, "play around" with the alsamixer settings, especially noting what is muted . . .

Remember, you can do this with a Live CD, and there is no risk to you for damaging your laptop.

---

### Post by MoreOrLess on 2012-01-28
Sorry for my eariler impatience :\ 

> because Mint and Lubuntu architecture is same.
In this case, there is a difference. Mint uses pulseaudio sound server, while Lubuntu does not. Pulseaudio makes it easier to select an output device (when it works).

One thing I see is that the HDMI audio (the audio chip built into the GPU) has index 0. To change that is a bit complicated since both devices use the snd-hda-intel driver. See: [http://alsa.opensrc.org/MultipleCards#Ordering_multiple_cards_of_the_same_type](http://alsa.opensrc.org/MultipleCards#Ordering_multiple_cards_of_the_same_type)

You can test the internal card by sending sound directly to it with aplay (WARNING: may be loud if you don't adjust volume with alsamixer).
```
aplay -Dhw:1,0 /usr/share/sounds/alsa/Fornt_left.wav
```

If you can't figure it out and you're sure you don't need the HDMI audio, we can also blacklist the snd-hda-codec-hdmi module.

---

### Post by MoreOrLess on 2012-01-28
> **GregA said:**
> Play around with alsamixer
Note: The OP will have to select a different sound card using F6 because the HDMI audio is default.

---

### Post by Wowo1050 on 2012-01-28
@ MoreOrLess

the code "aplay -Dhw:1,0 /usr/share/sounds/alsa/Fornt_left.wav" does not work.
"file or program not found"

---

### Post by MoreOrLess on 2012-01-28
> **Wowo1050 said:**
> "file or program not found"

There was a typo in the command (Fornt should be Front).

---

### Post by Wowo1050 on 2012-01-28
space between "aplay" and "-Dhw"?

Doesn't work either...

---

### Post by MoreOrLess on 2012-01-28
Ok. Try blacklisting the HDMI.
Create a file in /etc/modprobe.d/ like so (I'm assuming leafpad is your text editor).
```
sudo leafpad /etc/modprobe.d/blacklist_hdmi.conf
```
Copy/paste this line into the file:
```
blacklist snd_hda_codec_hdmi
```
Save/quit, and then run:
```
sudo depmod -a
```
Reboot and pray. If no sound, post output of this to verify the blacklist:
```
aplay -l
```

---

### Post by Wowo1050 on 2012-02-05
Nothing works. The following appears when I try to start the alsaplayer:

---

### Post by Wowo1050 on 2012-02-07
Seems I have to give up.

---

### Post by Wowo1050 on 2012-02-08
Hard to believe that nowhere in this world there is any help for a laptop that has sound under Mint but not under Lubuntu...

:confused:

---

### Post by Wowo1050 on 2012-02-09
Is it really sooooooooo difficult for professionals to find a solution for a laptop that has sound with Linux Mint??

---

### Post by MoreOrLess on 2012-02-09
> **Wowo1050 said:**
> Is it really sooooooooo difficult for professionals to find a solution for a laptop that has sound with Linux Mint??
Professional? I haven't seen one payment yet... (this is a user forum, not launchpad).

Also, can you post your alsa-info again (just the alsainfo.txt and use [ code ][ /code ])? I want to make sure you've blacklisted the HDMI so it's not the default device.

---

### Post by Wowo1050 on 2012-02-09
> **MoreOrLess said:**
> Professional? I haven't seen one payment yet... (this is a user forum, not launchpad).

Also, can you post your alsa-info again (just the alsainfo.txt and use [ code ][ /code ])? I want to make sure you've blacklisted the HDMI so it's not the default device.


If sound works, I will pay you.

---

### Post by Wowo1050 on 2012-02-09
what code exactly?

What do I have to write into the terminal?

---

### Post by Wowo1050 on 2012-02-10
put in front again...

---

### Post by Wowo1050 on 2012-02-11
My laptop has sound with Linux Mint 12, Ubuntu 11.10 AND Xubuntu!

Just not with Lubuntu. Soon I will get crazy.

---

### Post by Wowo1050 on 2012-02-12
to the start.

---

### Post by MoreOrLess on 2012-02-12
You still haven't re-posted the alsa-info and please don't bump more than once a day..

---

### Post by Wowo1050 on 2012-02-13
Please tell me exactly what I have to write into the terminal. step by step.

thanks.

---

### Post by MoreOrLess on 2012-02-13
You already did it earlier in the thread.. [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Wowo1050 on 2012-02-14
here you are:


wowo@wowo-K53U:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2012-02-14 09:51:17--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Auflösen des Hostnamen »[www.alsa-project.org«](www.alsa-project.org«)... 77.48.224.243
Verbindungsaufbau zu [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... verbunden.
HTTP-Anforderung gesendet, warte auf Antwort... 302 Found
Platz: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [folge]
--2012-02-14 09:51:21--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Auflösen des Hostnamen »git.alsa-project.org«... 77.48.224.243
Wiederverwendung der bestehenden Verbindung zu [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP-Anforderung gesendet, warte auf Antwort... 200 OK
Länge: nicht spezifiziert [text/plain]
In »»alsa-info.sh«« speichern.

    [  <=>                                  ] 27.247      98,1K/s   in 0,3s    

2012-02-14 09:51:21 (98,1 KB/s) - »»alsa-info.sh«« gespeichert [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

---

### Post by MoreOrLess on 2012-02-14
Sigh... I'm sorry, but I don't have enough patience to help you. Keep bumping the thread, and maybe someone will help..

---

### Post by Wowo1050 on 2012-02-14
> **MoreOrLess said:**
> Sigh... I'm sorry, but I don't have enough patience to help you. Keep bumping the thread, and maybe someone will help..

no patience?

not good.

---

### Post by Wowo1050 on 2012-02-15
Well, when I see how few problems get solved here, I assume that your patience is generally exhausted quite easily.

---

### Post by roybellingan on 2012-03-31
alt + f2 
and enter

sudo leafpad /etc/modprobe.d/alsa-base.conf 

search a line who reads

# Prevent abnormal drivers from grabbing index 0

and add a new line with 

options snd_hda_codec_hdmi=-2


Congrats, now your first audio card is the one that works..!
(or in another words you have changed your default sound card)

---

