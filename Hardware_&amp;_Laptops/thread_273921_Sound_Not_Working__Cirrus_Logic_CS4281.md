---
title: "Sound Not Working :: Cirrus Logic CS4281"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by moufranica on 2006-10-09
I have problems with a Fujitsu machine. I have no sound. I am attaching some relevant informations:

Output of 'cat /proc/asound/cards
```

0 [CS4281         ]: CS4281 - Cirrus Logic CS4281
                     Cirrus Logic CS4281 at 0x11001000, irq 5


```

Output of 'sudo vi /etc/modprobe.d/alsa-base'
```

# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2


```

Output of 'lsmod | grep snd'
```

snd_cs4281             21856  3
gameport               15496  2 snd_cs4281
snd_rawmidi            25504  1 snd_cs4281
snd_ac97_codec         92704  1 snd_cs4281
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
snd_pcm                89864  3 snd_cs4281,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10632  1 snd_pcm
snd_opl3_lib           10624  1 snd_cs4281
snd_seq_device          8716  2 snd_rawmidi,snd_opl3_lib
snd_timer              25220  2 snd_pcm,snd_opl3_lib
snd_hwdep               9376  1 snd_opl3_lib
snd                    55268  14 snd_cs4281,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_seq_device,snd_timer,snd_hwdep
soundcore              10208  2 snd


```

Please let me know what steps should I follow?

---

