---
title: "On-Board Soundchip prevents Soundblaster Audigy USB 2 NX from working"
date: 2006-03-17
forum: Hardware &amp; Laptops
---

### Post by stokedfish on 2006-03-17
Sorry for my bad English, but I asked this question in 5 other linux boards already and nobody can help...

OS: Kubuntu Dapper Flight 5
Problem: USB Soundcard gets detected, but on-board chip prevents its use
Possible Solution: Completely disable my on-board soundchip (I never use it, it's broke anyway)

- I can't disable it in my bios
- this soundcard works well on Suse 10.0 (with the help of Yast)

```
lsufish@fish:~$ lsusb
Bus 001 Device 003: ID 041e:3020 Creative Technology, Ltd SoundBlaster Audigy 2 NX
Bus 001 Device 001: ID 0000:0000

```
```
fish@fish:~$ cat /proc/asound/cards
0 [rev40          ]: VIA686A - VIA 82C686A/B rev40
                     VIA 82C686A/B rev40 with Cx20468 at 0x1400, irq 10
1 [modem          ]: VIA82XX-MODEM - VIA 82XX modem
                     VIA 82XX modem at 0x1800, irq 10
2 [NX             ]: USB-Audio - SB Audigy 2 NX
                     Creative Technology Ltd SB Audigy 2 NX at usb-0000:00:11.2-2, full speed
```
```
fish@fish:~$ lsmod | grep snd
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_usb_audio          76864  1
snd_usb_lib            16640  1 snd_usb_audio
snd_hwdep               9376  1 snd_usb_audio
snd_via82xx_modem      15368  1
snd_via82xx            28696  4
gameport               15496  1 snd_via82xx
snd_ac97_codec         92448  2 snd_via82xx_modem,snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89736  6 snd_usb_audio,snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  3 snd_seq,snd_pcm
snd_page_alloc         10632  3 snd_via82xx_modem,snd_via82xx,snd_pcm
snd_mpu401_uart         7680  1 snd_via82xx
snd_rawmidi            25504  3 snd_seq_midi,snd_usb_lib,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    55268  24 snd_seq_oss,snd_seq,snd_usb_audio,snd_hwdep,snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd
usbcore               129668  4 snd_usb_audio,snd_usb_lib,uhci_hcd
```
/home/fish/.asoundrc:

```
pcm.dmixer {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:1,0"
   period_time 0
   period_size 1024
   buffer_size 8192
    rate 48000
     }

     bindings {
         0 0
    1 1
     }
}

pcm.dmixer {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"
   period_time 0
   period_size 1024
   buffer_size 8192
    rate 48000
     }

     bindings {
         0 0
    1 1
     }
}

pcm.dsp0 {
    type plug
    slave.pcm "dmixer"
}

pcm.dsp1 {
    type plug
    slave.pcm "dmixer"
}

pcm.!default {
        type plug
   slave.pcm "dmixer"
}

pcm.default {
   type plug
   slave.pcm "dmixer"
}

ctl.mixer1 {
    type hw
    card 1
}

ctl.mixer0 {
    type hw
    card 0
}
```
/etc/modprobe.d/alsa-base:

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

# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
```
/etc/modules:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
```
Any help is muuuch appreciated! This makes me go nuts...grrrrrrrrrrrr!!!!

Btw, this is NOT a dapper problem, it doesn't work on breezy either...  

So how the hell do I prevent the kernel from loading the module for my on-board soundchip?

KMix is a joke, I can set it in any way I want, it will always use my on-board sound... :(

---

### Post by mandible on 2006-03-17
a

---

### Post by stokedfish on 2006-03-17
mandible, I can't...

[QUOTE=stokedfish]
- I can't disable it in my bios[/QUOTE]

---

### Post by stokedfish on 2006-03-17
OMG I just got it! woooooooohooooooooooooo!!!

I had to add an option to /etc/modprobe.d/alsa-base, it looks like this now:

```
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-via82xx index=-2
```
The last line is the key to [amaroK heaven](http://www.last.fm/user/stokedfish/journal/2006/02/16/77997/) - thx!!! (found it in the search) ;-)

---

