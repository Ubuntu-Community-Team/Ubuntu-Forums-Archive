---
title: "Ubuntu uses the wrong sound card"
date: 2005-01-29
forum: Installation &amp; Upgrades
---

### Post by Titeuf on 2005-01-29
Hi all,
I have a SB Live and a bttv-based tv tuner card and the installer detected both of them, and loaded for both of them their kernel modules.
But it configures the bttv card to be my primary sound card, but as this card doesn't have sound output, I can't hear any sounds.
I can switch from both cards with alsamixer using alsamixer -c 0 (bttv) and alsamixer -c 1 (bttv)
So can anyone help me with making the SB Live card the standard one ?

---

### Post by rudi on 2005-01-30
Hi,
  I have only one soundcard, so i can't test if it works, but you might want to look at: **/usr/share/alsa/alsa.conf **search for the section: # defaults. There are lines like:
   ```

 defaults.ctl.card 0
 defaults.pcm.card 0
 defaults.pcm.device 0
 defaults.pcm.subdevice -1
 defaults.rawmidi.card 0
 defaults.rawmidi.device 0
 defaults.rawmidi.subdevice -1
 defaults.hwdep.card 0
 defaults.hwdep.device 0
 defaults.timer.class 2
 defaults.timer.sclass 0
 defaults.timer.card 0
 defaults.timer.device 0
 defaults.timer.subdevice 0
``` 
  perhaps if you change the 0 to 1 it might work, but i'm not sure.

---

### Post by Titeuf on 2005-01-30
This didn't solve my problem.
Alsamixer now opens automatically the good sound card, but other programs like rhythmbox still don't work. It says: "Couldn't open source for writing"

---

### Post by Titeuf on 2005-01-30
I can have sound with beep-media-player when I configure the output plugin.
But I'm thinking of this: Ubuntu automatically loads the module snd_bt87x, which I don't need. How can I stop it autoloading this module ?

---

### Post by Titeuf on 2005-01-30
From [url=https://bugzilla.ubuntu.com/show_bug.cgi?id=1293#c1]:
> 
To switch it around, I added the following (from the mentioned website, just
changed for my needs) to /etc/modprobe.d/aliases:

alias snd-card-0 snd_emu10k1
options snd_emu10k1 index=0

alias snd-card-1 snd_bt87x
options snd_bt87x index=1

My sound now, but with gstreamer-apps like rhythmbox, I have to use the esd output of gstreamer. But I want to use the alsa-output (as I have a SB Live, it supports hardware mixing, so I don't need a sound daemon).
When I open gstreamer-properties, and test with alsa, I get: "Failed to build testpipeline for ALSA" (or something like that, this is just a translation)

---

### Post by Marquis_de_Carabas on 2005-01-30
I have the same problem. I've got a Soundblaster Audigy card and an onboard sound chipset as well. Obviously I want to use the Soundblaster, but the onboard sound is set up as the primary soundcard.

I found a workaround (I forget where I found it now), which involves typing the following in a terminal:

> sudo rm /dev/dsp
sudo ln -s /dev/audio1 /dev/dsp

This works (I've actually put it in a shell script to make it quicker and easier) perfectly - all sound from every app then comes through the Audigy - but I'm sure there must be a better way.

Have you checked your bios to see if you can disable the unwanted sound chipset there? Unfortunately my bios doesn't provide that option, but if yours does then this may solve your problem.

By the way, the command I originally found was along the lines of "sudo mv /dev/dsp /home/backup/" but after this had worked a few times I adapted it to the version above.

---

### Post by Titeuf on 2005-01-30
[QUOTE=Marquis_de_Carabas]I have the same problem. I've got a Soundblaster Audigy card and an onboard sound chipset as well. Obviously I want to use the Soundblaster, but the onboard sound is set up as the primary soundcard.

I found a workaround (I forget where I found it now), which involves typing the following in a terminal:



This works (I've actually put it in a shell script to make it quicker and easier) perfectly - all sound from every app then comes through the Audigy - but I'm sure there must be a better way.

Have you checked your bios to see if you can disable the unwanted sound chipset there? Unfortunately my bios doesn't provide that option, but if yours does then this may solve your problem.

By the way, the command I originally found was along the lines of "sudo mv /dev/dsp /home/backup/" but after this had worked a few times I adapted it to the version above.[/QUOTE]
 This method has also been suggested in the bug report that I posted before, but I think that changing a file is a cleaner solution.
As for disabling sound in my bios: this is just a TV Tuner PCI card, so I can't do that. But the onboard sound is already disabled. Otherwise I would have 3 sound cards :-P
Now everything works with alsa, except that gstreamer can't use directly alsa for it's output, but has to use esd.

---

### Post by accuser on 2005-03-21
[QUOTE=Marquis_de_Carabas]Have you checked your bios to see if you can disable the unwanted sound chipset there? Unfortunately my bios doesn't provide that option, but if yours does then this may solve your problem.[/QUOTE]

I have the same problem, and my onboard sound device *is* disabled in the BIOS, but Ubuntu still detects the device and installs it. What gives?

---

### Post by IdoMcFly on 2005-03-21
I had the same problem, solved by adding in /etc/modules the module to the sound card to it loads before the other one.

---

### Post by Marquis_de_Carabas on 2005-03-26
[QUOTE=IdoMcFly]I had the same problem, solved by adding in /etc/modules the module to the sound card to it loads before the other one.[/QUOTE]

Thank you. This is undoubtedly the simplest solution I have seen so far. aplay -l now lists the Audigy as card 0 and the onboard sound as card 1. Result!  :)

---

### Post by FloSynergy on 2006-03-23
huh?

sorry, but i don't get that?

"by adding in /etc/modules the module to the sound card to it loads before the other one."?

i've got the same issue and i'd really like to figure this out.

thanks,

flo

---

