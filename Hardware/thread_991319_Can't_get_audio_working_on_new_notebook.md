---
title: "Can't get audio working on new notebook"
date: 2008-11-23
forum: Hardware
---

### Post by pssturges on 2008-11-23
Hi,

Just brought home my shiny new Medion Akoya notebook PC. I just can't seem to get any audio working. Ubuntu is showing the sound card as follows:
```
 
lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

```

Initially alsa wasn't even finding any audio device, so I downloaded the latest alsa (1.0.18rc3), complied & installed it. Now the card is detected by alsa but I can't get any sound.

```

phil@phil-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 5: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

In the mixer I only get one slider for ALSA, Master.
On Realtek ALC268 (OSS Mixer ) I get 5. Volume, Microphone, PCM-2, In-gain & Digital-1. Seems, no mater how I adjust the sliders, I can't get any sound.

Any Ideas? Is the sound card just too new to have decent drivers, perhaps?

Cheers,
Phil

---

### Post by pssturges on 2008-11-25
Anyone?

---

### Post by Stephen_at on 2008-11-26
Its working on my akoya S5610 which is also dual booting

[http://ubuntuforums.org/showthread.php?t=993804](http://ubuntuforums.org/showthread.php?t=993804)

---

### Post by pssturges on 2008-11-26
Thanks for the reply. Glad to hear you got yours working well. Mine, however is a completely different story. I read your other post and thought I'd try a few things. Now, I'm back to square 1! Alsa can't find any audio devices. During my previous research on this, I found some sources that suggested editing /etc/modprobe/alsa-base and inserting lines such as

```
options snd-hda-intel model=mitac
```
and
```
options snd-hda-intel enable_msi=1
```.

At some point these combined with the latest asla drivers I allowed alsa to detect my card. But still no sound. I was never really quite sure whether or not these lines applied to my particular card so when I read your post I tried removing them. Now I get no alsa devices whether or not the lines are in.

```
phil@phil-laptop:~$ aplay -l
aplay: device_list:215: no soundcards found...
phil@phil-laptop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

```

I'd be interested to compare our /etc/modprobe/alsa-base & our /usr/share/alsa-base/alsa-default. Here are mine:

```
/etc/modprobe/alsa-base
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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=mitac
options snd-hda-intel enable_msi=1
```

```
/usr/share/alsa-base/alsa-default
# Configuration file for alsa-base

# List, separated by spaces, the names of modules that should be
# unloaded, if present, before the machine is suspended. Use the
# special name "all" if you would like all ALSA sound modules to be
# removed. The modules that are removed will be loaded again after
# resume.  Currently this only has an effect if you are using apmd.
# Examples:
#     Value         Action at suspend time
#     ""            Do nothing
#     "snd-cs46xx"  Stop sound processes and remove the snd-cs46xx module
#     "all"         Stop sound processes and remove all ALSA modules
force_unload_modules_before_suspend=""
options snd-hda-intel model=3stack-dig

```

I've spent way too many hours on this and would really like to get it sorted out.

Many Thanks
Phil

---

### Post by pssturges on 2008-11-26
Quick update... I just updated my kernel to 2.6.27-7-generic via repositories. Audio on my system has returned to the status as in the first post. Still no sound..

---

### Post by pssturges on 2008-12-03
Still no sound. Anyone?

---

### Post by Sylchat on 2008-12-03
I don't know if it can help you. I have rev.3 on HP Pavillon and had no sound until 8.04. On 7.10 I had to use the latest ALSA drivers.

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

I compared the files, I have /usr/share/alsa-base/alsa.default (with a dot, not a dash). You have an extra line in your alsa-default:
14c14
<
---
> options snd-hda-intel model=3stack-dig

And 2 lines in your alsa-base:
42a43,44
> options snd-hda-intel model=mitac
> options snd-hda-intel enable_msi=1

But my alsa-base is in /etc/modprobe.d/alsa-base.

---

### Post by 235711 Specimen on 2008-12-05
I'm having the same (or a very similar problem) on my MacBook Pro (this has the same soundcard as your computer: the Intel Corporation 82801H).  I can see the devices under "lspci -v", and also under "aplay -l", I named myself in the permissions in "/etc/group", and still no audio.

I've read - but I don't remember where - that the driver for this sound card hasn't been publicly released from Intel, which would mean I might have to edit a file of some sort (essentially writing a driver?).  Don't take my word for that, but know that I've been looking into the same thing.

---

### Post by pssturges on 2008-12-06
Well I finally have sound! Sort of... The info I used to get it going can be found [here.]("https://help.ubuntu.com/community/HdaIntelSoundHowto") The important bit that actually got it going was the bit about "options snd-hda-intel probe_mask=1". I simply added that line to my /etc/modprobe.d/alsa-base.

The only problem I still have is that the built-in subwoofer is not working at all, so the sound is really thin and tinny. So I guess that's a partial solved?

I'd would love to get the subby going but at least I have some sound now.

Thanks to those who helped out.

Cheers
Phil

---

