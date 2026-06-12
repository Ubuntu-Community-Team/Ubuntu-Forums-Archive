---
title: "Headphone Jack not detected"
date: 2010-05-29
forum: Hardware
---

### Post by MusicMan374 on 2010-05-29
I am having issues with my headphone jack on Xubuntu 10.04.

At first it would play through both of them, then I installed the alsa-mixer-gui and changed one of the levels and now when I plug in headphones nothing comes out of the headphones, as if they aren't plugged in. I cannot get anything out of the headphones now. This is the output of aplay -l:

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm running 64bit if it makes a difference. I would love some help on this, googling around has returned nothing of use.

---

### Post by MusicMan374 on 2010-05-29
Bump? I could really use some help on this one. All of the solutions I have found are for the Intel sound cards, mine is a conexant/ATI i think? At least that's what I gathered from the aplay -l

---

### Post by lidex on 2010-05-30
There's a simple solution - you need to reset the change you made. I don't think there's a need for debugging here. Try gnome-alsamixer.
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

---

### Post by MusicMan374 on 2010-05-30
I tried the gnome alsa mixer before posting, there is no headphone jack sense option available. I don't know how I'd go about resetting that change but even before the sound came out of both speakers and headphones at the same time which isn't a great option. I can try purging alsa altogether and reinstalling I guess see if that does anything.

---

### Post by MusicMan374 on 2010-05-30
reinstalled everything alsa related, including purging configuration files and I cannot get it to revert. Before I had a problem but it was an easier solvable. Now nothing comes out of the headphones, as if the jack doesn't exist. Happened after adjusting the master level in the alsamixer-gui rather than the gnome-alsamixer.

---

### Post by lidex on 2010-05-30
Try purging alsamixer-gui. And do this as well. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

### Post by MusicMan374 on 2010-05-30
Purged alsamixdergui and removed the library that came with it, deleted the pulse directory but both the asound folder and conf file were not present. I will restart and check to see if the problem is resolved

---

### Post by MusicMan374 on 2010-05-30
No dice. Still nothing through the headphones jack.

---

### Post by lidex on 2010-05-31
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by MusicMan374 on 2010-05-31
Last one returned an error, here are all of the results:

```
ryan@ryan-NB-Xubuntu:~$ uname -a
Linux ryan-NB-Xubuntu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
ryan@ryan-NB-Xubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ryan@ryan-NB-Xubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).
ryan@ryan-NB-Xubuntu:~$ head -n l /proc/asound/card*/codec#*
head: l: invalid number of lines
```

---

### Post by dino99 on 2010-05-31
is your hardware well recognized ? : system pref sound

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

there are some opened bugs about hda+ati+hdmi around on google

i think you might try the latest packages from this ppa:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by MusicMan374 on 2010-05-31
I will try these and post results later. The sound that comes through the HDMI works fine, I just have to switch the sound device to ALSA ATI HD or something rather. The default is ALSA ATI SB if I remember correctly. I have hooked the netbook up to an hdtv before to watch something and video+sound worked fine. It's just the headphone jack.

---

### Post by MusicMan374 on 2010-05-31
[IMG]http://i45.tinypic.com/dm63dh.png[/IMG]
That is my sound mixer dialog. Is that what you needed?

I have already followed basic troubleshooting steps and I'm pretty sure the driver is the best it's gonna get but I can retry everything to be extra sure.

That PPA seems to contain intel and nvidia graphics drivers, and I have an ATI card. However, I actually chose not to use the restricted driver available for it because the ATI driver actually made the performance really terrible. It couldn't even handle youtube on 360p. I use the OSS drivers for ATI, and even though it only provides 2D support/acceleration, performance for everyday video and internet use is excellent. I don't need the 3D acceleration on my netbook, I have a desktop with a high end nvidia card for that :P

BTW: the second level in addition to master that is covered by the dropdown box is PCM. There are no other levels to modify, just Master and PCM.

---

### Post by lidex on 2010-05-31
> head: l: invalid number of lines
Should be the digit 1, not an l.
Try upgrading alsa via the alsa-upgrade link in my sig.

---

### Post by MusicMan374 on 2010-05-31
No go on the script in your signature. Ran it per the instructions and same issue remains. I'm considering just clearing it and reinstalling xubuntu so at least the sound comes out of BOTH the headphone jack and the internal speakers. Because before when I plugged in headphones the internal speakers got quieter but did not shut off all the way. If I could get back to that stage then I'm sure there's an easy fix?

---

### Post by lidex on 2010-05-31
What is your codec? What is make/model of the PC?
```
head -n 1 /proc/asound/card*/codec#*
```

---

