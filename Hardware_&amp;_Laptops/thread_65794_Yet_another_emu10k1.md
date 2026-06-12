---
title: "Yet another emu10k1"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by seethru on 2005-09-15
Been reading all of them, but can't seem to find a solution for myself. I recently purchased a SBLive! from another member at these forums to replace my onboard sound, and give myself hardware mixing. I made a fresh asound.conf..

```
pcm.emu10k1 {
   type hw
   card 0
}

ctl.emu10k1 {
   type hw
   card 0
}
```

and created a new file in /etc/modutils named alsa and put the following inside it (as-per the alsa walkthrough)

```
# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-emu10k1
# module options should go here

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
	
# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
```

When I run an lsmod | grep snd I get this output

```
snd_mpu401              6408  0
snd_mpu401_uart         7360  1 snd_mpu401
snd_emu10k1_synth       7616  0
snd_emux_synth         36096  1 snd_emu10k1_synth
snd_seq_virmidi         7232  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_seq_dummy           3716  0
snd_seq_oss            33664  0
snd_seq_midi            9184  0
snd_seq_midi_event      7040  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51024  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul ,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           118404  2 snd_emu10k1_synth
snd_rawmidi            25056  4 snd_mpu401_uart,snd_seq_virmidi,snd_seq_midi,snd _emu10k1
snd_seq_device          8524  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,s nd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         83516  1 snd_emu10k1
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10696  2 snd_emu10k1,snd_pcm
snd_util_mem            4544  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8992  2 snd_emux_synth,snd_emu10k1
snd                    55172  17 snd_mpu401,snd_mpu401_uart,snd_emux_synth,snd_s eq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_c odec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9696  1 snd
```

No sound, and no errors when attempting to play sound. The analog/digital output is set to on in alsamixer, and I've stored those settings.

Also, there is a file in /etc/modutils named alsa-base which contains the following

