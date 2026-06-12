---
title: "Sound problems"
date: 2005-11-12
forum: General Help
---

### Post by Zalbor on 2005-11-12
Sound works fine in gnome, but no games and some other programs have sound. Specifically, sound isn't working in:
[list][*]Enigma
[*]Frozen bubble
[*]Super tux
[*]DOSbox
[*]ScummVM
[*]All KDE apps.[/list]
At least that's the ones I tried. Any ideas how I can fix this?

Also, this might be related: ScummVM plays most games fine, but it freezes when I try to play broken sword. I'm using the same files that I used in Hoary and it used to work.

---

### Post by Zalbor on 2005-11-15
ScummVM started working somehow, but all the rest don't. I tried to change DOSbox's setting for the sound server, but nothing works. This is the terminal output when I run it:
```
$ dosbox
CONFIG:Loading settings from config file /home/user/.dosboxrc
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA:Can't open sequencer
MIDI:Opened device:none

```

And similar ones for the other servers. Does anyone know what the problem is?

---

### Post by SlugO on 2005-11-18
This fixed the sound problem with scummvm and a few other games for me:

[How to configure sound to work properly in GNOME?]("http://ubuntuguide.org/#configuresoundproperly")

---

### Post by Copter on 2006-02-17
[QUOTE=Zalbor]ScummVM started working somehow, but all the rest don't. I tried to change DOSbox's setting for the sound server, but nothing works. This is the terminal output when I run it:
```
$ dosbox
CONFIG:Loading settings from config file /home/user/.dosboxrc
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA:Can't open sequencer
MIDI:Opened device:none

```

And similar ones for the other servers. Does anyone know what the problem is?[/QUOTE]
same problem here. its global midi problem rather than dosbox issue. i cant even find midi device in system settings. cant believe that noone can solve this here...

EDIT

```

copter@xidge:~$ sudo modprobe snd_seq_device

copter@xidge:~$ sudo modprobe snd_seq_midi

copter@xidge:~$ lsmod | grep midi
snd_seq_midi            9088  0
snd_rawmidi            24704  1 snd_seq_midi
snd_seq_midi_event      6848  2 snd_seq_oss,snd_seq_midi
snd_seq                50736  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54884  14 snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

copter@xidge:~$ dosbox
CONFIG: Using default settings. Create a configfile to change them
ALSA:Can't subscribe to MIDI port (65:0)
MIDI:Opened device:oss

copter@xidge:~$ kmid
KMid 2.0 Copyright (C) 1997,98,99,2000,01 Antonio Larrosa Jimenez. Malaga (Spain)
KMid comes with ABSOLUTELY NO WARRANTY; for details view file COPYING
This is free software, and you are welcome to redistribute it
under certain conditions

```ive found it _somewhere_ here. i **_hate_** when people are not posting exact solutions but links to some other threads that points to other thereads when some guy gives a link to some other thread... and at the end after clicking 10 links i get back where i started...

anyway now midi device is aviable in system settings now. another step is to add these mods to /etc/modules file.

copter :]

---

### Post by Copter on 2006-02-18
[https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo]("https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo")

worth checking out.

---

### Post by sallam on 2006-03-02
wow, the above link thinks we are all computer scientists here. I didn't know that I need a universal degree to listen to games. That's amazing!
Isn't there a button to click or something? what do I tell my small kid? wait till you graduate and help we with this?

How come a basic, elemental thing such as listening to midi sounds is not built-in with ubuntu distros? and why do they want us to dedicate our entire life to learn Linux, to be able to use a computer or play a simple freaking game? I don't get it. I'd rather spend my life learning how to do stuff with applications. The more transparent an operating system works, the more successful it gets.

---

