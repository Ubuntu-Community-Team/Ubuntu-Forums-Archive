---
title: "ATI 5700 HDMI  Surround Sound AAC HELP PLZ"
date: 2014-04-26
forum: Hardware
---

### Post by HSken on 2014-04-26
Hey

I have configured a new HTPC with ubuntu 14.04 and XBMC, I got most things working but have some small issues left:
[LIST]
[*]AAC 5.1 Audio plays as Stereo in XBMC
[*]"speaker-test -c 6" only FL Center FR play sound
[/LIST]

[SIZE=2]I have tried tons of post but noting seems to work and had to re-install 3x because I [/SIZE]completely[SIZE=2] broke the setup :p

Ok my setup:
HTPC:
[LIST]
[*]Core 2 Q6600
[*]AMD Radeon HD 5700 Series (AMD Catalyst 14.4 Beta Driver)
[*]4 GB DRR2
[/LIST]
Reviever: ONKYO TX-SR608

I tested with several media and most videos play 5.1 in XBMC exept those with AAC, also my FLAC files with 5.1 play in Stereo.

[/SIZE]aplay -D plughw:0,3 /usr/share/sounds/alsa/Rear_Right.wav
Also doesn't play on the rear right but on the Front Right :(.

$ aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
[SIZE=2]
[/SIZE][h=3]cat /proc/asound/card*/codec#*[/h][FONT=Verdana]```
[/FONT]Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x5]: PCM AC3
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3
  Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Converter: stream=1, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  IEC Coding Type: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x02[FONT=Verdana]
```[/FONT]
[FONT=Verdana]
Any tips or help appriciated![/FONT]
[SIZE=2]
[/SIZE]

---

### Post by HSken on 2014-04-26
I found that that when I switch to "Optical/Coax" then AAC video audio works fine, but then I get horrible stuttering playback of FLAC 5.1 audio, I'm getting there but would really appreciate some help.

---

### Post by HSken on 2014-05-20
I solved all of my problems: [http://ubuntuforums.org/showthread.php?t=2225249](http://ubuntuforums.org/showthread.php?t=2225249)

---