```
# autoloader aliases
alias char-major-116 snd
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1
alias sound-slot-2 snd-card-2
alias sound-slot-3 snd-card-3
alias sound-slot-4 snd-card-4
alias sound-slot-5 snd-card-5
alias sound-slot-6 snd-card-6
alias sound-slot-7 snd-card-7
above sound-slot-0 snd-pcm-oss snd-mixer-oss snd-seq-oss
above sound-slot-1 snd-pcm-oss snd-mixer-oss snd-seq-oss
above sound-slot-2 snd-pcm-oss snd-mixer-oss snd-seq-oss
above sound-slot-3 snd-pcm-oss snd-mixer-oss snd-seq-oss
above sound-slot-4 snd-pcm-oss snd-mixer-oss snd-seq-oss
above sound-slot-5 snd-pcm-oss snd-mixer-oss snd-seq-oss
above sound-slot-6 snd-pcm-oss snd-mixer-oss snd-seq-oss
above sound-slot-7 snd-pcm-oss snd-mixer-oss snd-seq-oss
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
# Load optional modules above their base modules
above snd-pcm snd-pcm-oss
above snd-mixer snd-mixer-oss
above snd-seq snd-seq-oss snd-seq-midi
above snd-emu10k1 snd-emu10k1-synth
above snd-via82xx snd-seq
# Cause a script to be run after snd-*-synth module initialization
post-install snd-emu8000-synth /lib/alsa/modprobe-post-install snd-emu8000-synth
post-install snd-emu10k1-synth /lib/alsa/modprobe-post-install snd-emu10k1-synth
# Cause a script to be run after card driver module initialization
post-install snd-ad1816a /lib/alsa/modprobe-post-install snd-ad1816a
post-install snd-ad1848 /lib/alsa/modprobe-post-install snd-ad1848
post-install snd-ali5451 /lib/alsa/modprobe-post-install snd-ali5451
post-install snd-als100 /lib/alsa/modprobe-post-install snd-als100
post-install snd-als4000 /lib/alsa/modprobe-post-install snd-als4000
post-install snd-armaaci /lib/alsa/modprobe-post-install snd-armaaci
post-install snd-asihpi /lib/alsa/modprobe-post-install snd-asihpi
post-install snd-atiixp /lib/alsa/modprobe-post-install snd-atiixp
post-install snd-au1x00 /lib/alsa/modprobe-post-install snd-au1x00
post-install snd-au8810 /lib/alsa/modprobe-post-install snd-au8810
post-install snd-au8820 /lib/alsa/modprobe-post-install snd-au8820
post-install snd-au8830 /lib/alsa/modprobe-post-install snd-au8830
post-install snd-azt2320 /lib/alsa/modprobe-post-install snd-azt2320
post-install snd-azt3328 /lib/alsa/modprobe-post-install snd-azt3328
post-install snd-ca0106 /lib/alsa/modprobe-post-install snd-ca0106
post-install snd-cmi8330 /lib/alsa/modprobe-post-install snd-cmi8330
post-install snd-cmipci /lib/alsa/modprobe-post-install snd-cmipci
post-install snd-cs4231 /lib/alsa/modprobe-post-install snd-cs4231
post-install snd-cs4232 /lib/alsa/modprobe-post-install snd-cs4232
post-install snd-cs4236 /lib/alsa/modprobe-post-install snd-cs4236
post-install snd-cs4281 /lib/alsa/modprobe-post-install snd-cs4281
post-install snd-cs46xx /lib/alsa/modprobe-post-install snd-cs46xx
post-install snd-darla20 /lib/alsa/modprobe-post-install snd-darla20
post-install snd-darla24 /lib/alsa/modprobe-post-install snd-darla24
post-install snd-dt019x /lib/alsa/modprobe-post-install snd-dt019x
post-install snd-echo3g /lib/alsa/modprobe-post-install snd-echo3g
post-install snd-emu10k1x /lib/alsa/modprobe-post-install snd-emu10k1x
post-install snd-ens1370 /lib/alsa/modprobe-post-install snd-ens1370
post-install snd-ens1371 /lib/alsa/modprobe-post-install snd-ens1371
post-install snd-es1688 /lib/alsa/modprobe-post-install snd-es1688
post-install snd-es18xx /lib/alsa/modprobe-post-install snd-es18xx
post-install snd-es1938 /lib/alsa/modprobe-post-install snd-es1938
post-install snd-es1968 /lib/alsa/modprobe-post-install snd-es1968
post-install snd-es968 /lib/alsa/modprobe-post-install snd-es968
post-install snd-fm801 /lib/alsa/modprobe-post-install snd-fm801
post-install snd-fm801-tea575x /lib/alsa/modprobe-post-install snd-fm801-tea575x
post-install snd-gina20 /lib/alsa/modprobe-post-install snd-gina20
post-install snd-gina24 /lib/alsa/modprobe-post-install snd-gina24
post-install snd-gusclassic /lib/alsa/modprobe-post-install snd-gusclassic
post-install snd-gusextreme /lib/alsa/modprobe-post-install snd-gusextreme
post-install snd-gusmax /lib/alsa/modprobe-post-install snd-gusmax
post-install snd-harmony /lib/alsa/modprobe-post-install snd-harmony
post-install snd-hda-intel /lib/alsa/modprobe-post-install snd-hda-intel
post-install snd-hdsp /lib/alsa/modprobe-post-install snd-hdsp
post-install snd-hdspm /lib/alsa/modprobe-post-install snd-hdspm
post-install snd-ice1712 /lib/alsa/modprobe-post-install snd-ice1712
post-install snd-ice1724 /lib/alsa/modprobe-post-install snd-ice1724
post-install snd-indigo /lib/alsa/modprobe-post-install snd-indigo
post-install snd-indigodj /lib/alsa/modprobe-post-install snd-indigodj
post-install snd-indigoio /lib/alsa/modprobe-post-install snd-indigoio
post-install snd-intel8x0 /lib/alsa/modprobe-post-install snd-intel8x0
post-install snd-interwave /lib/alsa/modprobe-post-install snd-interwave
post-install snd-interwave-stb /lib/alsa/modprobe-post-install snd-interwave-stb
post-install snd-korg1212 /lib/alsa/modprobe-post-install snd-korg1212
post-install snd-layla20 /lib/alsa/modprobe-post-install snd-layla20
post-install snd-layla24 /lib/alsa/modprobe-post-install snd-layla24
post-install snd-maestro3 /lib/alsa/modprobe-post-install snd-maestro3
post-install snd-mia /lib/alsa/modprobe-post-install snd-mia
post-install snd-miro /lib/alsa/modprobe-post-install snd-miro
post-install snd-mixart /lib/alsa/modprobe-post-install snd-mixart
post-install snd-mona /lib/alsa/modprobe-post-install snd-mona
post-install snd-mpu401 /lib/alsa/modprobe-post-install snd-mpu401
post-install snd-msnd-pinnacle /lib/alsa/modprobe-post-install snd-msnd-pinnacle
post-install snd-mtpav /lib/alsa/modprobe-post-install snd-mtpav
post-install snd-nm256 /lib/alsa/modprobe-post-install snd-nm256
post-install snd-opl3sa2 /lib/alsa/modprobe-post-install snd-opl3sa2
post-install snd-opti92x-ad1848 /lib/alsa/modprobe-post-install snd-opti92x-ad1848
post-install snd-opti92x-cs4231 /lib/alsa/modprobe-post-install snd-opti92x-cs4231
post-install snd-opti93x /lib/alsa/modprobe-post-install snd-opti93x
post-install snd-pc98-cs4232 /lib/alsa/modprobe-post-install snd-pc98-cs4232
post-install snd-pcsp /lib/alsa/modprobe-post-install snd-pcsp
post-install snd-pcxhr /lib/alsa/modprobe-post-install snd-pcxhr
post-install snd-pdaudiocf /lib/alsa/modprobe-post-install snd-pdaudiocf
post-install snd-pdplus /lib/alsa/modprobe-post-install snd-pdplus
post-install snd-portman2x4 /lib/alsa/modprobe-post-install snd-portman2x4
post-install snd-powermac /lib/alsa/modprobe-post-install snd-powermac
post-install snd-pxa2xx-ac97 /lib/alsa/modprobe-post-install snd-pxa2xx-ac97
post-install snd-rme32 /lib/alsa/modprobe-post-install snd-rme32
post-install snd-rme96 /lib/alsa/modprobe-post-install snd-rme96
post-install snd-rme9652 /lib/alsa/modprobe-post-install snd-rme9652
post-install snd-s3c2410 /lib/alsa/modprobe-post-install snd-s3c2410
post-install snd-sa11xx-uda1341 /lib/alsa/modprobe-post-install snd-sa11xx-uda1341
post-install snd-sb16 /lib/alsa/modprobe-post-install snd-sb16
post-install snd-sb8 /lib/alsa/modprobe-post-install snd-sb8
post-install snd-sbawe /lib/alsa/modprobe-post-install snd-sbawe
post-install snd-serialmidi /lib/alsa/modprobe-post-install snd-serialmidi
post-install snd-serial-u16550 /lib/alsa/modprobe-post-install snd-serial-u16550
post-install snd-sgalaxy /lib/alsa/modprobe-post-install snd-sgalaxy
post-install snd-sonicvibes /lib/alsa/modprobe-post-install snd-sonicvibes
post-install snd-sscape /lib/alsa/modprobe-post-install snd-sscape
post-install snd-sun-amd7930 /lib/alsa/modprobe-post-install snd-sun-amd7930
post-install snd-sun-cs4231 /lib/alsa/modprobe-post-install snd-sun-cs4231
post-install snd-sun-dbri /lib/alsa/modprobe-post-install snd-sun-dbri
post-install snd-trident /lib/alsa/modprobe-post-install snd-trident
post-install snd-usb-audio /lib/alsa/modprobe-post-install snd-usb-audio
post-install snd-usb-usx2y /lib/alsa/modprobe-post-install snd-usb-usx2y
post-install snd-vx222 /lib/alsa/modprobe-post-install snd-vx222
post-install snd-vxp440 /lib/alsa/modprobe-post-install snd-vxp440
post-install snd-vxpocket /lib/alsa/modprobe-post-install snd-vxpocket
post-install snd-wavefront /lib/alsa/modprobe-post-install snd-wavefront
post-install snd-ymfpci /lib/alsa/modprobe-post-install snd-ymfpci
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
```

