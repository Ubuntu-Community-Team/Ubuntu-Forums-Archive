---
title: "Loud pop out of speakers"
date: 2011-09-19
forum: Hardware
---

### Post by nomko on 2011-09-19
Hi,

I have a question. Every time when i have my speakers on hey pop after a while which is very annoying. I've done some research on the internet and the only solutions i find are ment for 9.04/9.10. I'm using 10.04.3 rigth now.

Most solutions are to add/modify the following line:

[B]options snd-hda-intel power_save=10 power_save_controller=N

[/B]In my alsa-base i don't have it, How can i get rid of that pop?

Info:
**LSPCI**
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
**Kernel**
2.6.32-33-generic

**Alsa-base.conf**
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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

---

### Post by .... on 2011-09-19
> In my alsa-base i don't have it
The file is now called /etc/modprobe.d/alsa-base.conf

---

### Post by nomko on 2011-09-19
Thanks for your answer, but this still doesn't solve my problem.

---

### Post by .... on 2011-09-19
So you actually copied/pasted that line to the end of the file and restarted the system (or at least reloaded alsa)?

---

### Post by nomko on 2011-09-20
> **.... said:**
> So you actually copied/pasted that line to the end of the file and restarted the system (or at least reloaded alsa)?

According to you i have to add this:

```
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```


And how do i restart alsa?

---

### Post by nomko on 2011-09-21
I tried to add the above lines. But i still got the pop in my speakers. I even found a site to update ALSA. Did this and still no solution.

Anybody, please, how do i get rid of that popping sound?

---

### Post by nomko on 2011-09-23
Anybody?

---

### Post by nomko on 2011-09-24
Bump

---

### Post by .... on 2011-09-24
```
Power-Saving
~~~~~~~~~~~~
The power-saving is a kind of auto-suspend of the device.  When the
device is inactive for a certain time, the device is automatically
turned off to save the power.  The time to go down is specified via
`power_save` module option, and this option can be changed dynamically
via sysfs.

The power-saving won't work when the analog loopback is enabled on
some codecs.  Make sure that you mute all unneeded signal routes when
you want the power-saving.

The power-saving feature might cause audible click noises at each
power-down/up depending on the device.  Some of them might be
solvable, but some are hard, I'm afraid.  Some distros such as
openSUSE enables the power-saving feature automatically when the power
cable is unplugged.  Thus, if you hear noises, suspect first the
power-saving.  See /sys/module/snd_hda_intel/parameters/power_save to
check the current value.  If it's non-zero, the feature is turned on.
```So check the value of /sys/module/snd_hda_intel/parameters/power_save
```
cat /sys/module/snd_hda_intel/parameters/power_save
```

---

