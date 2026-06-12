---
title: "lubuntu alsa sound, repeating first syllable"
date: 2016-08-09
forum: Hardware
---

### Post by nathlx on 2016-08-09
Hi,

I install the latest lubuntu (xenial) on my sony vaio P. 
Most things work great, but sound doesnt work at all, opening in any desktop player just stays at playing 0:00 with no sound, (VLC, mplayer,audacious).

If I try running   nath@nathVP:~$ aplay /usr/share/sounds/alsa/Front_Center.wavI get the first syllable of "front", "Fron" played over and over (fron,fron,fron,fron,fron) until i cancel it. This shows that at least the sound isnt muted.

If i plugin a usb soundcard it works perfectly, howeverI would like to get internal sound working. 

```

lspci gives
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 06)

nath@nathVP:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=MID
    HDA Intel MID, ALC262 Analog
    Default Audio Device
sysdefault:CARD=MID
    HDA Intel MID, ALC262 Analog
    Default Audio Device
front:CARD=MID,DEV=0
    HDA Intel MID, ALC262 Analog
    Front speakers
surround21:CARD=MID,DEV=0
    HDA Intel MID, ALC262 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=MID,DEV=0
    HDA Intel MID, ALC262 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=MID,DEV=0
    HDA Intel MID, ALC262 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=MID,DEV=0
    HDA Intel MID, ALC262 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=MID,DEV=0
    HDA Intel MID, ALC262 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=MID,DEV=0
    HDA Intel MID, ALC262 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=MID,DEV=0
    HDA Intel MID, ALC262 Analog
    Direct sample mixing device
dsnoop:CARD=MID,DEV=0
    HDA Intel MID, ALC262 Analog
    Direct sample snooping device
hw:CARD=MID,DEV=0
    HDA Intel MID, ALC262 Analog
    Direct hardware device without any conversions
plughw:CARD=MID,DEV=0
    HDA Intel MID, ALC262 Analog
    Hardware device with all software conversions





```

I tried this guide for DKMS and the latest alsa build but with no luck, 
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

pulse audio is not installed i beleive and on this old laptop may be too heavy? The wiki for sound fixes all seem to use pulse audio.

---

### Post by Yellow Pasque on 2016-08-10
The first thing I would do is run the alsa info script to have a reference point: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Next, I would try this:
```
echo "options snd-hda-intel position_fix=1" | sudo tee -a /etc/modprobe.d/posfix.conf
```
Reboot and see if it helps. If it does not, then undo it:
```
sudo rm /etc/modprobe.d/posfix.conf
```

EDIT: Technical reference link: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by Yellow Pasque on 2016-08-10
On second glance, position_fix=1 should be the default for your sound chip, so I don't know if the previous post will help (but I would still try it).
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825709](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825709)
[http://git.kernel.org/cgit/linux/kernel/git/tiwai/sound.git/commit/?id=645e903528ca6cd510f9ac71a6a23de1a4d931e3](http://git.kernel.org/cgit/linux/kernel/git/tiwai/sound.git/commit/?id=645e903528ca6cd510f9ac71a6a23de1a4d931e3)

If it doesn't help, trying the same thing with position_fix=4 may be worth a shot:
```
sudo rm /etc/modprobe.d/posfix.conf
echo "options snd-hda-intel position_fix=4" | sudo tee -a /etc/modprobe.d/posfix.conf
```
..and reboot.

---

### Post by nathlx on 2016-08-15
Thanks for those, I tried both of your suggestions but no change, aplay /usr/share/sounds/alsa/Front_Center.wav still just plays fro-fro-fro until i kill it. 

just after i installed the sound worked, and i took a alsa report, then after a reboot the sound stopped, and after a day of trying i made a second report.
[http://www.alsa-project.org/db/?f=26fa6c2e924affbd71a3453a7b80fc1e895693de](http://www.alsa-project.org/db/?f=26fa6c2e924affbd71a3453a7b80fc1e895693de)
this one is after it stopped working:
[http://www.alsa-project.org/db/?f=a914bc51e99bff23a901a57dabd2ff804e00d2a3](http://www.alsa-project.org/db/?f=a914bc51e99bff23a901a57dabd2ff804e00d2a3)

I tried dist-upgrade which updated a few packages but still no change.

Thanks,

---

### Post by Yellow Pasque on 2016-08-15
So this is working:
```
[   15.232105] snd_hda_intel 0000:00:1b.0: azx_get_response timeout, switching to polling mode: last cmd=0x000f0001
[   15.350086] snd_hda_codec_realtek hdaudioC0D0: ALC262: SKU not ready 0x411111f0
[   15.350238] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC262: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   15.350249] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   15.350258] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   15.350264] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   15.350270] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   15.350279] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x12
[   15.361362] input: HDA Intel MID Headphone Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.836418] snd_hda_intel 0000:00:1b.0: No response from codec, disabling MSI: last cmd=0x020c0000
[   17.840099] snd_hda_intel 0000:00:1b.0: azx_get_response timeout, switching to single_cmd mode: last cmd=0x020c0000
```

And this is not:
```
[   17.104100] snd_hda_intel 0000:00:1b.0: azx_get_response timeout, switching to polling mode: last cmd=0x000f0001
[   17.182010] snd_hda_codec_realtek hdaudioC0D0: ALC262: SKU not ready 0x411111f0
[   17.182161] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC262: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   17.182171] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.182180] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   17.182186] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   17.182192] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   17.182201] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x12
[   17.196531] input: HDA Intel MID Headphone Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8

```

Hmmm. Let we try and wrap my head around that.

---

### Post by Yellow Pasque on 2016-08-15
Based on:
[https://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio.txt](https://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio.txt)

I think the next thing I would try is this:
```
sudo echo "enable_msi=0" | sudo tee -a /etc/modprobe.d/msifix.conf
```

---

### Post by nathlx on 2016-08-15
Ok, that last one worked, back to how it was working after a fresh install. Basically now sound just comes from everywhere all the time, and i run alsamixer to turn up the volume wherever I want it to come out, I can live with that, thanks!

---

### Post by nathlx on 2016-08-15
Ok, I did the change, rebooted, and it worked. I rebooted again, it worked. I shutdown, booted without headphones plugged in then plugged them in. no back to fro-fo-fro-fro again. Strange!

Not sure why but it worked for a while, and is now broken as before. very strange.. 
new alsa report;
[http://www.alsa-project.org/db/?f=72da2ab829886d0193c1d5146cc1bf5f9e258095](http://www.alsa-project.org/db/?f=72da2ab829886d0193c1d5146cc1bf5f9e258095)

also get this in alsa report:
libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/msifix.conf line 1: ignoring bad line starting with 'enable_msi=0'

So i guess that second fix isn:t the reason it started working? 

such a strange problem!

---

### Post by Yellow Pasque on 2016-08-15
Oh, it was a copy/paste failure on my part (sorry) :
Should have been:
```
echo "options snd-hda-intel enable_msi=0" | sudo tee -a /etc/modprobe.d/msifix.conf
```

---

