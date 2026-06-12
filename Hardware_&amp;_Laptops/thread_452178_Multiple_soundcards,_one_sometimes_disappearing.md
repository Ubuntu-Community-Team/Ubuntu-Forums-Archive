---
title: "Multiple soundcards, one sometimes disappearing"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by mthmulders on 2007-05-23
Hello all,

Let me first describe my situation: I am having a computer with a sound-chip on the motherboard; there is a sound card on the PCI-bus; and finally, there's a TV-tuner. I prefer to connect my headset to the on-board chip while connecting my 5.1 speaker system to the PCI-sound card. Skype can be configured to use a specific sound card, so that works fine.

Now, when I boot my Kubuntu system, my sound cards appear in random order. That is, sometimes the PCI-card is listed first (in /proc/asound/cards), sometimes it is the motherboard-chip. Because I don't like to reconfigure both Skype and KDE every time, I figured out that it is possible to specify a fixed index in /etc/modprobe.d/alsa-base. I did it like this:
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
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
# My own options, combined with the solution for Ubuntu bug #62691
options snd-cmipci mpu_port=0x330 fm_port=0x388 index=0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
# options snd-cmipci mpu_port=0x330 fm_port=0x388

```

This does partially solve my problem. My PCI-sound card (that's the cmipci) is listed first... if listed at all. Many times, after booting, I find myself with one sound card less. All cards are listed, except for the cmipci card. The strange thing is that lspci does list the card.

Can anybody shed light on this?

---

### Post by Rmantingh on 2007-06-19
Have you tried setting your default card with:
$ asoundconf list
$ asoundconf set-default-card <name-from-list>

I have a different problem though....
I also have two soundcards in my system (onboard Intel and PCI Audigy).
I would like to use the onboard one for my headset (to be used with Skype)
and the other for playing music through my normal speakers.
I can set the default soundcard OK (see above) but if I specify in Skype
that I want to use my onboard soundcard for my headset this doesn't
work. Whatever the default soundcard is according to Ubuntu (set with
asoundconf) this is what Skype uses as well. Whatever I select in
the Sound Devices menu is ignored.
Have you experienced any similar problem or is Skype always
selecting the right card for you?

---

### Post by mthmulders on 2007-06-19
No, Skype often picks my TV-card. It can be changed, of course, but that's not too annoying. The annoying thing from the problem as I described it above is that every time my soundcard isn't listed I need to reboot.
For the last weeks, it's always there on the first boot, and it's the default one. Maybe there's been a patch in the kernel or something...

---

### Post by mr.thraz on 2007-10-19
> **Rmantingh said:**
> Have you tried setting your default card with:
$ asoundconf list
$ asoundconf set-default-card <name-from-list>

I have a different problem though....
I also have two soundcards in my system (onboard Intel and PCI Audigy).
I would like to use the onboard one for my headset (to be used with Skype)
and the other for playing music through my normal speakers.
I can set the default soundcard OK (see above) but if I specify in Skype
that I want to use my onboard soundcard for my headset this doesn't
work. Whatever the default soundcard is according to Ubuntu (set with
asoundconf) this is what Skype uses as well. Whatever I select in
the Sound Devices menu is ignored.
Have you experienced any similar problem or is Skype always
selecting the right card for you?


thanks, i needed that.

---

### Post by mthmulders on 2007-10-22
> **Rmantingh said:**
> Have you tried setting your default card with:
$ asoundconf list
$ asoundconf set-default-card <name-from-list>

Should that be executed as normal user or as root?

---

### Post by SyncMaster on 2007-11-18
I ran asoundconf once as normal user, once as root. But it warns you if you are running it as root, so I don't know what is correct.
At least it helped to solve one part of my problem.

I still could only play back and not record. But this I solved by enabling Microphone Capture (and Mic Boost) in the Volume Control (Edit > Preferences, Microhphone,)
Close this and go to Switch and enable the two new options...

Just if someone else can not record. In fact I still have no clue which device is meant by "capture" in the "Sound Recorder". Skype and Audacity use different names, which made more sense.

Rainer

---

