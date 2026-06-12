---
title: "Microphone not working in Skype"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by Cappy on 2007-02-04
I really really need some help! I've searched high and low and nothing has helped so far!

I've gotten the microphone to work in the gnome sound recorder but the microphone will not work in Skype (or Audacity - just helpful information, I don't need it). Sound works PERFECTLY (using emu10k1, I believe) in skype and all applications. Skype is configured for ALSA.

I tried fixing it with a suggestion from another post:
[http://www.ubuntuforums.org/showthread.php?t=311959](http://www.ubuntuforums.org/showthread.php?t=311959)

Now my microphone completely doesn't work. I did the same procedure but undid what I did and my mic STILL doesn't work (in anything anymore).

I'm using the "Ubuntu Ultimate" edition, basically just Ubuntu with automatix stuff already downloaded and installed.
I'm using an Audigy 4 with ALSA (I guess, it's on automatic). The mic input that works for me is called Multichannel/PT. 

Any help is greatly appreciated!

---

### Post by Cappy on 2007-02-04
here is my amixer output:

```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined cvolume cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 31
  Mono: Playback 100 [100%]
  Front Left: Capture 31 [100%] [on]
  Front Right: Capture 31 [100%] [on]
Simple mixer control 'Tone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Bass',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control 'Treble',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control 'PCM',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 100
  Front Left: Capture 0 [0%]
  Front Right: Capture 0 [0%]
Simple mixer control 'PCM Center',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%]
Simple mixer control 'PCM Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%]
  Front Right: Playback 100 [100%]
Simple mixer control 'PCM LFE',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'PCM Side',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%]
  Front Right: Playback 100 [100%]
Simple mixer control 'PCM Surround',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%]
  Front Right: Playback 100 [100%]
Simple mixer control 'Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 80 [80%]
  Front Right: Playback 80 [80%]
Simple mixer control 'Surround',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%]
  Front Right: Playback 0 [0%]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 0 [0%]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 0 [0%]
Simple mixer control 'Side',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%]
  Front Right: Playback 0 [0%]
Simple mixer control 'Synth',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] Capture 0 [0%]
  Front Right: Playback 0 [0%] Capture 0 [0%]
Simple mixer control 'Wave',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 80 [80%]
  Front Right: Playback 80 [80%]
Simple mixer control 'Line',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [off]
  Front Right: Capture 31 [100%] [off]
Simple mixer control 'CD',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [off]
  Front Right: Capture 31 [100%] [off]
Simple mixer control 'Mic',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 31 [100%] [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic2'
Simple mixer control 'Video',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'Phone',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 0 [0%] [off]
Simple mixer control 'IEC958 Optical',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] Capture 0 [0%]
  Front Right: Playback 0 [0%] Capture 0 [0%]
Simple mixer control 'IEC958 Optical Raw',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Mono
  Limits: Capture 0 - 15
  Mono: Capture 15 [100%] [off]
Simple mixer control 'Aux',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'Aux2',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] Capture 0 [0%]
  Front Right: Playback 0 [0%] Capture 0 [0%]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'AMic',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%]
  Front Right: Playback 0 [0%]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] Capture 0 [0%]
  Front Right: Playback 0 [0%] Capture 0 [0%]
Simple mixer control 'Audigy Analog/Digital Output Jack',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Audigy CD',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] Capture 0 [0%]
  Front Right: Playback 0 [0%] Capture 0 [0%]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

```

---

### Post by citizenofnowhere on 2007-02-04
Try changing your sound mode in skype from ALSA to OSS (I know OSS isn't great but skype  likes it more, ALSA support is still new). Then close any other application that could possibly be using sound, and restart skype. 

The major problem with OSS is that it allows only one program to access the sound at any time, which is probaby why your audacity isn't detecting the input either - there could be a setting somewhere set to oss. SO just try closing everything like I've said above.

Good luck!

---

### Post by oneiota on 2007-02-05
I don't have a solution, but I accidentally found a work around on my own system.  I accidentally plugged my mic into my speaker socket and the speaker jack into the mic socket and it worked.  It shouldn't be this way, but until I find the right fix myself, I can at least use Skype.

For interest, if I boot the same machine (same headset, etc) into Windows, Skype works well and the speaker and mic work as one would expect - that is, when plugged into the correct sockets.

---

### Post by borobudur on 2007-02-07
I have the same problem and I haven't found a way to fix it. 
It worked at the beginning properly.

Could it be that the problem is that I installed some multimedia plug-ins like ffmpeg, totem-xine, gstreamer, sox, faad and lame? I know, some are for the picture but some are also for the sound, aren't they?

---

### Post by Cappy on 2007-03-04
I now have fixed my problem after 2 weeks of running Ubuntu =) I thought it just wouldn't work because I thought I was doing EVERYTHING I could think of. I was actually considering just buying a new audio card.

