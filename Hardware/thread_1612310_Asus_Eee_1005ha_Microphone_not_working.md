---
title: "Asus Eee 1005ha Microphone not working"
date: 2010-11-03
forum: Hardware
---

### Post by gwinkleman on 2010-11-03
After opening up Skype I found that my video works however my microphone does not.  I've opened up my sound preferences and nothing seems to be muted and the microphone input volume is at 100% but during tests there is no sound. I opened the sound recorder and clicked record and the microphone works when I do this but nowhere else. Help please.

---

### Post by lidex on 2010-11-03
Have a look here:
[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)

---

### Post by gwinkleman on 2010-11-03
> **lidex said:**
> Have a look here:
[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)

I tried this link but the software that was recommended was outdated and couldn't be found. Any more recent solutions? I am running Ubuntu 10.10 desktop.

---

### Post by jemssmith on 2010-11-03
First You must insure that you have fitted/plugged your microphone's cable to right place into your system. For that you can see Microphone's drawn icon into system's Audio panel. Refit at proper place and then check. If Problem not resolved you can reinstall audio drivers. At the last contact your Audio/Microphone's manufacturer's Support Team.

---

### Post by gwinkleman on 2010-11-03
> **jemssmith said:**
> First You must insure that you have fitted/plugged your microphone's cable to right place into your system. For that you can see Microphone's drawn icon into system's Audio panel. Refit at proper place and then check. If Problem not resolved you can reinstall audio drivers. At the last contact your Audio/Microphone's manufacturer's Support Team.
The computer has a built in microphone.

---

### Post by lidex on 2010-11-04
What I've seen for this unit is it works out of the box. The mic is digital. Try installing gnome-alsamixer.
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Jesse David on 2010-11-15
I've been having the same problem myself for a while.  The sound preferences tab doesn't even show for me, and I've been trying pretty much everything I could find to make it work again (it did at one point but can't remember when it stopped).

For whatever reason it works for "Sound Recorder" but for other programs such as Skype it does not.

