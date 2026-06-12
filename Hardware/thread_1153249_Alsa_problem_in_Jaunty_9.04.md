---
title: "Alsa problem in Jaunty 9.04"
date: 2009-05-08
forum: Hardware
---

### Post by Shnureaga on 2009-05-08
I use Ubuntu 9.04, a laptop Packard-Bell Easynote MZ35 and Wubi. After fresh install the alsa drivers are 1.0.19 i think. After that i downloaded and installed 1.0.20 from the official site. Even than in console when i start alsamixer i get the info that my version is 1.0.18 :( The purpose of my thread is that i can't get sound in my headphones. The laptop is playing music from the integrated speakers very well. 
I will appreciate any help.

---

### Post by Shnureaga on 2009-05-08
This will be helpful: 

lukavia@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lukavia@ubuntu:~$ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.20 emulation code)
Kernel: Linux ubuntu 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:27:06 UTC 2009 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA ATI SB at 0xc0400000 irq 16

Audio devices:
0: ALC861VD Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC861-VD


lukavia@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc Device [1002:5a31] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 82)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62]
09:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
09:04.0 Network controller [0280]: RaLink RT2561/RT61 rev B 802.11g [1814:0302]


lukavia@ubuntu:~$ lsmod | grep snd
snd_hda_codec_realtek   205060  1 
snd_hda_intel          34120  1 
snd_hda_codec          83584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              15364  1 snd_hda_codec
snd_pcm_oss            45984  0 
snd_mixer_oss          22912  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy          10884  2 
snd_seq_oss            36224  0 
snd_seq_midi           14240  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57584  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29192  2 snd_pcm,snd_seq
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    66852  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm


lukavia@ubuntu:~$ cat /proc/asound/card*/codec* | grep Codec
Codec: Realtek ALC861-VD
lukavia@ubuntu:~$

---

### Post by DJYoshaBYD on 2009-05-08
wow.. every person on here that has a problem, is having it with 9.04... downgrade to 8.10 or 8.04 and see if the issues is still there.. it will probably go away..

---

### Post by Shnureaga on 2009-05-08
wow, downgrade is not the solutoin :) in 8.10 i did not have the problem though...

---

### Post by Shnureaga on 2009-05-10
anybody?:(

---

### Post by Shnureaga on 2009-05-12
OK, i found the solution. After installation of alsa 1.0.20 i did these things

```
sudo gedit /etc/modprobe.d/alsa-base
```

we get window, which in my case was empty and i added

```
options snd-hda-intel position_fix=1 model=dallas
```

close and save the file, reboot

that's F_ing all :)

At first place i used these two lines in the **/etc/modprobe.d/alsa-base** file

```
options snd-hda-intel model=hp
options snd-hda-intel model=3stack
```

And it worked, **but** there was a strange thing - that both headphones and speakers worked perfectly, **but only for 3 minutes**, after that if i unplugged headphones there was no sound from speakers......

Hope to be helpfull:guitar:

---