One big problem was that I needed to leave the microphone on "ALSA" in the (System --> Preferences -- Sound) menu. It might also work on OSS (and also use OSS inside of Skype too, if you do this). Most importantly, I needed to turn the right "capture on".

```

Simple mixer control 'Analog Mix',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] Capture 0 [0%]
  Front Right: Playback 0 [0%] Capture 0 [0%]

```

This was the setting that I needed to change. How did I find it? _ I went to the **Volume Control** (that's the volume icon on the top right of your screen [in GNOME]), I then went to **Edit-->Preferences** and checked every check box. I then went to the **Capture** tab and raised the volume for each control to maximum. You now want to make sure the **microphone icon** below each icon does NOT have an "X" on it. You should definitely see a **Microphone** in the **Capture** tab. Also make sure the "microphone" icon DEFINITELY isn't muted on the **Master Capture**. _

You can use the command **vumeter -r &** to make sure your microphone is working (just leave it on while you are changing your settings, I tap or blow on my microphone while I am changing settings to make sure I see it on the Recording Level Monitor).
Hopefully, it will work, otherwise you may need to play around a little bit with it. For me it was that I needed to use both "Microphone" and "Analog Mix Capture" on my Audigy 4 Non-Pro. For my onboard sound card (A7N8X Deluxe - Nforce2) I had to use the console program "alsamixer" as described at the bottom of this post (The Volume Control doesn't have all the functionality of alsamixer) - [http://www.ubuntuforums.org/showthread.php?t=255071#10]("http://www.ubuntuforums.org/showthread.php?t=255071#10")

---

### Post by keerikkadan on 2007-03-12
try restarting after chosing same sound device in skype and volume control tab

---

### Post by klett on 2007-03-15
My skype works perfectly after following cappy's advice:

> This was the correct setting for me. How did I find it? I went to the Volume Control, I went to Edit-->Preferences and checked every check box. I then went to the Capture tab and raised the volume for each control to maximum. You now want to make sure the "microphone" icon below each icon does NOT have an "X" on it. You should definitely see a "Microphone" in the Capture tab. Also make sure the "microphone" icon DEFINITELY isn't muted on the "Master Capture".

My system:

Ubuntu 6.06
Thinkpad r60

Thanks!!

---

### Post by Monosabio on 2007-06-01
> **Cappy said:**
> I now have fixed my problem after 2 weeks of running Ubuntu =) I thought it just wouldn't work because I thought I was doing EVERYTHING I could think of. I was actually considering just buying a new audio card.

This was the setting that I needed to change. How did I find it? _ I went to the **Volume Control** (that's the volume icon on the top right of your screen [in GNOME]), I then went to **Edit-->Preferences** and checked every check box. I then went to the **Capture** tab and raised the volume for each control to maximum. You now want to make sure the **microphone icon** below each icon does NOT have an "X" on it. You should definitely see a **Microphone** in the **Capture** tab. Also make sure the "microphone" icon DEFINITELY isn't muted on the **Master Capture**. _


After spending more than 4 hours trying to find a solution I've decided to reinstall Ubuntu, but I still  wasn't able to record with my microphone  and could not use voice capabilities with skype. Then I read your post and follow your advice. You are great man ! Your tip worked perfectly for me ! Thanks !:D

---

### Post by euchrid on 2007-06-07
If the above doesn't work for you, try updating the Alsa drivers. See this post: [http://ubuntuforums.org/showthread.php?p=2798055#post2798055]("http://ubuntuforums.org/showthread.php?p=2798055#post2798055")

---

