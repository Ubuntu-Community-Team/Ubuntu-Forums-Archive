---
title: "Can't get soundcard detected"
date: 2005-12-01
forum: General Help
---

### Post by philstr on 2005-12-01
Please bear with me as this is the first time I've really tried Linux. Everything has been so impressive so far but now I can't get Breezy to get any sound out of my soundcard. :confused: 

If I type lspci I get this:

0000:00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
0000:00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
0000:00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
0000:00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
0000:00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
0000:00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
0000:00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[COLOR="Red"]0000:00:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)[/COLOR]
0000:00:0c.0 USB Controller: NEC Corporation USB (rev 41)
0000:00:0c.1 USB Controller: NEC Corporation USB (rev 41)
0000:00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
0000:01:05.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2 Ultra] (rev 15)

So that seems to mean I have an Ensoniq 5880 device in my computer. My understanding is this needs the snd_ens1371 module to work. So I added this to the etc/modules file and when I do lsmod | grep 1371 I get the following:

snd_ens1371            22240  0
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd                    48644  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

So it appears the module is loaded. So that makes it all the more confusing when I go to open the volume ontrol and it says:

No Volume Control Elements and/or devices found 

And when I go to System/Preferences/Sound there is no sound card to pick as the default in the drop own box.

Anyone have any clue as to what is wrong or what I should try next?

Oh and it's not the card itself as that works fine under XP.

---

### Post by philstr on 2005-12-02
Can anyone help at all? Would really like to get the sound working and I've searched the forums but all the problems described seem to be after at least the soundcard shows up in System/Preferences/Sound.

---

### Post by az on 2005-12-02
P

---