```
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Mon Nov 15 16:50:59 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      ASUSTeK Computer INC.
Product Name:      1005HA


!!Kernel Information
!!------------------

Kernel release:    2.6.32-25-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.22
Utilities version:  1.0.22


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
                      HDA Intel at 0xf7db8000 irq 28


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
    Subsystem: 1043:83ce
--
    Prefetchable memory behind bridge: 0000000040200000-00000000403fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1
    model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    position_fix : 0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC269
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0269
Subsystem Id: 0x104383ce
Revision Id: 0x100004
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC269 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x3f, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x3f, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x3f 0x3f]
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
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x11, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x90 0x90]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Volume", index=0, device=0
  Control: name="Capture Switch", index=0, device=0
  Control: name="Mic Boost", index=0, device=0
  Device: name="ALC269 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x11, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x15 0x15]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x18 0x19 0x1a 0x1b 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x00]
  Connection: 2
     0x0c 0x0d
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x10 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x11 [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x99a30920: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00010050: OUT EAPD Balanced
  EAPD 0x2: EAPD
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0321401f: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 2
     0x0c 0x0d*
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x03a19830: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=08, enabled=1
  Connection: 2
     0x0c* 0x0d
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005822d: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = Purple
    DefAssociation = 0x2, Sequence = 0xd
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
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
  Processing caps: benign=0, ncoeff=33
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x23 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 7
     0x18 0x19 0x1a 0x1b 0x1d 0x12* 0x0b
Node 0x24 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 Nov 15 16:43 /dev/snd/controlC0
crw-rw----  1 root audio 116,  4 Nov 15 16:43 /dev/snd/hwC0D0
crw-rw----  1 root audio 116, 24 Nov 15 17:46 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 Nov 15 17:37 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  1 Nov 15 16:43 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Nov 15 16:43 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Nov 15 16:43 .
drwxr-xr-x 3 root root 180 Nov 15 16:43 ..
lrwxrwxrwx 1 root root  12 Nov 15 16:43 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xf7db8000 irq 28'
  Mixer name    : 'Realtek ALC269'
  Components    : 'HDA:10ec0269,104383ce,00100004'
  Controls      : 11
  Simple ctrls  : 7
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 63 [98%] [0.00dB] [on]
  Front Right: Playback 63 [98%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [1.00dB] [on]
  Front Right: Playback 64 [100%] [1.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 21 [46%] [4.00dB] [on]
  Front Right: Capture 21 [46%] [4.00dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 90 [75%] [15.00dB]
  Front Right: Capture 90 [75%] [15.00dB]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Speaker Playback Switch'
        value.0 true
        value.1 true
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 64'
        comment.dbmin -6300
        comment.dbmax 100
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 64
        value.1 64
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
        comment.range '0 - 64'
        comment.dbmin -6300
        comment.dbmax 100
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 63
        value.1 63
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 46'
        comment.dbmin -1700
        comment.dbmax 2900
        iface MIXER
        name 'Capture Volume'
        value.0 21
        value.1 21
    }
    control.6 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
    }
    control.7 {
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
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 64'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value 64
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.10 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.tlv '0000000100000008ffffec1400000014'
        comment.dbmin -5100
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
    }
    control.11 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 120'
        comment.tlv '0000000100000008fffff44800000032'
        comment.dbmin -3000
        comment.dbmax 3000
        iface MIXER
        name 'Digital Capture Volume'
        value.0 90
        value.1 90
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_iso8859_1
nls_cp437
vfat
fat
usb_storage
binfmt_misc
ppdev
joydev
snd_hda_codec_realtek
fbcon
tileblit
font
bitblit
softcursor
snd_hda_intel
vga16fb
vgastate
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
arc4
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
ath9k
ath9k_common
mac80211
snd_timer
snd_seq_device
ath9k_hw
i915
ath
uvcvideo
drm_kms_helper
snd
psmouse
cfg80211
intel_agp
videodev
v4l1_compat
drm
i2c_algo_bit
serio_raw
soundcore
snd_page_alloc
agpgart
atl1c
led_class
video
output
eeepc_laptop
lp
parport
ahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x411111f0
0x12 0x99a30920
0x14 0x99130110
0x15 0x0321401f
0x16 0x411111f0
0x18 0x03a19830
0x19 0x411111f0
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x4005822d
0x1e 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   18.606707]   alloc kstat_irqs on node -1
[   18.606725] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.606983]   alloc irq_desc for 28 on node -1
[   18.606991]   alloc kstat_irqs on node -1
[   18.607014] HDA Intel 0000:00:1b.0: irq 28 for MSI/MSI-X
[   18.607075] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.842175] Console: switching to colour frame buffer device 128x37
--
[   19.084907] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   19.693524] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   23.694596] type=1505 audit(1289835791.509:5):  operation="profile_load" pid=777 name="/usr/share/gdm/guest-session/Xsession"



```

---

### Post by lidex on 2010-11-15
> **Jesse David said:**
> I've been having the same problem myself for a while.  The sound preferences tab doesn't even show for me, and I've been trying pretty much everything I could find to make it work again (it did at one point but can't remember when it stopped).

For whatever reason it works for "Sound Recorder" but for other programs such as Skype it does not.