is there any chance any of that has anything to do with it? Please keep in mind I've come from a working sound system using an onboard, nforce2 chipset, to no sound using hardware mixing. If anyone has the same card, please paste any relevant configs/settings you can think of as I went through a lot of trouble to get my nforce2 to work, and I didn't expect to have to go through all this again.

edit: I know I've posted this in the Hoary section, however I am using Breezy.

---

### Post by seethru on 2005-09-15
anyone? this is driving me nuts :/

---

### Post by skoal on 2005-09-15
seethru, what "alsa walkthrough" are you talking about?

I have an SBLive! myself.  The alsa driver for it uses hardware mixing already.  I don't know why you would need the dmixer for this card (asound.conf).  If you have the same card I do, no need for software mixing and the associated latencies.  SBLive! is da king on linux.  You basically don't need any of that stuff you got there, unless I've completely misunderstood what you want.  I'm listening to amarok mp3's with realplayer internet streams playing at the same time.  Setup/works straight out of the box.

* Your issues more than likely stem from your old sound card (as you cited), and (possibly) improper mixer settings.

1. Backup both of those files you made, "asound.conf" and "/etc/modutils/alsa" (?).  You don't need either of them.  *Hotplug and /etc/modprobe.d/??? should take care of it all for you*.

2. Remove those 2 files you made or (better yet) just "mv asound.conf asound.conf~" (or the like).

