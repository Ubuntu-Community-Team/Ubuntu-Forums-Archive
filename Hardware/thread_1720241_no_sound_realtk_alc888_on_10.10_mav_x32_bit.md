---
title: "no sound realtk alc888 on 10.10 mav x32 bit"
date: 2011-04-03
forum: Hardware
---

### Post by uveryames on 2011-04-03
problem: no sound from headphone jack/speakers. 

gnome alsa mixer has everything unmuted. my laptop is custom and is not brand name. had it put together from cyberpowerpc.com

is this a pulse audio problem?  or something else? any help would be awesome this is sooo annoying.  im trying to make the complete switch to ubuntu and this is one of my main hang ups.

ty in advance! 


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
uveryames@uveryames:~$ 
_________________________________

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
________

thanks in advance!

---

### Post by lidex on 2011-04-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by uveryames on 2011-04-03
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
Vendor: Phoenix Technologies LTD
Version: 1.0A-0004-0022 
Release Date: 05/21/2009
Address: 0xE57A0
Runtime Size: 108640 bytes
ROM Size: 1536 kB
Characteristics:
ISA is supported
PCI is supported
PC Card (PCMCIA) is supported
PNP is supported
BIOS is upgradeable
BIOS shadowing is allowed
ESCD support is available
Boot from CD is supported
ACPI is supported
USB legacy is supported
AGP is supported
BIOS boot specification is supported
Targeted content distribution is supported

Invalid entry length (0). DMI table is broken! Stop.

sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0002, DMI type 2, 17 bytes
Base Board Information
Manufacturer: Intel Corporation
Product Name: Montevina CRB
Version: Not Applicable
Serial Number: Not Applicable
Asset Tag: Tag 12345
Features:
Board is a hosting board
Board is replaceable
Location In Chassis: Not Applicable
Chassis Handle: 0x0003
Type: Motherboard
Contained Object Handles: 1
0x0000

Handle 0x0011, DMI type 10, 6 bytes
On Board Device Information
Type: Sound
Status: Disabled
Description: HD-Audio

Invalid entry length (0). DMI table is broken! Stop.
_________

as far as the alsa script info. i dont know how to provide a "link" to upload it to. the option i receive is "would you like to upload info to alsa-project.org [Y/N]. i hit yes and it doesnt come back with a link. so how do i provide you with one? 

i found the alsa info file that has all my info..what is the best way to copy/paste that or get it uploaded here so u can view it.  the File: /tmp/alsa-info.txt.xOTlPH1lHU  

thank you so much

---

### Post by DanneStrat on 2011-04-05
Hi!

I will see if I can help you out.

Try this:

Open "alsa-base.conf" by doing this in

terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```


Now add these two lines to the end of the file:

```
alias snd-card-0 snd-hda-intel

