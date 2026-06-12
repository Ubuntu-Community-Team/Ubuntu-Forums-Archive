---
title: "Lenovo &#37045;&#38451;E 460 sound card  [HDA Intel ] IDT 92HD81B1C5 the volume is smaller&#65311;"
date: 2011-07-06
forum: Hardware
---

### Post by fleagle236 on 2011-07-06
I would install alsa drivers 1.0.24, but it is tell me the chips is not supported, so i use the default drivers. Now it can play music but the volume is very small.

Please help me. Thanks.


My basic info:

$uname -a
Linux Zachary 2.6.32-5-686 #1 SMP Mon Jun 13 04:13:06 UTC 2011 i686 GNU/Linux

$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0

$cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

$cat /proc/asound/card0/codes#0
Codec: IDT 92HD81B1C5
Address: 0
Function Id: 0x1
Vendor Id: 0x111d76d5
Subsystem Id: 0x17aa4007
Revision Id: 0x100104
No Modem Function Group found
Default PCM:
rates [0x5e0]: 44100 48000 88200 96000 192000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=3, o=0, i=0, unsolicited=1, wake=1
IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Power-Map: 0x00
Node 0x0a [Pin Complex] wcaps 0x400583: Stereo Amp-In
Amp-In caps: N/A
Amp-In vals: [0x02 0x02]
Pincap 0x0001173c: IN OUT HP EAPD Detect
Vref caps: HIZ 50 GRD 80
EAPD 0x2: EAPD
Pin Default 0x02a1902e: [Jack] Mic at Ext Front
Conn = 1/8, Color = Pink
DefAssociation = 0x2, Sequence = 0xe
Pin-ctls: 0x22: IN VREF_GRD
Unsolicited: tag=02, enabled=1
Power: setting=D0, actual=D0
Connection: 3
0x13* 0x14 0x1c
Node 0x0b [Pin Complex] wcaps 0x400581: Stereo
Pincap 0x0001001c: OUT HP EAPD Detect
EAPD 0x2: EAPD
Pin Default 0x0221401f: [Jack] HP Out at Ext Front
Conn = 1/8, Color = Green
DefAssociation = 0x1, Sequence = 0xf
Pin-ctls: 0xc0: OUT HP
Unsolicited: tag=01, enabled=1
Power: setting=D0, actual=D0
Connection: 3
0x13 0x14* 0x1c
Node 0x0c [Pin Complex] wcaps 0x400583: Stereo Amp-In
Amp-In caps: N/A
Amp-In vals: [0x02 0x02]
Pincap 0x00011734: IN OUT EAPD Detect
Vref caps: HIZ 50 GRD 80
EAPD 0x2: EAPD
Pin Default 0x90a10120: [Fixed] Mic at Int N/A
Conn = 1/8, Color = Unknown
DefAssociation = 0x2, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x24: IN VREF_80
Unsolicited: tag=00, enabled=0
Power: setting=D0, actual=D0
Connection: 3
0x13* 0x14 0x1c
Node 0x0d [Pin Complex] wcaps 0x400501: Stereo
Pincap 0x00010050: OUT EAPD Balanced
EAPD 0x2: EAPD
Pin Default 0x90130110: [Fixed] Speaker at Int N/A
Conn = ATAPI, Color = Unknown
DefAssociation = 0x1, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Power: setting=D0, actual=D0
Connection: 3
0x13* 0x14 0x1c
Node 0x0e [Pin Complex] wcaps 0x400583: Stereo Amp-In
Amp-In caps: N/A
Amp-In vals: [0x00 0x00]
Pincap 0x00010034: IN OUT EAPD Detect
EAPD 0x2: EAPD
Pin Default 0x40000000: [N/A] Line Out at Ext N/A
Conn = Unknown, Color = Unknown
DefAssociation = 0x0, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=00, enabled=0
Power: setting=D0, actual=D0
Connection: 3
0x13 0x14 0x1c*
Node 0x0f [Pin Complex] wcaps 0x400583: Stereo Amp-In
Amp-In caps: N/A
Amp-In vals: [0x00 0x00]
Pincap 0x00010034: IN OUT EAPD Detect
EAPD 0x2: EAPD
Pin Default 0x40000000: [N/A] Line Out at Ext N/A
Conn = Unknown, Color = Unknown
DefAssociation = 0x0, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=00, enabled=0
Power: setting=D0, actual=D0
Connection: 3
0x13* 0x14 0x1c
Node 0x10 [Pin Complex] wcaps 0x400500: Mono
Pincap 0x00000010: OUT
Pin Default 0x40000000: [N/A] Line Out at Ext N/A
Conn = Unknown, Color = Unknown
DefAssociation = 0x0, Sequence = 0x0
Pin-ctls: 0x00:
Power: setting=D0, actual=D0
Connection: 1
0x1a
Node 0x11 [Pin Complex] wcaps 0x400483: Stereo Amp-In
Amp-In caps: N/A
Amp-In vals: [0x00 0x00]
Pincap 0x00000024: IN Detect
Pin Default 0x40000000: [N/A] Line Out at Ext N/A
Conn = Unknown, Color = Unknown
DefAssociation = 0x0, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=00, enabled=0
Power: setting=D0, actual=D0
Node 0x12 [Vendor Defined Widget] wcaps 0xf00503: Stereo Amp-In
Amp-In caps: N/A
Amp-In vals: [0x00 0x00]
Power: setting=D0, actual=D0
Connection: 1
0x20
Node 0x13 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
Amp-Out caps: N/A
Amp-Out vals: [0x7e 0x7e]
Converter: stream=5, channel=0
Power: setting=D0, actual=D0
Delay: 13 samples
Node 0x14 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
Amp-Out caps: N/A
Amp-Out vals: [0x7d 0x7d]
Converter: stream=5, channel=0
Power: setting=D0, actual=D0
Delay: 13 samples
Node 0x15 [Audio Input] wcaps 0x1d0541: Stereo
Converter: stream=0, channel=0
SDI-Select: 0
Power: setting=D0, actual=D0
Delay: 13 samples
Connection: 1
0x17
Processing caps: benign=0, ncoeff=0
Node 0x16 [Audio Input] wcaps 0x1d0541: Stereo
Converter: stream=0, channel=0
SDI-Select: 0
Power: setting=D0, actual=D0
Delay: 13 samples
Connection: 1
0x18
Processing caps: benign=0, ncoeff=0
Node 0x17 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
Amp-Out vals: [0x89 0x89]
Power: setting=D0, actual=D0
Connection: 7
0x0c* 0x0e 0x0f 0x1b 0x11 0x12 0x0a
Node 0x18 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Power: setting=D0, actual=D0
Connection: 7
0x0c* 0x0e 0x0f 0x1b 0x11 0x12 0x0a
Node 0x19 [Audio Selector] wcaps 0x300501: Stereo
Power: setting=D0, actual=D0
Connection: 3
0x13* 0x14 0x1c
Node 0x1a [Audio Mixer] wcaps 0x200500: Mono
Power: setting=D0, actual=D0
Connection: 1
0x19
Node 0x1b [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-In vals: [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
Power: setting=D0, actual=D0
Connection: 6
0x0c 0x0e 0x0f 0x13 0x14 0x0a
Node 0x1c [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x9f 0x9f]
Power: setting=D0, actual=D0
Connection: 1
0x1b
Node 0x1d [Audio Output] wcaps 0x4061d: Stereo Digital Amp-Out
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x00 0x00]
Converter: stream=0, channel=0
Digital:
Digital category: 0x0
PCM:
rates [0x5e0]: 44100 48000 88200 96000 192000
bits [0xe]: 16 20 24
formats [0x5]: PCM AC3
Power: setting=D0, actual=D0
Delay: 4 samples
Node 0x1e [Audio Output] wcaps 0x4061d: Stereo Digital Amp-Out
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x00 0x00]
Converter: stream=0, channel=0
Digital:
Digital category: 0x0
PCM:
rates [0x5e0]: 44100 48000 88200 96000 192000
bits [0xe]: 16 20 24
formats [0x5]: PCM AC3
Power: setting=D0, actual=D0
Delay: 4 samples
Node 0x1f [Pin Complex] wcaps 0x400781: Stereo Digital
Pincap 0x00000014: OUT Detect
Pin Default 0x40000000: [N/A] Line Out at Ext N/A
Conn = Unknown, Color = Unknown
DefAssociation = 0x0, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=00, enabled=0
Power: setting=D0, actual=D0
Connection: 1
0x1d
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
Pincap 0x00000034: IN OUT Detect
Pin Default 0x40000000: [N/A] Line Out at Ext N/A
Conn = Unknown, Color = Unknown
DefAssociation = 0x0, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=00, enabled=0
Power: setting=D0, actual=D0
Connection: 1
0x1e
Node 0x21 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
Amp-Out vals: [0x00]
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono$uname -a
Linux Zachary 2.6.32-5-686 #1 SMP Mon Jun 13 04:13:06 UTC 2011 i686 GNU/Linux

