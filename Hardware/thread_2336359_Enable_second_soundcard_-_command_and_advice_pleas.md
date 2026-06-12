---
title: "Enable second soundcard - command and advice please"
date: 2016-09-07
forum: Hardware
---

### Post by Andrew F in Australia on 2016-09-07
Hi All,

I had an ESI Juli@ soundcard working perfectly in 14.04, but it has broken in an upgrade to 16.04

Output from aplay -l shows that it recognises the onboard soundcard as well as the ESI Juli@ card

Given that this is a dual boot machine, the option of disabling in bios is not preferred.

I have looked at similar posts for an hour and it appears to be a configuration problem (see below) but don't understand the syntax of the alsa-conf file so was reluctant to change things that I didn't understand.

Could someone please advise how to disable the onboard card on bootup, or more importantly, enable the Juli@ card so that the computer can play audio again.  The posts below seemed to be the most helpful, but I've been up for 20 hours now, so couldn't get them to work

[https://ubuntuforums.org/showthread.php?t=2309283&highlight=disable+onboard+sound+card](https://ubuntuforums.org/showthread.php?t=2309283&highlight=disable+onboard+sound+card)
[https://ubuntuforums.org/showthread.php?t=2268010&highlight=disable+onboard+sound+card](https://ubuntuforums.org/showthread.php?t=2268010&highlight=disable+onboard+sound+card)

With thanks in advance.

A

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Juli [ESI Juli@], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Juli [ESI Juli@], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: VT2020 Digital [VT2020 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 2: VT2020 Alt Analog [VT2020 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

However, the external card is not recognised in the loaded modules.  [These are the only three that show up in the sound controller as well]

```
$ lspci | grep Audio
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
06:07.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)


```

lsmod shows that the modules are loaded for the Juli@ card but the card is not recognised, I believe:

```
 lsmod | grep snd
snd_hda_codec_hdmi     53248  1
snd_hda_codec_via      24576  1
snd_hda_codec_generic    77824  1 snd_hda_codec_via
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_codec_generic,snd_hda_intel
snd_ice1724           155648  3
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_ak4113             16384  1 snd_ice1724
snd_pt2258             16384  1 snd_ice1724
snd_ak4114             16384  1 snd_ice1724
snd_i2c                16384  2 snd_pt2258,snd_ice1724
snd_ice17xx_ak4xxx     16384  1 snd_ice1724
snd_ak4xxx_adda        20480  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_ac97_codec        131072  1 snd_ice1724
ac97_bus               16384  1 snd_ac97_codec
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  8 snd_ice1724,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_ak4113,snd_ak4114,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_ice1724,snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  34 snd_pt2258,snd_ice1724,snd_ac97_codec,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_i2c,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_ak4xxx_adda,snd_hda_intel,snd_seq_device,snd_ak4113,snd_ak4114
soundcore              16384  1 snd


```

---

### Post by Yellow Pasque on 2016-09-07
The easiest way is to blacklist the snd-hda-intel module entirely if you're not going to use the onboard or HDMI sound:
```
echo "blacklist snd-hda-intel" | sudo tee -a /etc/modprobe.d/blacklisthda.conf
```
Alternatively, if you can't prevent the module from loading, you should be able to disable like this:
```
echo "options snd-hda-intel enable=0,0" | sudo tee -a /etc/modprobe.d/blacklisthda.conf
```

If you want to revert the change(s), then you can just delete the file you created (and reboot):
```
sudo rm /etc/modprobe.d/blacklisthda.conf
```

> However, the external card is not recognised in the loaded modules
False. It's just a bit confusing because it lists it by chipset (VIA Envy24) rather than the name of the card.
```
06:07.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
```
Anyway, if a PCI sound card wasn't recognized by lspci, then it wouldn't show up in aplay.

---

### Post by Andrew F in Australia on 2016-09-07
THanks[SIZE=2] Temüjin,

The soundcard was originally detected but not playing music.

By blacklisting the module and also preventing the module from loading, it now works.

As always, the support on this forum is appreciated and your response in particular here.

With best regards,

A
[/SIZE]

---