### Post by MusicMan374 on 2010-06-01
Oh sorry I ran that and forgot to post it in my last reply. Here it is:

```
$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20582 (Pebble)

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
```

---

### Post by lidex on 2010-06-01
So you have no idea what kind of computer you own?

---

### Post by MusicMan374 on 2010-06-01
It's a Toshiba Satellite T115D-S1120. Sorry.

---

### Post by lidex on 2010-06-01
Let's get an idea of where your system vitals are now. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by MusicMan374 on 2010-06-01
These are the contents of the text file produced by your script:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Wed Jun  2 03:38:22 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      Satellite T115D


!!Kernel Information
!!------------------

Kernel release:    2.6.32-22-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.22.1
Library version:    1.0.22
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
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

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf0600000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xcfdec000 irq 28


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383
	Subsystem: 1179:ffe2
--
01:05.1 0403: 1002:960f
	Subsystem: 1002:9612


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
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1
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
	probe_only : N,N,N,N,N,N,N,N
	single_cmd : N

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1
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
	probe_only : N,N,N,N,N,N,N,N
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Conexant CX20582 (Pebble)
Address: 0
Function Id: 0x1
Vendor Id: 0x14f15066
Subsystem Id: 0x1179ffe2
Revision Id: 0x100301
No Modem Function Group found
Default PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x10 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x32 0x32]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x13 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x50 0x50] [0x80 0x80] [0x50 0x50] [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x16 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x17 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x03 0x03]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x042140f0: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Green
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x04a190f0: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x0:
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x0:
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1e [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x95a701f0: [Fixed] Mic at Int Top
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x921701f0: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="Conexant Digital", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x22 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Node 0x23 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x04, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x24 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11
Node 0x25 [Vendor Defined Widget] wcaps 0xf00000: Mono
Codec: ATI RS690/780 HDMI
Address: 0
Function Id: 0x1
Vendor Id: 0x1002791a
Subsystem Id: 0x00791a00
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x60]: 44100 48000
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
  Device: name="ATI HDMI", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  0 May 31 20:04 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 32 May 31 20:04 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  4 May 31 20:04 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 36 May 31 20:04 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116, 24 May 31 20:19 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 Jun  1 20:35 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 17 May 31 20:19 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 51 May 31 20:19 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116,  1 May 31 20:04 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 May 31 20:04 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 May 31 20:04 .
drwxr-xr-x 3 root root 260 May 31 20:04 ..
lrwxrwxrwx 1 root root  12 May 31 20:04 pci-0000:00:14.2 -> ../controlC0
lrwxrwxrwx 1 root root  12 May 31 20:04 pci-0000:01:05.1 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xf0600000 irq 16'
  Mixer name	: 'Conexant CX20582 (Pebble)'
  Components	: 'HDA:14f15066,1179ffe2,00100301'
  Controls      : 12
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 50 [68%] [-24.00dB] [off]
  Front Right: Playback 50 [68%] [-24.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic B',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Mic C',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic E',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic F',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [on]
  Front Right: Capture 80 [100%] [6.00dB] [on]
Simple mixer control 'Ext Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '30dB'

!!-------Mixer controls for card 1 [HDMI]

Card hw:1 'HDMI'/'HDA ATI HDMI at 0xcfdec000 irq 28'
  Mixer name	: 'ATI RS690/780 HDMI'
  Components	: 'HDA:1002791a,00791a00,00100000'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 74'
		comment.dbmin -7400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 50
		value.1 50
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value false
	}
	control.3 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '0dB'
		comment.item.1 '10dB'
		comment.item.2 '20dB'
		comment.item.3 '30dB'
		comment.item.4 '40dB'
		iface MIXER
		name 'Ext Mic Boost Capture Enum'
		value '30dB'
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 80'
		comment.dbmin -7400
		comment.dbmax 600
		iface MIXER
		name 'Capture Volume'
		value.0 80
		value.1 80
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.6 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.7 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.8 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.11 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Mic B'
		comment.item.1 'Mic C'
		comment.item.2 'Mic E'
		comment.item.3 'Mic F'
		iface MIXER
		name 'Capture Source'
		value 'Mic B'
	}
	control.12 {
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
}
state.HDMI {
	control.1 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.2 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.3 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
michael_mic
arc4
cryptd
aes_x86_64
aes_generic
dm_crypt
snd_hda_codec_atihdmi
ppdev
joydev
snd_hda_codec_conexant
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
uvcvideo
videodev
v4l1_compat
v4l2_compat_ioctl32
snd
soundcore
rtl8187se
shpchp
atl1c
snd_page_alloc
i2c_piix4
edac_core
edac_mce_amd
k8temp
psmouse
serio_raw
lp
parport
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
radeon
ttm
drm_kms_helper
drm
i2c_algo_bit
ahci
video
output


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x19 0x042140f0
0x1a 0x04a190f0
0x1b 0x400001f0
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x95a701f0
0x1f 0x921701f0
0x20 0x400001f0
0x22 0x400001f0
0x23 0x400001f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[ 8046.810087] ehci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00013)
[ 8046.810148] HDA Intel 0000:00:14.2: restoring config space at offset 0xf (was 0x10a, writing 0xa)
[ 8046.810172] HDA Intel 0000:00:14.2: restoring config space at offset 0x1 (was 0x4100006, writing 0x4100002)
[ 8046.810313] HDA Intel 0000:01:05.1: restoring config space at offset 0x4 (was 0x0, writing 0xcfdec000)
[ 8046.810317] HDA Intel 0000:01:05.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800008)
[ 8046.810323] HDA Intel 0000:01:05.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
[ 8046.810354] atl1c 0000:08:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
--
[ 8047.240072] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 8047.240092] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 8047.240148] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
--
[ 8057.250093] PM: resume of drv:radeon dev:0000:01:05.0 complete after 10009.945 msecs
[ 8057.250111] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 8057.250117] HDA Intel 0000:01:05.1: setting latency timer to 64
[ 8057.250143] HDA Intel 0000:01:05.1: irq 27 for MSI/MSI-X
[ 8057.340095] r8180 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
--
[ 8058.490642] Component: resume devices, time: 11680
[ 8058.490644] Modules linked in: michael_mic arc4 cryptd aes_x86_64 aes_generic dm_crypt snd_hda_codec_atihdmi ppdev joydev snd_hda_codec_conexant snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 snd soundcore rtl8187se(C) shpchp atl1c snd_page_alloc i2c_piix4 edac_core edac_mce_amd k8temp psmouse serio_raw lp parport fbcon tileblit font bitblit softcursor vga16fb vgastate radeon ttm drm_kms_helper drm i2c_algo_bit ahci video output
[ 8058.490688] Pid: 3206, comm: pm-suspend Tainted: G        WC 2.6.32-22-generic #33-Ubuntu