Reboot and hopefully everything gets setup correctly.  You may have to play with your mixer settings.  If for some reason the mixer settings are using hardware settings from your old nForce board, you might have to 'alsactl -f ~/emu10k1.state store' && 'alsactl -f ~/emu10k1.state restore'.  That should give you a fresh hardware mixer state.  I dunno.  I miss the good 'ole days of 'alsaconf'.  /etc/init.d/alsa uses (by default) /var/lib/alsa/asound.state for mixer settings.  If the new mixer settings work, then just 'sudo alsactl store' and it should take care of that file for you.  I dunno if alsa script on shutdown does or not (without further digging)...

I've attached some relevant files.  By the way, I'm on hoary so I have no idea what (if any) changes have been made to hotplug/alsa, et al...

\\//_

```
skoal@morpheus://~ $ lsmod |grep 'snd\|emu'
emu10k1_gp              3840  0 
gameport               16520  2 emu10k1_gp
snd_emu10k1           118916  2 
snd_rawmidi            26016  1 snd_emu10k1
snd_seq_device          8972  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         83320  1 snd_emu10k1
snd_pcm_oss            53536  0 
snd_mixer_oss          19968  1 snd_pcm_oss
snd_pcm                95240  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              25860  2 snd_emu10k1,snd_pcm
snd_page_alloc         10244  2 snd_emu10k1,snd_pcm
snd_util_mem            4736  1 snd_emu10k1
snd_hwdep               9632  1 snd_emu10k1
snd                    56292  12 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore              10464  1 snd
```
```
skoal@morpheus://~ $ lspci -vv |grep -i 'audio\|creative'
0000:02:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
        Subsystem: Creative Labs CT4620 SBLive!
0000:02:0c.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 05)
        Subsystem: Creative Labs Gameport Joystick
```

---

