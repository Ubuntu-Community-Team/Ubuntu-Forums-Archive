---
title: "NF4 Surround, SPDIF passthrough - again"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by roberthr on 2007-01-25
Did anybody managed to make nForce 4 (CK804) audio to passthrough surround sound to external receiver?

I've read forum all over and tried several solutions but sound still remains stereo only.

speaker-test -c6 plays only front left and right speakers. Center, sub and rear speakers doesn't produce sound.

If I play DVD or DivX with AC3 (tried Totem, Mplayer and VLC), setting output to SPDIF or AC3 passthrough doesn't do anything altough there is a slight difference if I set VLC to play 5.1 or AC-52 sound. It plays something, but it's hard to tell what and it's not surround.

External receiver has blue indicator and it turns on when receiver get Dolby or DTS signal. From Windows I get that light but from Linux I don't.

Been pulling my hair out for months to achieve that but no success :-(

Soundcard is on Asus A8N-SLI SE motherboard and SPDIF connector is coax.

lspci shows:
```
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
```aplay -l:
```
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```~/.asoundrc (altough I didn't see any difference):
```
# ~/.asoundrc or /etc/asound.conf
# ALSA configuration file

##### USAGE #####
# Save this file as "~/.asoundrc" (for user-specific sound configuration) or
# "/etc/asound.conf" (for system-wide sound configuration) and specify ALSA
# device names ad described in the next section.


##### DEVICE NAMES #####
# This configuration file defines four devices for use by the user.  Those
# devices are "analog", "mixed-analog", "digital", and "mixed-digital".  The
# user may also re-define "default" to be identical to one of the above-named
# devices (i.e. to send all sound output to the digital output unless otherwise
# specified).  Use the device names as described below:
#  - "analog" outputs to the analog output directly and (at least on software
#  sound cards) blocks other audio output.  After playback completes, "queued"
#  sounds are output in sequence.
#  - "mixed-analog" mixes audio output from multiple programs into the analog
#  output (so you can hear beeps, alerts, and other noises while playing back
#  an audio stream).
#  - "digital" outputs to the digital output directly.  Since most (all?)
#  digital outputs expect 48kHz PCM audio, this may not work for some playback
#  (i.e. CD's--which are 44.1kHz PCM audio--or 32kHz audio streams from TV
#  recordings, etc.).
#  - "mixed-digital"

# All other devices created within this file are used only by the configuration
# file itself and should /not/ be used directly.  In other words, do not use
# the devices "analog-hw", "dmix-analog", "digital-hw", or "dmix-digital".


##### IMPORTANT #####
# To make this ALSA configuration file work with your sound card, you will need
# to define the appropriate card and device information for the "analog-hw" and
# "digital-hw" devices below.  You can find the card and device information
# using "aplay -l".


##### Configuration File #####

# Override the default output used by ALSA.  If you do not override the
# default, your default device is identical to the (unmixed) "analog" device
# shown below.  If you prefer mixed and/or digital output, uncomment the
# appropriate four lines below (only one slave.pcm line).
#
# Note, also, that as of ALSA 1.0.9, "software" sound cards have been modified
# such that their default "default" device is identical to the "mixed-analog"
# device.  Whether using an ALSA version before or after 1.0.9, it does no harm
# and has no affect on performance to redefine the device (even if the
# redefinition does not change anything).  Also, by using this ALSA
# configuration file, you once again have access to unmixed analog output using
# the "analog" device.
pcm.!default {
  type plug
## Uncomment the following to use "mixed-analog" by default
  slave.pcm "dmix-analog"
## Uncomment the following to use (unmixed) "digital" by default
#  slave.pcm "digital-hw"
## Uncomment the following to use "mixed-digital" by default
#  slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the card
ctl.!default {
  type hw
  card 0
}

# Alias for (converted) analog output on the card
# - This is identical to the device named "default"--which always exists and
# refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog" to access analog
# output on the card
# - Note that as of ALSA 1.0.9, "software" sound card definitions redefine
# "default" to do mixing, meaning this device is different from "default" and
# allows playback while blocking other sound sources (until playback
# completes).
pcm.analog {
  type plug
  slave.pcm "analog-hw"
}

# Control device (mixer, etc.) for the card
ctl.analog {
  type hw
  card 0
}

# Alias for (converted) mixed analog output on the card
# - This will accept audio input--regardless of rate--and convert to the rate
# required for the dmix plugin (in this case 48000Hz)
# - Note that as of ALSA 1.0.9, "software" sound card definitions redefine
# "default" to do mixing, meaning this device is identical to "default" for
# "software" sound cards.
pcm.mixed-analog {
  type plug
  slave.pcm "dmix-analog"
}

# Control device (mixer, etc.) for the card
ctl.mixed-analog {
  type hw
  card 0
}

# Alias for (converted) digital (S/PDIF) output on the card
# - This will accept audio input--regardless of rate--and convert to the rate
# required for the S/PDIF hardware (in this case 48000Hz)
pcm.digital {
  type plug
  slave.pcm "digital-hw"
}

# Control device (mixer, etc.) for the card
ctl.digital {
  type hw
  card 0
}

# Alias for mixed (converted) digital (S/PDIF) output on the card
#  - This will accept audio input--regardless of rate--and convert to the rate
#  required for the S/PDIF hardware (in this case 48000Hz)
pcm.mixed-digital {
  type plug
  slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the card
ctl.mixed-digital {
  type hw
  card 0
}

# The following devices are not useful by themselves.  They require specific
# rates, channels, and formats.  Therefore, you probably do not want to use
# them directly.  Instead use of of the devices defined above.

# Alias for analog output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.analog-hw {
  type hw
  card 0
  # The default value for device is 0, so no need to specify
#  - Uncomment one of the below or create a new "device N" line as appropriate
#    for your sound card or 
#  device 1
#  device 4
}

# Control device (mixer, etc.) for the card
ctl.analog-hw {
  type hw
  card 0
}

# Alias for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.digital-hw {
  type hw
  card 0
  device 2
#  - Comment out "device 1" above and uncomment one of the below or create a
#    new "device N" line as appropriate for your sound card or 
#  device 2
#  device 4
}

# Control device (mixer, etc.) for the card
ctl.digital-hw {
  type hw
  card 0
}

# Direct software mixing plugin for analog output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.dmix-analog {
  type dmix
  ipc_key 1234
  slave {
    pcm "analog-hw"
    period_time 0
    period_size 1024
    buffer_size 4096
    rate 48000
  } 
}

# Control device (mixer, etc.) for the card
ctl.dmix-analog {
  type hw
  card 0
}

# Direct software mixing plugin for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.dmix-digital {
  type dmix
  ipc_key 1235
  slave {
    pcm "digital-hw"
    period_time 0
    period_size 1024
    buffer_size 4096
    rate 48000
  } 
}

# Control device (mixer, etc.) for the card
ctl.dmix-digital {
  type hw
  card 0
}

```And amixer dumps:
```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 30 [97%] [on]
  Front Right: Playback 30 [97%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 29 [94%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 29 [94%] [off]
  Front Right: Playback 29 [94%] [off]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 29 [94%] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 29 [94%] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 30 [97%] [off] Capture [off]
  Front Right: Playback 30 [97%] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 29 [94%] [on] Capture [off]
  Front Right: Playback 29 [94%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Front Input',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'PCM' 'Analog In' 'IEC958 In'
  Item0: 'PCM'
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 14 [93%] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 29 [94%] [on] Capture [off]
  Front Right: Playback 29 [94%] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [on]
  Front Right: Capture 0 [0%] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '6ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

```

---

### Post by Innova on 2007-03-20
I am now having the same problem...I get audio out of my SPDIF, but not ac3.

---

### Post by westis78 on 2007-04-10
I seem to have the same problem. (same chip too, mobo is asus a8n-sli deluxe)

I don't use the digital out but "speaker-test -c6" leaves all but FR and FL silent. When I enable "Duplicate Front" I get sound on all speakers (a 5.1-system connected with 3 analog plugs) but of course that is only a copy of the front speakers and no real surround. 

When I boot into windows XP I get full surround.

---

### Post by pivot@pivpoint.no on 2007-06-27
*bump*

same mobo... stereo output.

---

### Post by drejom on 2007-11-07
anyone had any luck with this on gutsy?

---

### Post by sudo_t43p on 2007-11-21
Hi,

I have also A8N-SLI but I cannot get any sound via S/PDIF? 

BR,
Chrisse

---

### Post by sudo_t43p on 2007-11-21
> **sudo_t43p said:**
> Hi,

I have also A8N-SLI but I cannot get any sound via S/PDIF? 

BR,
Chrisse

Nevermind, this solved the problem:

#amixer sset 'IEC958 Playback AC97-SPSA' 0
#sudo alsactl store

---

### Post by stokkes on 2007-11-23
Gonna bump this thread.

I'm having the exact same issue as the OP.

FR/FL speakers work fine through S/PDIF, however no Dolby, DTS, AC3 is working at all.

Why the hell is this so complicated? Like the OP, I boot into Windows and get 5.1 so I know it's not a hardware issue.

---

### Post by Greenskycity on 2007-12-26
I'm going to add fuel to the fire.  I've got this exact same setup- I run my computer to my stereo and use my RCA style digital out of my computer to get stereo sound, but there is no 5.1.  I've got the same chipset and in WIndows the 5.1 works also.
    I have got everything on my computer working beautifully except for this, so I am a little hesitant to try most of what I've read on here because stereo is still sound, better stereo than crashing my whole installation.  Any ideas from the forum?
Green

---

### Post by Jouse on 2008-01-12
And a bump. Also having the same problem with Asus A8N-SLI.
SPDIF works fine for stereo, but can't get 5.1 working. 

If anyone has a working configuration for this chip, please help!

---

### Post by Yellow Pasque on 2008-01-12
You folks might want to look at this thread: [http://gentoo-wiki.com/HOWTO_Dolby_Digital_and_DTS](http://gentoo-wiki.com/HOWTO_Dolby_Digital_and_DTS)

---

### Post by Jouse on 2008-01-12
Good news, I got it working. Below is my systeminfo and the steps needed to make it work.

lspci -v:
```
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=256]
        Memory at d5003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
```

aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

aplay -L:
```
default:CARD=CK804
    NVidia CK804, NVidia CK804
    Default Audio Device
front:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Front speakers
surround40:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
```

I don't have .asoundrc and all alsa configfiles are untouched. 

1) alsamixer -> **Unmute IEC958**  & **set IEC958 Playback AC97-SPSA to 0** & **IEC958 Playback Source to PCM**

2) mplayer usage:
```
mplayer -ao alsa:device=hw=0.0 -ac hwac3, file.ac3 
```
This command works also for non-AC3 audio (note the trailing comma after hwac3. 

For MythVideo I have:
```
mplayer -ao alsa:device=hw=0.0 -ac hwac3,hwdts, -quiet -fs -zoom %s 
```

---

### Post by crispy_chunks on 2008-01-18
Bump.

I have the same problem. Surround not working as intended on this board! Only frontspeakers playing when i to speaker-test -c6

---

### Post by crispy_chunks on 2008-01-18
> **Jouse said:**
> Good news, I got it working. Below is my systeminfo and the steps needed to make it work.

lspci -v:
```
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=256]
        Memory at d5003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
```

aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

aplay -L:
```
default:CARD=CK804
    NVidia CK804, NVidia CK804
    Default Audio Device
front:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Front speakers
surround40:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
```

I don't have .asoundrc and all alsa configfiles are untouched. 

1) alsamixer -> **Unmute IEC958**  & **set IEC958 Playback AC97-SPSA to 0** & **IEC958 Playback Source to PCM**

2) mplayer usage:
```
mplayer -ao alsa:device=hw=0.0 -ac hwac3, file.ac3 
```
This command works also for non-AC3 audio (note the trailing comma after hwac3. 

For MythVideo I have:
```
mplayer -ao alsa:device=hw=0.0 -ac hwac3,hwdts, -quiet -fs -zoom %s 
```

I have the same output as you from aplay, but my lspci is:

```
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=256]
        Memory at d6003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
```

I have tried your mplayer configuration, but alas (or alsa hehe), still only front speakers playing :(

I have roughly the same problems as the other guys, but i also have some other strange symptoms: alsamixer cant control volume, but i can turn sound off by setting IEC958 Playback AC97-SPSA to 1 (or something else).

Also normal mp3's actually play on all speakers through amarok (dont think its surround tho, just upsampled by the settings in amarok). Also [this]("http://www.halfgaar.net/resources/chan-id.zip") wave file should be surround, but in amarok ONLY plays the two front speakers.

---

### Post by crispy_chunks on 2008-01-19
A little more info for those interested! :D

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2637](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2637)

Gotta read it through, will post if i successfully get surround!

---

### Post by purduephotog on 2008-03-24
A8n-SLI Premium, same problems.

Mythbuntu 8.04Beta, all updates.

I did follow the instructions here and managed to get the Optical link laser to turn on- now my  stereo recognizes the digital feed in on the DVR but nothing ever comes of it.  I've tried every combination on the system setup and still can not get sound out over the optical.  I do have FR/FL speaker output, but no rear speaker output for the speaker-test -c6.

Suggestions very much welcome- and if you have a working A8N-SLI-Premium board I would love to have a clone of your configs ;)

---

### Post by wyrdvans on 2008-04-03
Any luck with this?  I'm also having this issue.  Front speakers work through spdif(coax) but can't get ac3 on it.

---

### Post by Anthill on 2008-04-30
Same config, same problem, same luck in fixing it.  :(

---

### Post by sastian on 2008-05-20
same issue here
i get front and center to work but no rear
any get this to work on a nVidia CK804 AC'97 (Realtec chip)

sastian@Media-Center:~$ lspci | grep "audio" 
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

btw:
speaker-test -c6 -D plug:surround51 yeilds only FR & FL while a DVD seems to also have center and subs.. may be due to the reciever but worth noting.

---

