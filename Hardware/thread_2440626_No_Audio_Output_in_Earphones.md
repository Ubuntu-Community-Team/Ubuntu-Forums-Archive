---
title: "No Audio Output in Earphones"
date: 2020-04-13
forum: Hardware
---

### Post by aryannc on 2020-04-13
Hi, 
I am encountering a no audio-output issue in headphones on an Alienware 15 R2 with Ubuntu 18.04.4 LTS.

I followed the steps suggested in this [thread]("https://ubuntuforums.org/showthread.php?t=1638201&highlight=Sound+Output+Earphones"), but the issue hasn't resolved.

**alsa-info-script** results: [URL="https://alsa-project.org/db/?f=2e17eb6710d699b03537f687e3209f12137fde0e"]https://alsa-project.org/db/?f=2e17eb6710d699b03537f687e3209f12137fde0e
[/URL]
**alsa-base.conf:** ```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=auto
```

**alsamixer:**

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.1.3 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel PCH                                  F1:  Help               &#9474;
&#9474; Chip: Creative CA0132                                F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -11.00, -11.00]               Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                                                            &#9474;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#9474;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#9474;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#8594;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#8594;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#8594;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#8594;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#8594;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#8594;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#8594;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                                            &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;     &#9474;OO&#9474;              &#9474;OO&#9474;     &#9474;MM&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;    45<>45   98<>98                                                           &#9474;
&#9474;  < Master >  PCM    Surround  S/PDIF  S/PDIF 1 S/PDIF 2 S/PDIF 3 S/PDIF 4    &#9474;
```

**Sound Menu:**
[ATTACH=CONFIG]285503[/ATTACH]

Thank you for your help in advance.

---

### Post by Yellow Pasque on 2020-04-13
Hmm. This was supposed to have been fixed a long time ago: [https://github.com/torvalds/linux/commit/b5337cfe067e96b8a98699da90c7dcd2bec21133](https://github.com/torvalds/linux/commit/b5337cfe067e96b8a98699da90c7dcd2bec21133)

The first thing you should do is get rid of this line (and reboot). It is for a completely different codec, IDT/Sigmatel STAC92HD71B, and you have a Creative CA0132:
```
snd_hda_intel model=dell-m6-amic
```


The other suggestion I have is toggling these controls in alsamixer:
```
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
```

You can see some other Alienware owners have had success with that: [https://askubuntu.com/questions/725265/sound-only-out-of-internal-speakers-never-headphones-alienware-laptop-ubuntu](https://askubuntu.com/questions/725265/sound-only-out-of-internal-speakers-never-headphones-alienware-laptop-ubuntu)

---

### Post by aryannc on 2020-04-14
Thank you for your help.
As you and this [thread]("https://askubuntu.com/questions/725265/sound-only-out-of-internal-speakers-never-headphones-alienware-laptop-ubuntu") had suggested, I toggled **ON** the following controls in **alsamixer**, which solved the issue:```
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
```

---