```
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Mon Nov 15 16:50:59 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      ASUSTeK Computer INC.
Product Name:      1005HA


!!Kernel Information
!!------------------

Kernel release:    2.6.32-25-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.22
Utilities version:  1.0.22


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
                      HDA Intel at 0xf7db8000 irq 28


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
    Subsystem: 1043:83ce
--
    Prefetchable memory behind bridge: 0000000040200000-00000000403fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1
    model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    position_fix : 0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC269
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0269
Subsystem Id: 0x104383ce
Revision Id: 0x100004
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC269 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x3f, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x3f, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x3f 0x3f]
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
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x11, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x90 0x90]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Volume", index=0, device=0
  Control: name="Capture Switch", index=0, device=0
  Control: name="Mic Boost", index=0, device=0
  Device: name="ALC269 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x11, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x15 0x15]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x18 0x19 0x1a 0x1b 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x00]
  Connection: 2
     0x0c 0x0d
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x10 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x11 [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x99a30920: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00010050: OUT EAPD Balanced
  EAPD 0x2: EAPD
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0321401f: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 2
     0x0c 0x0d*
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x03a19830: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=08, enabled=1
  Connection: 2
     0x0c* 0x0d
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005822d: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = Purple
    DefAssociation = 0x2, Sequence = 0xd
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
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
  Processing caps: benign=0, ncoeff=33
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x23 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 7
     0x18 0x19 0x1a 0x1b 0x1d 0x12* 0x0b
Node 0x24 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 Nov 15 16:43 /dev/snd/controlC0
crw-rw----  1 root audio 116,  4 Nov 15 16:43 /dev/snd/hwC0D0
crw-rw----  1 root audio 116, 24 Nov 15 17:46 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 Nov 15 17:37 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  1 Nov 15 16:43 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Nov 15 16:43 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Nov 15 16:43 .
drwxr-xr-x 3 root root 180 Nov 15 16:43 ..
lrwxrwxrwx 1 root root  12 Nov 15 16:43 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xf7db8000 irq 28'
  Mixer name    : 'Realtek ALC269'
  Components    : 'HDA:10ec0269,104383ce,00100004'
  Controls      : 11
  Simple ctrls  : 7
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 63 [98%] [0.00dB] [on]
  Front Right: Playback 63 [98%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [1.00dB] [on]
  Front Right: Playback 64 [100%] [1.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 21 [46%] [4.00dB] [on]
  Front Right: Capture 21 [46%] [4.00dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 90 [75%] [15.00dB]
  Front Right: Capture 90 [75%] [15.00dB]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Speaker Playback Switch'
        value.0 true
        value.1 true
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 64'
        comment.dbmin -6300
        comment.dbmax 100
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 64
        value.1 64
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
        comment.range '0 - 64'
        comment.dbmin -6300
        comment.dbmax 100
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 63
        value.1 63
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 46'
        comment.dbmin -1700
        comment.dbmax 2900
        iface MIXER
        name 'Capture Volume'
        value.0 21
        value.1 21
    }
    control.6 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
    }
    control.7 {
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
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 64'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value 64
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.10 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.tlv '0000000100000008ffffec1400000014'
        comment.dbmin -5100
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
    }
    control.11 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 120'
        comment.tlv '0000000100000008fffff44800000032'
        comment.dbmin -3000
        comment.dbmax 3000
        iface MIXER
        name 'Digital Capture Volume'
        value.0 90
        value.1 90
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_iso8859_1
nls_cp437
vfat
fat
usb_storage
binfmt_misc
ppdev
joydev
snd_hda_codec_realtek
fbcon
tileblit
font
bitblit
softcursor
snd_hda_intel
vga16fb
vgastate
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
arc4
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
ath9k
ath9k_common
mac80211
snd_timer
snd_seq_device
ath9k_hw
i915
ath
uvcvideo
drm_kms_helper
snd
psmouse
cfg80211
intel_agp
videodev
v4l1_compat
drm
i2c_algo_bit
serio_raw
soundcore
snd_page_alloc
agpgart
atl1c
led_class
video
output
eeepc_laptop
lp
parport
ahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x411111f0
0x12 0x99a30920
0x14 0x99130110
0x15 0x0321401f
0x16 0x411111f0
0x18 0x03a19830
0x19 0x411111f0
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x4005822d
0x1e 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   18.606707]   alloc kstat_irqs on node -1
[   18.606725] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.606983]   alloc irq_desc for 28 on node -1
[   18.606991]   alloc kstat_irqs on node -1
[   18.607014] HDA Intel 0000:00:1b.0: irq 28 for MSI/MSI-X
[   18.607075] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.842175] Console: switching to colour frame buffer device 128x37
--
[   19.084907] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   19.693524] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   23.694596] type=1505 audit(1289835791.509:5):  operation="profile_load" pid=777 name="/usr/share/gdm/guest-session/Xsession"



```

Use the link in my sig to update alsa to latest version. Remove any backports first, If the mic is working anywhere, it suggests the software may be the problem. Many have issues with the mic in skype.

To deal with the sound preferences/pulse, remove your pulse config files and re-install.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

```
sudo apt-get install --reinstall pulseaudio gstreamer0.10-pulseaudio gnome-media gnome-media-common
```

---

### Post by Jesse David on 2010-11-19
Thanks,

That seems to have fixed that problem, however for some reason another problem has occurred.

Now whenever I try to play streaming video on Firefox, I get no sound and I need to restart the computer to play videos on Totem.  But probably a question for a different part of the forum

---