options snd-hda-intel model=auto
```


Then save the file(file > save)

Reboot the computer.

Now check if you get sound.

---

### Post by uveryames on 2011-04-05
OK i added the 2 lines and no beans still :/ 

thank you anyways!  

speakers are unmuted in alsamixer and the volume is at 100.  im puzzled

---

### Post by lidex on 2011-04-05
Still waiting on that alsa-info output. When you run it this time key in <Y> at the prompt and press enter and make sure you remove any edits from alsa-base.conf and reset alsa first:
```
sudo alsa force-reload
```

---

### Post by uveryames on 2011-04-06
sorry lidex i posted it in the other thread that you are helping me with.  here you go:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Wed Apr  6 04:19:43 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Intel Corporation
Product Name:      Cantiga & ICH9M Chipset
Product Version:   Not Applicable


!!Kernel Information
!!------------------

Kernel release:    2.6.35-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf3400000 irq 47


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 1509:300e


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
snd-hda-intel: model=auto


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : auto,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC888
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0888
Subsystem Id: 0x1509300e
Revision Id: 0x100202
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x411: Stereo
  Device: name="ALC888 Analog", type="Audio", device=0
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
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
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC888 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x14 0x14]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC888 Digital", type="HDMI", device=3
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400780: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x18564130: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Green
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x99a30950: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x5, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x0:
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x0:
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19840: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181304f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x4, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0121401f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40148a05: [N/A] Speaker at Ext N/A
    Conn = RCA, Color = Purple
    DefAssociation = 0x0, Sequence = 0x5
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400780: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01444120: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400680: Mono Digital
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=25
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 7 Apr  5 21:18 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 6 Apr  5 21:18 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 5 Apr  5 21:18 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 4 Apr  5 21:18 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 3 Apr  5 21:18 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116, 8 Apr  5 21:18 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Apr  5 21:14 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Apr  5 21:18 .
drwxr-xr-x 3 root root 200 Apr  5 21:18 ..
lrwxrwxrwx 1 root root  12 Apr  5 21:18 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xf3400000 irq 47'
  Mixer name	: 'Realtek ALC888'
  Components	: 'HDA:10ec0888,1509300e,00100202'
  Controls      : 21
  Simple ctrls  : 12
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 20 [65%] [-16.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 253 [99%] [0.40dB]
  Front Right: Playback 253 [99%] [0.40dB]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Mic',1
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [off]
  Front Right: Capture 0 [0%] [-16.50dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Internal Mic' 'Mic' 'Line'
  Item0: 'Mic'


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 31
		value.1 31
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 true
		value.1 true
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mic Boost'
		value.0 0
		value.1 0
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1650
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.11 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Internal Mic'
		comment.item.1 Mic
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		value Mic
	}
	control.12 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.13 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.14 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Beep Playback Volume'
		value.0 0
		value.1 0
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Beep Playback Switch'
		value.0 true
		value.1 true
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 20
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.21 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 253
		value.1 253
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_seq_device
snd_hda_intel
aes_i586
aes_generic
parport_pc
ppdev
dm_crypt
binfmt_misc
snd_hda_codec_realtek
snd_hda_codec
snd_hwdep
snd_pcm
arc4
snd_timer
nvidia
joydev
snd
iwlagn
iwlcore
mac80211
cfg80211
soundcore
snd_page_alloc
psmouse
serio_raw
lp
parport
ahci
video
output
intel_agp
r8169
mii
libahci
agpgart


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x18564130
0x12 0x99a30950
0x14 0x99130110
0x15 0x411111f0
0x16 0x411111f0
0x17 0x411111f0
0x18 0x01a19840
0x19 0x411111f0
0x1a 0x0181304f
0x1b 0x0121401f
0x1c 0x411111f0
0x1d 0x40148a05
0x1e 0x01444120
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   20.501372]   alloc kstat_irqs on node -1
[   20.501379] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.501415]   alloc irq_desc for 47 on node -1
[   20.501417]   alloc kstat_irqs on node -1
[   20.501425] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   20.501450] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.501454] ALSA hda_intel.c:2559: chipset global capabilities = 0x4401
[   20.532031] ALSA hda_intel.c:914: codec_mask = 0x1
[   20.532112] ALSA hda_intel.c:1354: codec #0 probed OK
[   20.644702] ADDRCONF(NETDEV_UP): wlan0: link is not ready
--
[   20.657035] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.721694] ALSA hda_codec.c:3701: hda_codec: model 'auto' is selected
[   20.721698] ALSA patch_realtek.c:1524: SKU: Nid=0x1d sku_cfg=0x40148a05
[   20.721701] ALSA patch_realtek.c:1526: SKU: port_connectivity=0x1
[   20.721703] ALSA patch_realtek.c:1527: SKU: enable_pcbeep=0x1
[   20.721705] ALSA patch_realtek.c:1528: SKU: check_sum=0x00000004
[   20.721707] ALSA patch_realtek.c:1529: SKU: customization=0x0000008a
[   20.721710] ALSA patch_realtek.c:1530: SKU: external_amp=0x0
[   20.721712] ALSA patch_realtek.c:1531: SKU: platform_type=0x1
[   20.721714] ALSA patch_realtek.c:1532: SKU: swap=0x0
[   20.721716] ALSA patch_realtek.c:1533: SKU: override=0x1
[   20.721720] ALSA hda_codec.c:4619: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0)
[   20.721723] ALSA hda_codec.c:4623:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   20.721728] ALSA hda_codec.c:4627:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   20.721731] ALSA hda_codec.c:4628:    mono: mono_out=0x0
[   20.721733] ALSA hda_codec.c:4631:    dig-out=0x11/0x1e
[   20.721735] ALSA hda_codec.c:4632:    inputs:
[   20.721738] ALSA hda_codec.c:4636:  Internal Mic=0x12
[   20.721740] ALSA hda_codec.c:4636:  Mic=0x18
[   20.721742] ALSA hda_codec.c:4636:  Line=0x1a
[   20.721744] ALSA hda_codec.c:4638: 
[   20.723212] ALSA patch_realtek.c:1581: realtek: No valid SSID, checking pincfg 0x40148a05 for NID 0x1d
[   20.723215] ALSA patch_realtek.c:1597: realtek: Enabling init ASM_ID=0x8a05 CODEC_ID=10ec0888
[   20.723218] ALSA patch_realtek.c:1411: realtek: Enable HP auto-muting on NID 0x1b
[   20.723271] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   20.725898] ALSA hda_codec.c:2154: Cannot find slave Front Playback Volume, skipped
[   20.725901] ALSA hda_codec.c:2154: Cannot find slave Surround Playback Volume, skipped
[   20.725904] ALSA hda_codec.c:2154: Cannot find slave Center Playback Volume, skipped
[   20.725906] ALSA hda_codec.c:2154: Cannot find slave LFE Playback Volume, skipped
[   20.725909] ALSA hda_codec.c:2154: Cannot find slave Side Playback Volume, skipped
[   20.725912] ALSA hda_codec.c:2154: Cannot find slave Headphone Playback Volume, skipped
[   20.725915] ALSA hda_codec.c:2154: Cannot find slave Mono Playback Volume, skipped
[   20.725918] ALSA hda_codec.c:2154: Cannot find slave Line-Out Playback Volume, skipped
[   20.725920] ALSA hda_codec.c:2154: Cannot find slave PCM Playback Volume, skipped
[   20.725926] ALSA hda_codec.c:2154: Cannot find slave Front Playback Switch, skipped
[   20.725928] ALSA hda_codec.c:2154: Cannot find slave Surround Playback Switch, skipped
[   20.725931] ALSA hda_codec.c:2154: Cannot find slave Center Playback Switch, skipped
[   20.725933] ALSA hda_codec.c:2154: Cannot find slave LFE Playback Switch, skipped
[   20.725936] ALSA hda_codec.c:2154: Cannot find slave Side Playback Switch, skipped
[   20.725940] ALSA hda_codec.c:2154: Cannot find slave Mono Playback Switch, skipped
[   20.725944] ALSA hda_codec.c:2154: Cannot find slave Line-Out Playback Switch, skipped
[   20.725947] ALSA hda_codec.c:2154: Cannot find slave PCM Playback Switch, skipped
[   20.726377] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   21.428059] ppdev: user-space parallel port driver
[   22.385515] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   28.291581] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.291716] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.291918] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.292192] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.292326] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.292454] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.292633] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.292900] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.293050] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.293179] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.293357] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.293624] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.293756] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.293884] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.294063] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.294330] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.294462] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.294590] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.294769] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.295036] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.297725] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   28.297736] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   28.305019] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   28.313010] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   28.321043] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   28.321052] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   28.321055] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   28.321060] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   28.321253] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.321388] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.321573] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.321842] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.322223] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   28.322229] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   28.328040] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   28.328046] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   28.328063] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.328073] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.328633] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.328636] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   28.328639] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   28.328651] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.328954] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.329246] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.329620] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.330093] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.330387] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.330674] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.331048] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.331522] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.331813] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.332123] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.332497] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.332969] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.333260] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.333548] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.333920] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.334392] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.334682] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.334968] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.335341] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.335813] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.336106] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.336364] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.336633] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.336907] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.337166] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.337423] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.337694] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.337969] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.338232] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.338489] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.338760] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.339033] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.339293] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.339553] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.339822] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.341364] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.341638] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.341896] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.342165] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.342437] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.342697] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.342954] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.343223] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.343499] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.343760] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.344045] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.344317] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.344591] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.344856] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.345114] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.345383] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.345656] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.345920] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.346179] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.346449] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.346725] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.346987] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.347244] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.347513] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.347791] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.348127] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.348416] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.348797] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.349274] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.349568] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.349859] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.350239] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.350714] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.351010] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.351300] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.351677] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.352214] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.352511] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.352801] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.353179] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.353654] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.353951] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.354263] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.354638] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.355124] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.355419] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.355709] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.356108] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.356587] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.356883] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.357181] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.357558] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.358051] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.358347] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.358634] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.359020] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.359494] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.359792] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.360444] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.360821] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.361294] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.361596] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.361890] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.362265] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.362742] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   28.365837] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   28.365850] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x8, channel=0, format=0x4011
[   28.365983] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   28.366075] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   28.366120] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x8, channel=0, format=0x4011
[   28.366123] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   28.366302] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.366433] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.366613] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.366882] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.367256] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   28.367263] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   28.367276] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   28.367281] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   28.367293] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.367303] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.367836] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   28.367839] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   28.367863] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   28.367866] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   28.368047] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.368178] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.368359] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.368628] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.369000] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   28.369007] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   28.369019] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   28.369025] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   28.369035] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.369045] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   28.370641] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   28.370651] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   28.370735] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   28.370801] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   28.370814] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   28.370821] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   28.370824] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   28.370829] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   28.378294] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   28.378301] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   28.378314] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   28.378319] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[   29.440298] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   33.414826] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   33.414839] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[   34.614273] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[   34.614276] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[   34.614279] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[   34.614291] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  115.102855] padlock: VIA PadLock not detected.
[  117.428877] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.429014] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.429217] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.429495] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.429631] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.429764] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.429948] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.430221] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.430358] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.430490] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.430676] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.430949] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.431086] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.431218] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.431401] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.431675] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.431812] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.431944] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.432148] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.432420] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.435130] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  117.435142] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[  117.435146] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[  117.435150] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  117.435163] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  117.435170] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[  117.435173] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[  117.435178] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  117.435320] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.435453] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.435636] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.435908] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.436309] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  117.436316] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  117.436329] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  117.436334] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  117.436346] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.436356] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.436905] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.436908] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[  117.436910] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[  117.436921] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.437217] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.437510] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.437887] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.438365] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.438664] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.438955] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.439332] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.439810] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.440133] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.440425] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.440803] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.441281] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.441577] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.441868] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.442247] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.442725] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.443023] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.443315] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.443694] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.444386] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.444772] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.445081] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.445368] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.445648] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.445914] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.446180] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.446457] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.446736] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.447001] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.447267] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.447541] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.447817] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.448098] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.448359] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.448632] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.448907] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.449170] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.449431] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.449703] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.449979] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.450244] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.450504] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.450776] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.451055] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.451319] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.451580] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.451852] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.452300] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.452645] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.452987] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.453342] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.453700] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.454044] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.454385] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.454739] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.455096] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.455441] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.455783] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.456153] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.456515] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.456895] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.457315] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.457780] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.458426] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.458806] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.459180] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.459641] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.460251] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.460629] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.461003] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.461465] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.462027] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.462406] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.462781] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.463241] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.463802] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.464224] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.464599] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.465060] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.465621] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.466000] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.466376] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.466835] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.467394] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.467769] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.468196] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.468656] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.469217] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.469593] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.469967] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.470427] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.470988] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.471368] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.471741] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.472230] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.472786] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.473161] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.473531] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.473989] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.474550] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  117.478198] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  117.478208] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x8, channel=0, format=0x4011
[  117.478313] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[  117.478389] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  117.478396] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x8, channel=0, format=0x4011
[  117.478399] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[  117.478587] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.478766] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.478995] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.479315] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.479738] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  117.479744] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  117.479757] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  117.479762] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  117.479775] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.479809] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.480471] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[  117.480474] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[  117.480560] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[  117.480562] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[  117.480743] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.480920] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.481147] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.481463] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.481877] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  117.481884] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  117.481896] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  117.481902] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  117.481912] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.481948] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  117.483749] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  117.483759] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[  117.483854] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[  117.483919] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  117.483932] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  117.483939] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[  117.483942] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[  117.483946] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  117.496757] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  117.496765] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  117.496779] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  117.496784] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  123.342167] wlan0: authenticate with 00:21:29:c9:e6:af (try 1)
--
[  123.367343] ata5: hard resetting link
[  123.426214] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  123.426231] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  123.540011] wlan0: associate with 00:21:29:c9:e6:af (try 2)
--
[  124.116066] ata5: EH complete
[  131.571829] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  131.571841] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[  131.571851] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[  131.571906] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  134.496162] wlan0: no IPv6 routers present
[  233.763117] lo: Disabled Privacy Extensions
[  285.473413] HDA Intel 0000:00:1b.0: PCI INT A disabled
[  285.597692] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  285.597737] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[  285.597758] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  285.597762] ALSA hda_intel.c:2559: chipset global capabilities = 0x4401
[  285.628143] ALSA hda_intel.c:914: codec_mask = 0x1
[  285.628308] ALSA hda_intel.c:1354: codec #0 probed OK
[  285.641238] ALSA hda_codec.c:3701: hda_codec: model 'auto' is selected
[  285.641250] ALSA patch_realtek.c:1524: SKU: Nid=0x1d sku_cfg=0x40148a05
[  285.641260] ALSA patch_realtek.c:1526: SKU: port_connectivity=0x1
[  285.641268] ALSA patch_realtek.c:1527: SKU: enable_pcbeep=0x1
[  285.641275] ALSA patch_realtek.c:1528: SKU: check_sum=0x00000004
[  285.641283] ALSA patch_realtek.c:1529: SKU: customization=0x0000008a
[  285.641295] ALSA patch_realtek.c:1530: SKU: external_amp=0x0
[  285.641302] ALSA patch_realtek.c:1531: SKU: platform_type=0x1
[  285.641310] ALSA patch_realtek.c:1532: SKU: swap=0x0
[  285.641317] ALSA patch_realtek.c:1533: SKU: override=0x1
[  285.641329] ALSA hda_codec.c:4619: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0)
[  285.641339] ALSA hda_codec.c:4623:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[  285.641348] ALSA hda_codec.c:4627:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[  285.641357] ALSA hda_codec.c:4628:    mono: mono_out=0x0
[  285.641364] ALSA hda_codec.c:4631:    dig-out=0x11/0x1e
[  285.641372] ALSA hda_codec.c:4632:    inputs:
[  285.641379] ALSA hda_codec.c:4636:  Internal Mic=0x12
[  285.641388] ALSA hda_codec.c:4636:  Mic=0x18
[  285.641396] ALSA hda_codec.c:4636:  Line=0x1a
[  285.641403] ALSA hda_codec.c:4638: 
[  285.643008] ALSA patch_realtek.c:1581: realtek: No valid SSID, checking pincfg 0x40148a05 for NID 0x1d
[  285.643018] ALSA patch_realtek.c:1597: realtek: Enabling init ASM_ID=0x8a05 CODEC_ID=10ec0888
[  285.643028] ALSA patch_realtek.c:1411: realtek: Enable HP auto-muting on NID 0x1b
[  285.643189] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[  285.648050] ALSA hda_codec.c:2154: Cannot find slave Front Playback Volume, skipped
[  285.648062] ALSA hda_codec.c:2154: Cannot find slave Surround Playback Volume, skipped
[  285.648072] ALSA hda_codec.c:2154: Cannot find slave Center Playback Volume, skipped
[  285.648081] ALSA hda_codec.c:2154: Cannot find slave LFE Playback Volume, skipped
[  285.648090] ALSA hda_codec.c:2154: Cannot find slave Side Playback Volume, skipped
[  285.648099] ALSA hda_codec.c:2154: Cannot find slave Headphone Playback Volume, skipped
[  285.648111] ALSA hda_codec.c:2154: Cannot find slave Mono Playback Volume, skipped
[  285.648120] ALSA hda_codec.c:2154: Cannot find slave Line-Out Playback Volume, skipped
[  285.648129] ALSA hda_codec.c:2154: Cannot find slave PCM Playback Volume, skipped
[  285.648150] ALSA hda_codec.c:2154: Cannot find slave Front Playback Switch, skipped
[  285.648159] ALSA hda_codec.c:2154: Cannot find slave Surround Playback Switch, skipped
[  285.648168] ALSA hda_codec.c:2154: Cannot find slave Center Playback Switch, skipped
[  285.648176] ALSA hda_codec.c:2154: Cannot find slave LFE Playback Switch, skipped
[  285.648185] ALSA hda_codec.c:2154: Cannot find slave Side Playback Switch, skipped
[  285.648201] ALSA hda_codec.c:2154: Cannot find slave Mono Playback Switch, skipped
[  285.648215] ALSA hda_codec.c:2154: Cannot find slave Line-Out Playback Switch, skipped
[  285.648224] ALSA hda_codec.c:2154: Cannot find slave PCM Playback Switch, skipped
[  285.654470] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[  289.313409] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.313550] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.313755] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.314037] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.314177] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.314313] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.314501] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.314776] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.314915] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.315051] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.315237] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.315511] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.315650] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.315784] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.315971] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.316270] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.316410] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.316546] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.316731] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.317008] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.319683] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  289.319694] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[  289.324050] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[  289.332097] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  289.340071] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  289.340096] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[  289.340106] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[  289.340120] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  289.340649] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.341120] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.341808] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.342766] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.344135] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  289.344152] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  289.352202] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  289.352223] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  289.352283] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.352322] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.354357] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.354367] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[  289.354376] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[  289.354415] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.355494] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.356587] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.357938] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.359634] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.360717] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.361743] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.363068] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.364442] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.364759] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.365065] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.365466] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.365952] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.366266] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.366572] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.368984] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.369486] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.369787] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.370084] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.370465] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.370946] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.371229] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.371495] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.371774] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.372058] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.372331] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.372599] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.372879] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.373178] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.373448] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.373716] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.373995] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.374278] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.374547] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.374815] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.375091] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.375372] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.375640] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.375905] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.376182] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.376464] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.376732] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.377209] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.377496] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.377781] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.378049] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.378315] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.378593] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.378874] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.379142] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.379408] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.379686] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.379967] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.380236] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.380505] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.380782] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.381183] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.381453] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.381724] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.382005] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.382289] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.382591] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.382889] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.383274] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.383757] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.384061] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.384353] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.384725] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.385319] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.385624] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.385921] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.386304] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.386785] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.387087] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.387383] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.387765] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.388248] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.388534] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.388816] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.389232] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.389707] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.389993] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.390274] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.390638] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.391096] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.391381] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.391663] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.392035] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.392505] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.392791] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.393141] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.393525] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.393982] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.394268] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.394549] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.394924] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.395406] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.395707] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.396007] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.396391] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.396872] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  289.399975] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  289.399984] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x8, channel=0, format=0x4011
[  289.400145] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[  289.400231] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  289.400239] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x8, channel=0, format=0x4011
[  289.400242] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[  289.400407] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.400542] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.400726] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.401039] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.401420] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  289.401427] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  289.401440] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  289.401445] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  289.401457] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.401467] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.402005] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[  289.402008] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[  289.402036] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[  289.402038] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[  289.402182] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.402317] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.402499] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.402771] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.403147] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  289.403154] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  289.403166] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[  289.403171] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  289.403182] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.403195] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  289.404848] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  289.404857] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[  289.404941] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[  289.405014] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  289.405028] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  289.405037] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[  289.405041] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[  289.405048] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[  289.416202] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  289.416209] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  289.416222] ALSA hda_intel.c:1679: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  289.416227] ALSA hda_codec.c:1227: hda_codec_setup_stream: NID=0x9, stream=0x1, channel=0, format=0x4011
[  294.450043] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  294.450089] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x9
[  294.454090] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2
[  294.454101] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x10
[  294.454110] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x6
[  294.454157] ALSA hda_codec.c:1290: hda_codec_cleanup_stream: NID=0x2


```

---

### Post by uveryames on 2011-04-07
bump

---

### Post by uveryames on 2011-04-08
bummppppp plzzz

---

### Post by lidex on 2011-04-09
What is the make/model of this comp?
I think you should try an alsa upgrade - via the link in my sig.
When you're done please post an updated alsa-info text.

---

