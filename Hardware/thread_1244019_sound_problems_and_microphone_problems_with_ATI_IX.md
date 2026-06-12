---
title: "sound problems and microphone problems with ATI IXP SB400"
date: 2009-08-19
forum: Hardware
---

### Post by kiserp on 2009-08-19
Hello! I have problems with playing and capture sound on my laptop Asus A6R (chipset ATI IXP SB400).


I noticed two only at this moment:
1. Sound pass to cycle  when I start my music player or on system start beep. it repeats. Same problem on [thread] [http://ubuntuforums.org/showthread.php?p=7810074#post7810074](http://ubuntuforums.org/showthread.php?p=7810074#post7810074) [/thread] 

2. Sound capture not work's.
Standart gnome sound recorder don't find any sound device.



lspci
```
 00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)

```lsmod | grep snd

```

snd_atiixp             24204  4 
snd_ac97_codec        112292  1 snd_atiixp
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  4 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  3 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  16 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_atiixp,snd_pcm

```aplay -l 

```
**** list PLAYBACK devises ****
card 0: IXP [ATI IXP], devise 0: ATI IXP AC97 [ATI IXP AC97]
  subdevice: 0/1
  subdevice &#8470;0: subdevice #0

```cat /proc/asound/cards

```
 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with AD1986 at 0xfebfcc00, irq 17
 
```please, help me...i don't know what to do T_T
PS
My distro is LinuxMint 7 (based on jaunty)

---

### Post by kiserp on 2009-08-20
there is no any idea?

---

