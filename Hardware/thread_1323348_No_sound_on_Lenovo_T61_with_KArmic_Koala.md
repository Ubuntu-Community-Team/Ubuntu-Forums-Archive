---
title: "No sound on Lenovo T61 with KArmic Koala"
date: 2009-11-11
forum: Hardware
---

### Post by venturax on 2009-11-11
Hi all,

Im a complete newbie to ubuntu and linux in general. Having wiped my Vista and replaced it with Ubuntu, I'm facing an annoying problem.

Theres no audio at all. I have tried to toggle almost all switches in the sound controls. I have tried to run alsamixer to crank everything to max. with no result ](*,)

Having googled without getting an answer, I'm now desperate!

What to do and what to check?

alsamixer reports : Card: HDA Intel, Chip: Analog Devices AD1984

---

### Post by venturax on 2009-11-11
amixer -l gives:
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB]
  Front Right: Playback 39 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'IEC958',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [off]
  Front Right: Playback 39 [100%] [0.00dB] [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'PCM' 'ADC'
  Item0: 'ADC'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 39 [72%] [0.00dB] [off]
  Front Right: Capture 39 [72%] [0.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 39 [72%] [0.00dB] [off]
  Front Right: Capture 39 [72%] [0.00dB] [off]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Docking Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Docking Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Internal Mic' 'Mix' 'Docking-Station'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Internal Mic' 'Mix' 'Docking-Station'
  Item0: 'Mic'
Simple mixer control 'Internal Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Speaker',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]

```

cat /proc/asound/card :
```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe020000 irq 17

```

cat /proc/asound/devices:
```

  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0- 0]: hardware dependent
  8: [ 0]   : control

```

---

### Post by venturax on 2009-11-12
I have tried the following with no result:
```
sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload
```

```
cat /proc/asound/cards
``` still give the same result as in the original post.

Tried:
```
sudo gedit /etc/modprobe.d/alsa-base-conf
```

and commented out
```
# options snd-hda-intel power_save=10 power_save_controller=N
```
and added a new line
```
options snd-hda-intel probe_mask=1 model=thinkpad
```

Still i get no sound. HELP!!! Im getting desperate :sad::sad::sad:

---

### Post by nigamp on 2009-11-12
> **venturax said:**
> I have tried the following with no result:
```
sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload
```

```
cat /proc/asound/cards
``` still give the same result as in the original post.

Tried:
```
sudo gedit /etc/modprobe.d/alsa-base-conf
```

and commented out
```
# options snd-hda-intel power_save=10 power_save_controller=N
```
and added a new line
```
options snd-hda-intel probe_mask=1 model=thinkpad
```

Still i get no sound. HELP!!! Im getting desperate :sad::sad::sad:
options snd-hda-intel probe_mask=1 model=thinkpad 
i think this shud be 
options snd-hda-intel probe_mask=1 model=laptop


another thing ..i m sure u must having sound wen u plug in ur headphones.....is it ?

---

### Post by venturax on 2009-11-13
> **nigamp said:**
> options snd-hda-intel probe_mask=1 model=thinkpad 
i think this shud be 
options snd-hda-intel probe_mask=1 model=laptop


another thing ..i m sure u must having sound wen u plug in ur headphones.....is it ?

Tried it and no luck. Theres no sound in the headphones either :-(

---

### Post by klemes on 2009-11-13
Try : 'options snd-hda-intel model=auto' and let Ubuntu get the type of the card from the BIOS.It's the safest way.

---

### Post by venturax on 2009-11-16
> **klemes said:**
> Try : 'options snd-hda-intel model=auto' and let Ubuntu get the type of the card from the BIOS.It's the safest way.

Also tried this, but still no sound. I will try to make a live cd of hardy to see if audio works in a previous edition... *sigh*

I would hate to migrate back to Vista, but I just cant do without audio.

---

### Post by AMindUnited on 2009-11-19
Have you read this? (I had no audio in my t61 after 9.10 install, and this fixed it)
[Karmic. Pluseaudio home folder is not ours]("http://ubuntuforums.org/showthread.php?t=1308237&highlight=pluseaudio")

there's also this one:
[sound-card-not-detected-ubuntu-910-fix-it]("http://h3manth.com/content/sound-card-not-detected-ubuntu-910-fix-it")
Hope that keeps you from goin' back to windoze

---

### Post by venturax on 2009-11-24
Still no love :-(

I will try to brun the Koala iso again and run entirely from the CD, to see if somehow i have screwed up something.. Will also try with an older version as well.. 

Will post the results.

Thanks all for the help so far. Really appriciated

---

### Post by rasan on 2009-11-24
Try This.

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by venturax on 2009-11-27
> **AMindUnited said:**
> Have you read this? (I had no audio in my t61 after 9.10 install, and this fixed it)
[Karmic. Pluseaudio home folder is not ours]("http://ubuntuforums.org/showthread.php?t=1308237&highlight=pluseaudio")

there's also this one:
[sound-card-not-detected-ubuntu-910-fix-it]("http://h3manth.com/content/sound-card-not-detected-ubuntu-910-fix-it")
Hope that keeps you from goin' back to windoze

An update! I now have audio!! ):P
What exactly solved it I dont know (thats probably the worst part),
I tried all suggestions, besides Rasans.

After all my attempts i revisited my sound preferences and found that output was directed to headphones. Switching to analog output i got sound. That didnt work to begin with, so some of the suggestions did the trick.

Thanks to all, who helped solve this problem. Plans for switching back to Vista are now cancelled \\:D/

---

### Post by oxtus on 2009-12-13
Help!

I am in the same situation. I have this in Alsamixer:

[IMG]http://farm3.static.flickr.com/2609/4180970985_652b82986d_b.jpg[/IMG]

Does it seem right?

Thanks

---

### Post by gvhill on 2009-12-25
I have Lenovo T500. I have read on another post that Bios records state of mute key. I simply went into windows and unmuted speakers. When back in Ubuntu speakers now work. Hope this helps someone. Was very frustrating problem for a few days.

---

### Post by droadtrip on 2009-12-25
[FONT=Georgia][SIZE=3][COLOR=Indigo]I have a Lenovo G3000 Laptop and found the best way to control my audio settings is by using "Pulse Audio" which I got from Add/Remove Programs.[/COLOR][/SIZE][/FONT]

---

### Post by venturax on 2010-01-04
> **oxtus said:**
> Help!

Does it seem right?

Thanks
My alsamixer looks like this:
[IMG]http://engenius.dk/misc/dump.png[/IMG]

---