```


I would've uploaded the text file but it exceeds the max file size by 5 kb or so. If you need it I can just put it in a tar archive and upload it.

---

### Post by lidex on 2010-06-02
> !!ALSA Version
!!------------
Driver version:     1.0.22.1
Library version:    1.0.22
Utilities version:  1.0.23

Apparently the upgrade-script failed. Try running it again and make sure alsa-backports are uninstalled first.

---

### Post by MusicMan374 on 2010-06-04
I ran alsamixer from the terminal and it now says .23, I assume that means I'm fully upgraded now? I forgot to remove backports last time. It seems to have done the trick for the installation but nothing for my headphone jack.

---

### Post by lidex on 2010-06-05
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by MusicMan374 on 2010-06-05
Nope. Nothing. It's weird, it works perfectly in windows. It is a software thing I just can't see why xubuntu can't detect the switch. By the way, for future reference, in xfce, mousepad is the text editor, not gedit, but I know what you mean by gedit in terminal.

---

### Post by lidex on 2010-06-05
> **MusicMan374 said:**
> Nope. Nothing. It's weird, it works perfectly in windows. It is a software thing I just can't see why xubuntu can't detect the switch. By the way, for future reference, in xfce, mousepad is the text editor, not gedit, but I know what you mean by gedit in terminal.

I should know that...I actually use it in gnome a lot. Small and fast.

---

### Post by MusicMan374 on 2010-06-06
I'm just going to give up on it. To be honest there were a lot of things not working well. The OSS drivers for my ATI card had better performance than the ATI restricted drivers, which was pretty ridiculous. But the OSS drivers didn't support the HDMI port output. The sound jacks didn't work right, and it still got pretty laggy at times. I ended up just restoring the entire thing to the factory image. This way I have all of the HDD accelerometer protection stuff, working jacks, and better mobility software. I'm still going to keep Ubuntu on my desktop though, everything works fantastically there. The netbook just doesn't have the power to take advantage of linux all that much.

---

### Post by Hack.The.Pow. on 2011-03-11
anybody ever figure this out??  I'm pretty sure I have the same sound card as you(HDA ATI SB).  Its in a Acer Asprire One (A0521).  Headphones worked fine in regular Ubuntu but don't work in xubuntu.

---

### Post by MusicMan374 on 2011-03-11
No I didn't, I ended up switching back to windows 7. I couldn't get much of the hardware to work right. Sorry. Try opening a new thread, maybe there are new solutions now?

---

