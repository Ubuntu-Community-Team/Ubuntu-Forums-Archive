---
title: "Onboard sound not working properly"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by mycroft on 2006-10-18
I have trouble configuring my nForce4 AC'97 based onboard sound card for Kubuntu running kernel 2.6.17.10. I can play music and the like, but the sound system (ALSA) only works every third reboot or so.

Output from cat/proc/asound/cards
```

 0 [CX8811         ]: CX88x - Conexant CX8811
                      Conexant CX8811 at 0xfa000000
 1 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at 0xfe02d000, irq 225
```

I should point out that no. 1 is not actually a sound card, but my TV tuner card - it does contain some limited audio functionality for transmitting audio to Line In.

Output from lsmod | grep snd:

```

snd_intel8x0           33436  1
snd_ac97_codec         96672  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm_oss            46080  0
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,cx88_alsa
snd_timer              23172  1 snd_pcm
snd                    55428  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,cx88_alsa,snd_pcm,snd_timer
soundcore               9952  1 snd
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm

```

I have tried playing around with /etc/modprobe.d/alsa-base - with mixed results.As you can see I have tried changing the index number for snd-intel8x0m to 0, but I haven't been able to determine if it has any effect.

```

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; :
 ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-
oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ;
/sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu
10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq
 ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ;
: ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=0
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

```

I also checked the /etc/modprobe.d/blacklist file, which actually mentions snd-intel8x0m - commenting it out doesn't seem to make much of a difference though.

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810) 
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

```

EDIT: It would seem that my problem primarily comes down to this: my TV tuner card is discovered before my onboard sound card, and consequently set as the default sound card - if the opposite were the case there would be no problems. So, is there any way I can change the order in which these two cards are discovered?

---

### Post by mycroft on 2006-10-26
Well - I haven't really had time to tinker with this lately, but I have noticed now that for the past eight(!) reboots, sound has been working correctly, even though I have taken no further steps to correct anything.
Maybe the issue - whether related to seeing the TV card as a sound card, or the .asoundrc being ignored - was simply due to the fact that Edgy Eft is still in development.

Either way, the problem has been solved... sort of anyway.

EDIT: Nope, it has just re-appeared. Guess I'm back at square one.

---

