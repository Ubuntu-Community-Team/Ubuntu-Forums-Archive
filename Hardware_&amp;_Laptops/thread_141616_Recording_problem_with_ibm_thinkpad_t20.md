---
title: "Recording problem with ibm thinkpad t20"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by ReiKn on 2006-03-08
I've tried to get my laptop (ibm thinkpad t20) record sound from the internal microphone. Microphone works as when i choose microphone as the recording source from alsamixer I can hear sound. Problem is that I can't record this sound. Gnome-sound-recorder just hangs on recording or produces a file of 4 bytes. Command line recording tools (like rec) also produce the same kind of 4b file.

Also when trying to use wengophone test call (which is just supposed to echo what you say) i can hear myself when speaking but the echo never comes.

When i try to record with Audacity the terminal output is an error message "PortAudio: read interrupted!". I've tried to follow "how to configure sound properly" from ubuntuguide but it doesn't help in my case. Sound card is of type cs46xx.

```

$ lspci -v | grep -i audio
0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

```

```

$ lsmod | grep snd
snd_cs46xx             88744  2
gameport               15016  2 snd_cs46xx
snd_ac97_codec         98620  1 snd_cs46xx
snd_ac97_bus            2176  1 snd_ac97_codec
snd_pcm_oss            55552  0
snd_mixer_oss          19936  1 snd_pcm_oss
snd_pcm                92488  4 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10984  2 snd_cs46xx,snd_pcm
snd_seq_dummy           3684  0
snd_seq_oss            35328  0
snd_seq_midi            9312  0
snd_rawmidi            24960  2 snd_cs46xx,snd_seq_midi
snd_seq_midi_event      7008  2 snd_seq_oss,snd_seq_midi
snd_seq                52752  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24900  2 snd_pcm,snd_seq
snd_seq_device          8780  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55908  13 snd_cs46xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9824  1 snd


```


Alsamixer has quite a few alternatives and alternative combinations so i don't really know which ones should be enabled. This is my configuration at the moment:
```

$ amixer

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Front Left: Playback 58 [92%] [on]
  Front Right: Playback 58 [92%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [on]
  Front Right: Playback 0 [0%] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 22 [71%] [on]
  Front Right: Playback 22 [71%] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 28 [90%] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities:
  Mono:
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Input',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities:
  Mono:
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 11 [73%] [off]
  Front Right: Capture 11 [73%] [off]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'ADC',0
  Capabilities: volume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 32767
  Front Left: 0 [0%] Capture [on]
  Front Right: 0 [0%] Capture [on]
Simple mixer control 'DAC',0
  Capabilities: volume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 32767
  Front Left: 22942 [70%] Capture [off]
  Front Right: 22942 [70%] Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

```

---

