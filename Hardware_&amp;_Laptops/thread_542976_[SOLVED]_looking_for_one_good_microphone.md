---
title: "[SOLVED] looking for one good microphone"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by univremonster on 2007-09-04
Hey everybody,

At risk of being called a troll, I will say that the biggest problems I've had with Ubuntu deal with a lack of drivers or hardware support.  That said, I am trying to use Skype, which I have working wonderfully, except that I don't have a microphone which makes conversing difficult.  I've seen a lot of people with sound problems on Ubuntu, so I thought I'd just take a quick poll to see if anyone had anything that worked really wonderfully, preferably plug and play, with Fiesty.

---

### Post by gautada on 2007-09-04
> except that I don't have a microphone which makes conversing difficult. I've seen a lot of people with sound problems on Ubuntu

The sound issues are typically associated with sound cards.  I believe a better "poll" would be for supported sound cards.  That said now a quick note on sound cards/systems: 

1.) Microphones are just inputs into the sound card if your sound card is working more than likely the microphone is as well.
2.) Stay away from on-board sound cards.  I have personally had lots of trouble with noise and electrical interference from these.  Spend the money and get a real sound card.
3.) Keep in mind that a mic will pickup the sound coming from your speakers so a mic/speaker headset is probably something you want to look into.

I use a microphone/headset combo for skype that came with some dictation software purchased years ago.

---

### Post by univremonster on 2007-09-04
I think I have a sound card built into the mobo, though I'm not sure, this was the first computer I built and it's a miracle the fans moved much less that it turned into the fully functional computer it is today.  I believe I have a sound card because when I type ```
amixer
``` into the terminal I get ```
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 51 [80%] [-13.00dB] [on]
  Front Right: Playback 51 [80%] [-13.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [on]
  Front Right: Playback 0 [0%] [-35.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-64.00dB] [off]
  Front Right: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [on]
  Front Right: Playback 0 [0%] [-35.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 52 [80%] [17.00dB] [on]
  Front Right: Playback 52 [80%] [17.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [off]
  Front Right: Playback 0 [0%] [-35.00dB] [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 65 [100%] [30.00dB] [off]
  Front Right: Playback 65 [100%] [30.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 35
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 35
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 35
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'

```

not to mention my speakers work fine.  So I just get any headset and I'm ready to go?

---

### Post by gautada on 2007-09-05
Yeah pretty much any head set will work.  Keep in mind that the mic/speaker headset has two plugs.  One for the mic and one for the speaker.  You might have to unplug your speakers to get the headset speaker plugged into the sound card.  I have speaker/mic jacks on the front of my PC so I can override my primary speakers without unplugging, when I need to use VOIP.  For headsets check out [Labtec]("http://www.labtec.com/index.cfm?countryid=1001&languageid=1&page=gear/listing&crid=8&crid2=9").

---

### Post by gautada on 2007-09-05
Also, don't forget that your headset volumes probably needs to be adjusted.  Use alsamixer or gnome-volume-control from the terminal.  You can use System->Preferences->Sound to test before launching your VOIP client.

---

