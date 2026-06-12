---
title: "Max Volume or Mute"
date: 2008-07-28
forum: General Help
---

### Post by Tsarj on 2008-07-28
[IMG]http://img507.imageshack.us/img507/4676/soundissueimagerz5.png[/IMG]
Ok. So that's the link to my issue. Only one device is selectable. How do I change it? I need to. It's max volume or mute... Please help.

---

### Post by eric3_14159 on 2008-07-29
Are you using OSS on purpose? If not, it may be possible to switch to ALSA. Go to System->Preferences->Sound, and try changing "Default Mixer Tracks" to any other options it has. I've never been able to predict which ones will be successful, but trying a few usually works out.

---

### Post by VictorR on 2008-07-29
I have something looking like this with USB 3D Sound dongle. It is a small device, looking like a pen-drive, which pretends to be a 5.1 surround USB sound card. I solved the problem using "softvol" ALSA plig-in. Below is my .asoundrc file:
```

pcm.USBsound {
    type hw
    card 1
    device 0
}

pcm.softvol {
    type            softvol
    slave {
        pcm         "USBsound"
    }
    control {
        name        "USB Master"
        card        0
    }
}


```
This file is located in your home directory (or you may have to create it) and it adds a new slider, called "USB Master" to Gnome ALSA Mixer, which works pretty fine. I think you can make something similar for your device.
I am afraid OSS is too old to play with it, ALSA is the default Ubuntu sound system.

---

### Post by Tsarj on 2008-07-29
No... It automatically chose OSS for me... But I have put the Live CD in and it automatically uses ALSA as my Default Mixer Track. Is there a file that tells the system which device to use for possible Default Mixer Tracks? If so, how do I edit it and point to the right device? 
Devices: ```
cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 6]: digital audio playback
  5: [ 0- 6]: digital audio capture
  6: [ 0- 1]: digital audio playback
  7: [ 0- 0]: digital audio playback
  8: [ 0- 0]: digital audio capture
  9: [ 0]   : control
```

Cards:```
cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 20
```
Pcm: ```
cat /proc/asound/pcm
00-06: Conexant HSF Modem : Conexant HSF Modem : playback 1 : capture 1
00-01: STAC92xx Digital : STAC92xx Digital : playback 1
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 3
```

How do I edit these files? How do make it possible to change my Default Mixer Track? In my previous post, I posted a link to a screenshot... In that, it demonstrates that OSS is the ONLY possible Device...

---

### Post by CatKiller on 2008-07-29
> **Tsarj said:**
> In my previous post, I posted a link to a screenshot... In that, it demonstrates that OSS is the ONLY possible Device...

You've not uninstalled ALSA, or anything similar have you? Conexant HSF is a modem device - that's not your sound card. I'd imagine that's why it doesn't have a proper volume control.

---

### Post by dexter.deepak on 2008-07-29
if you miss alsa, you can install it here...i am attaching the drivers.
give them executable permissions:
```
sudo chmod a+x alsa_?.sh
```
then execute the first one:
```
./alsa_1.sh
```
reboot and then try:
```
./alsa_2.sh
```
reboot.

---

### Post by Tsarj on 2008-07-29
Oh yeah, I'm at work and didn't bring my laptop today, but I just remembered that it says that alsamixer has Master Volume twice or something like that. I believe I still have ALSA installed... How do I check before I try to install?

***EDIT***Alsamixer:```
alsamixer
ALSA lib simple_none.c:1710:(simple_add1) helem (MIXER,'Master Playback Volume',0,2,0) appears twice or more

alsamixer: function snd_mixer_load failed: Invalid argument
```

---

### Post by VictorR on 2008-07-29
System -> Preferences -> Multimedia Systems Selector. Check all comboboxes to see what was installed in your system and what devices are presumable audio ones.

---

### Post by Tsarj on 2008-07-30
That didn't help cause I still cannot change my Default Mixer Track to ALSA. The only available device is OSS through my Fax Modem?! What?! haha

---

### Post by Tsarj on 2008-07-30
Bump

---

### Post by VictorR on 2008-08-01
It looks like you have SigmaTel sound card with Intel High Definition Audio chip, and somehow your Alsa driver is either broken or un-installed. (When you boot from Live-CD it works as it is supposed to be).
Conexant modem is another hardware with some audio capabilities, but it is not what you actually need.

You may try to re-install ALSA again, as dexter.deepak suggested or just using Synaptic, and then see, if it recovers your audio stuff.

Have a look at this How-to, it should be related to your problem [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