$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0

$cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

$cat /proc/asound/card0/codes#0
Codec: IDT 92HD81B1C5
Address: 0
Function Id: 0x1
Vendor Id: 0x111d76d5
Subsystem Id: 0x17aa4007
Revision Id: 0x100104
No Modem Function Group found
Default PCM:
rates [0x5e0]: 44100 48000 88200 96000 192000
bits [0xe]: 16 20 24
formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=3, o=0, i=0, unsolicited=1, wake=1
IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Power-Map: 0x00
Node 0x0a [Pin Complex] wcaps 0x400583: Stereo Amp-In
Amp-In caps: N/A
Amp-In vals: [0x02 0x02]
Pincap 0x0001173c: IN OUT HP EAPD Detect
Vref caps: HIZ 50 GRD 80
EAPD 0x2: EAPD
Pin Default 0x02a1902e: [Jack] Mic at Ext Front
Conn = 1/8, Color = Pink
DefAssociation = 0x2, Sequence = 0xe
Pin-ctls: 0x22: IN VREF_GRD
Unsolicited: tag=02, enabled=1
Power: setting=D0, actual=D0
Connection: 3
0x13* 0x14 0x1c
Node 0x0b [Pin Complex] wcaps 0x400581: Stereo
Pincap 0x0001001c: OUT HP EAPD Detect
EAPD 0x2: EAPD
Pin Default 0x0221401f: [Jack] HP Out at Ext Front
Conn = 1/8, Color = Green
DefAssociation = 0x1, Sequence = 0xf
Pin-ctls: 0xc0: OUT HP
Unsolicited: tag=01, enabled=1
Power: setting=D0, actual=D0
Connection: 3
0x13 0x14* 0x1c
Node 0x0c [Pin Complex] wcaps 0x400583: Stereo Amp-In
Amp-In caps: N/A
Amp-In vals: [0x02 0x02]
Pincap 0x00011734: IN OUT EAPD Detect
Vref caps: HIZ 50 GRD 80
EAPD 0x2: EAPD
Pin Default 0x90a10120: [Fixed] Mic at Int N/A
Conn = 1/8, Color = Unknown
DefAssociation = 0x2, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x24: IN VREF_80
Unsolicited: tag=00, enabled=0
Power: setting=D0, actual=D0
Connection: 3
0x13* 0x14 0x1c
Node 0x0d [Pin Complex] wcaps 0x400501: Stereo
Pincap 0x00010050: OUT EAPD Balanced
EAPD 0x2: EAPD
Pin Default 0x90130110: [Fixed] Speaker at Int N/A
Conn = ATAPI, Color = Unknown
DefAssociation = 0x1, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x40: OUT
Power: setting=D0, actual=D0
Connection: 3
0x13* 0x14 0x1c
Node 0x0e [Pin Complex] wcaps 0x400583: Stereo Amp-In
Amp-In caps: N/A
Amp-In vals: [0x00 0x00]
Pincap 0x00010034: IN OUT EAPD Detect
EAPD 0x2: EAPD
Pin Default 0x40000000: [N/A] Line Out at Ext N/A
Conn = Unknown, Color = Unknown
DefAssociation = 0x0, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=00, enabled=0
Power: setting=D0, actual=D0
Connection: 3
0x13 0x14 0x1c*
Node 0x0f [Pin Complex] wcaps 0x400583: Stereo Amp-In
Amp-In caps: N/A
Amp-In vals: [0x00 0x00]
Pincap 0x00010034: IN OUT EAPD Detect
EAPD 0x2: EAPD
Pin Default 0x40000000: [N/A] Line Out at Ext N/A
Conn = Unknown, Color = Unknown
DefAssociation = 0x0, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=00, enabled=0
Power: setting=D0, actual=D0
Connection: 3
0x13* 0x14 0x1c
Node 0x10 [Pin Complex] wcaps 0x400500: Mono
Pincap 0x00000010: OUT
Pin Default 0x40000000: [N/A] Line Out at Ext N/A
Conn = Unknown, Color = Unknown
DefAssociation = 0x0, Sequence = 0x0
Pin-ctls: 0x00:
Power: setting=D0, actual=D0
Connection: 1
0x1a
Node 0x11 [Pin Complex] wcaps 0x400483: Stereo Amp-In
Amp-In caps: N/A
Amp-In vals: [0x00 0x00]
Pincap 0x00000024: IN Detect
Pin Default 0x40000000: [N/A] Line Out at Ext N/A
Conn = Unknown, Color = Unknown
DefAssociation = 0x0, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=00, enabled=0
Power: setting=D0, actual=D0
Node 0x12 [Vendor Defined Widget] wcaps 0xf00503: Stereo Amp-In
Amp-In caps: N/A
Amp-In vals: [0x00 0x00]
Power: setting=D0, actual=D0
Connection: 1
0x20
Node 0x13 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
Amp-Out caps: N/A
Amp-Out vals: [0x7e 0x7e]
Converter: stream=5, channel=0
Power: setting=D0, actual=D0
Delay: 13 samples
Node 0x14 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
Amp-Out caps: N/A
Amp-Out vals: [0x7d 0x7d]
Converter: stream=5, channel=0
Power: setting=D0, actual=D0
Delay: 13 samples
Node 0x15 [Audio Input] wcaps 0x1d0541: Stereo
Converter: stream=0, channel=0
SDI-Select: 0
Power: setting=D0, actual=D0
Delay: 13 samples
Connection: 1
0x17
Processing caps: benign=0, ncoeff=0
Node 0x16 [Audio Input] wcaps 0x1d0541: Stereo
Converter: stream=0, channel=0
SDI-Select: 0
Power: setting=D0, actual=D0
Delay: 13 samples
Connection: 1
0x18
Processing caps: benign=0, ncoeff=0
Node 0x17 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
Amp-Out vals: [0x89 0x89]
Power: setting=D0, actual=D0
Connection: 7
0x0c* 0x0e 0x0f 0x1b 0x11 0x12 0x0a
Node 0x18 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
Amp-Out vals: [0x80 0x80]
Power: setting=D0, actual=D0
Connection: 7
0x0c* 0x0e 0x0f 0x1b 0x11 0x12 0x0a
Node 0x19 [Audio Selector] wcaps 0x300501: Stereo
Power: setting=D0, actual=D0
Connection: 3
0x13* 0x14 0x1c
Node 0x1a [Audio Mixer] wcaps 0x200500: Mono
Power: setting=D0, actual=D0
Connection: 1
0x19
Node 0x1b [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
Amp-In vals: [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
Power: setting=D0, actual=D0
Connection: 6
0x0c 0x0e 0x0f 0x13 0x14 0x0a
Node 0x1c [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x9f 0x9f]
Power: setting=D0, actual=D0
Connection: 1
0x1b
Node 0x1d [Audio Output] wcaps 0x4061d: Stereo Digital Amp-Out
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x00 0x00]
Converter: stream=0, channel=0
Digital:
Digital category: 0x0
PCM:
rates [0x5e0]: 44100 48000 88200 96000 192000
bits [0xe]: 16 20 24
formats [0x5]: PCM AC3
Power: setting=D0, actual=D0
Delay: 4 samples
Node 0x1e [Audio Output] wcaps 0x4061d: Stereo Digital Amp-Out
Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Amp-Out vals: [0x00 0x00]
Converter: stream=0, channel=0
Digital:
Digital category: 0x0
PCM:
rates [0x5e0]: 44100 48000 88200 96000 192000
bits [0xe]: 16 20 24
formats [0x5]: PCM AC3
Power: setting=D0, actual=D0
Delay: 4 samples
Node 0x1f [Pin Complex] wcaps 0x400781: Stereo Digital
Pincap 0x00000014: OUT Detect
Pin Default 0x40000000: [N/A] Line Out at Ext N/A
Conn = Unknown, Color = Unknown
DefAssociation = 0x0, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=00, enabled=0
Power: setting=D0, actual=D0
Connection: 1
0x1d
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
Pincap 0x00000034: IN OUT Detect
Pin Default 0x40000000: [N/A] Line Out at Ext N/A
Conn = Unknown, Color = Unknown
DefAssociation = 0x0, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=00, enabled=0
Power: setting=D0, actual=D0
Connection: 1
0x1e
Node 0x21 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
Amp-Out vals: [0x00]
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono

---

### Post by lidex on 2011-07-06
Check your levels in alsamixer
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by fleagle236 on 2011-07-07
> **lidex said:**
> Check your levels in alsamixer
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Thanks for you.

I act the way you said to do, change the all volume max. But the sound is still very small. 

My alsamixer all info is in the attachments, please help...


Thanks a lot.

---

### Post by lidex on 2011-07-07
Scroll to the right in alsamixer, there are more elements hiding there.

---

### Post by fleagle236 on 2011-07-11
Sorry, i did not aware the other options of the alsamixer.:(

The rest of alsamixer screenshort is here.

Please help me.


Thanks very much!

---