### Post by ashrack on 2006-08-31
I identical problems, even with GNOME-SOUND-RECORDER and alsa-record only producing 4KB files no matter what settings I use, and alsamixer I'have configure correctly per this guide:
[http://alsa.opensrc.org/index.php?page=cs46xx](http://alsa.opensrc.org/index.php?page=cs46xx)

---

### Post by jame on 2006-09-12
:confused: Same problem. 

The sound device should be right. I can hear my voice from mic.

1:
Gnome-media Sound Recorder breaks down after twice clicks of "record" button.
2:
Skype doesn't properly work. I can hear the other side but who can't.

I would like to appreciate anybody who is concerned about this bug.=D> 

Jame

---

### Post by paulistano on 2006-11-17
Same bug here with my T21. Any suggestions? :???:

---

### Post by Blue_J on 2006-11-19
I have the same problems.  The sounds card is a Hurcles with CS4614/24 sound chip.  It plays back fine and the mic is fed through to the speakers but it won't record.

I was using MEPIS off and on for a couple of years and just installed Ubuntu for the first time.  I really love the clean look and response of Ubuntu but one of my main uses is as an audio work station for band recordings.

Sound Recorder fails totally and Audacity works for playback but won't record from the mike.  Alsa mixer shows the mic as set for capture but the level control doesn't work.  There are other controls labeled capture and their level control do work but it's not helping.

---

### Post by davbeck on 2006-12-11
I also have the same problem and I was just wondering if anyone has this problem with anything besides an IBM with Ubuntu (not K, Ed, or X Ubuntu)? I personally have an IBM a21m and will be forced to revert back to windows if I can't solve the problem.](*,)

---

### Post by eric.boon on 2006-12-19
Just a "me too" - I recognize all of the symptoms mentioned above :(

Dell Dimension 4100 with CS46xx sound card, running debian testing.
Seems CS46xx support in general is kinda borked :(

---

### Post by eric.boon on 2006-12-19
See also
[here](http://www.linuxquestions.org/questions/showthread.php?t=438831) and [here](http://forum.skype.com/index.php?showtopic=10858)

I was able to record some sound using the command line tools **arecord** and **aplay**.

plug in a microphone on the mic in of the soundcard and open up the gnome-alsamixer.
1. Mute everything that looks like an input channel, including all Mic's (I've got two of those in my mixel panel)!
2. Check the Rec-tockboxes on the first 'Mic' and 'Capture' channels, and on the 'ADC' channel and put the sliders to approximately 90% of their maximum.
3. on the command line type:```
arecord -D plughw:0,0 test.wav
``` and start talking into the mic. Stop recording by pressing Ctrl-C.
4. Make sure you didn't mute your output channel (Master, PCM, DAC) ;-) and replay your recording with ```
aplay test.wav
```

It's not as fancy as gnome-sound-recorder, but it works...

(edit)
And instead of gnome-sound-recorder, I just tried Audacity. After leveling down the mic input to about 0.7, I got perfect recording quality! :D

---

### Post by tedrogers on 2006-12-23
Well this worked for me....thanks...after a long battle of posting on Ubuntuformus and bug posts on Launchpad ([https://launchpad.net/distros/ubuntu/+ticket/2685](https://launchpad.net/distros/ubuntu/+ticket/2685)) you have helped me to get it to record using arecord, aplay and alsamixer.

After a restart it also worked with Audacity! This is a first for me.

However it still doesn't work with the standard gnome sound recorder, which seems very odd indeed...it just hangs totally and then crashes my gnome bar at the top.

Also, I cannot get Skype to work at all which is really bugging me now. The whole reason I need the mic working is to use VoIP.

Any ideas at all?

---

### Post by stelloscuro on 2007-01-07
Have you tryed setting adc to 'capture' in the alsamixer, this solved all of my problems.  Cannot get Skype to work though!

---

### Post by tedrogers on 2007-01-07
Yes, I managed to get things like Audacity working by selecting capture on Mic, Capture and ADC. So I know the mic is recording sound and playing it back fine. I can even meter the input and see the level change as I talk or tap the mic sound hole on the laptop wrist wrest.

However, I too still cannot get Skype to work though or Gizmo either. This is too weird for me...it doesn't make sense at all.

All I can guess is that Skype for some reason is changing the capture setting automatically and rendering it unoperational, although this doesn't explain why Gizmo doesn't work (unless it is doing the same sort of thing as Skype is).

So....anyone else out there got any more success with this?

---

### Post by mattotoole on 2007-03-08
Bump.

Same problem here.  I'm mostly concerned with VOIP (Skype, Gizmo, etc).

---

### Post by tedrogers on 2007-03-09
I managed to get Gizmo working finally, but still not skype.

I just set everything to use OSS instead of alsa, but still make sure that all you captures, mic etc are all selected in alsa-mixer.

In gizmo make sure it is use /dev/dsp (OSS drivers) and not alsa.

---

### Post by petru on 2007-03-11
I tried to compile new alsa drivers (1.0.14rc3). Then I was able to use arecord and aplay on my T21. Skype did not work however.. I tried to edit file .asoundrc in my home dir like this (found in skype support forum):

```

pcm.asymed {

       type asym

       playback.pcm "dmix"

       capture.pcm "dsnoop"

}

pcm.!default {

       type plug

       slave.pcm "asymed"

}

```

Restarted computer and Skype, Wengophone do work now. Sound Recorder does not...
I hope this could help you too!

---

