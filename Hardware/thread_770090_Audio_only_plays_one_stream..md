---
title: "Audio only plays one stream."
date: 2008-04-27
forum: Hardware
---

### Post by ^graff_epsilon on 2008-04-27
Upon the install of 8.04 LTS, my sound will only play from one source, and even if I close that source, I have to restart the other program that I am trying to use first. I have seen this bug/problem reported before, but saw something that looks interesting in the verbose report from pulseaudio. Take a look at the red section and tell me what you think. I have no idea whether it's significant.

dchartas@eng-250412156:~$ sudo pulseaudio -v
I: core-util.c: Successfully gained nice level -11.
W: main.c: This program is not intended to be run as root (unless --system is specified).
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: module-hal-detect.c: Trying capability alsa
I: alsa-util.c: Couldn't open PCM device front:0: Device or resource busy
I: alsa-util.c: Couldn't open PCM device surround40:0: Device or resource busy
I: alsa-util.c: Couldn't open PCM device surround41:0: Device or resource busy
I: alsa-util.c: Couldn't open PCM device surround50:0: Device or resource busy
I: alsa-util.c: Couldn't open PCM device surround51:0: Device or resource busy
I: alsa-util.c: Couldn't open PCM device surround71:0: Device or resource busy[COLOR="Red"]
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0"): initialization failed.[/COLOR]
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 0 "alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 4 fragments of size 4352 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
I: module.c: Loaded "module-alsa-source" (index: #0; argument: "device_id=0 source_name=alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0").
I: module-hal-detect.c: Loaded 1 modules.
I: module.c: Loaded "module-hal-detect" (index: #1; argument: "").
I: module.c: Loaded "module-esound-protocol-unix" (index: #2; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #3; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #4; argument: "").
I: module-default-device-restore.c: Saved default sink 'alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0' not existant, not restoring default sink setting.
I: module.c: Loaded "module-default-device-restore" (index: #5; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #6; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #7; argument: "").
I: module.c: Loaded "module-gconf" (index: #8; argument: "").
I: module.c: Loaded "module-x11-publish" (index: #9; argument: "").
I: main.c: Daemon startup complete.
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...

---

### Post by yousillygoose on 2008-05-17
was this ever resolved because I am having the same problem

---

### Post by TheMemphisExperience on 2008-05-18
I have a similar situation.

I can use audacious and firefox to play sound simultaneously, but exaile, mplayer, and others do not want to share.

I have Audacious, ZNES( in Wine), and Firefox streaming something. I don't know where to go to find out what is in charge of these operations sound wise.

---

### Post by k0rv3n on 2008-05-18
Hey. I had a similar problem.
Check that all your programs are using ALSA and not any other driver. That was the problem I had :)

---

