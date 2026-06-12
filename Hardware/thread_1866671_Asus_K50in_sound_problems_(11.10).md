---
title: "Asus K50in sound problems (11.10)"
date: 2011-10-21
forum: Hardware
---

### Post by irem-altan on 2011-10-21
Hello,
I have just installed 11.10 on my asus k50in laptop.  There does not seem to be any problem (yet) other than some sound problems.  The speakers work fine (possibly a bit less loud than they should, but I'm not sure), but when I plug in an earphone, I cannot hear anything.  Interestingly, if the jack is plugged halfway through, I can get some sound, from only the left side, exactly as you would get if you had a connectivity problem.  I have tried some things, however I am a very new user of ubuntu, so I am a bit lost.  I'd appreciate it if anyone could help.

---

### Post by mike1312 on 2011-12-30
Same problem: asus k50in
headphones doesnt work
chipset ALC662```
lspci | grep Audio
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
```here is alsa conf as it is

```
cat /etc/modprobe.d/alsa-base.conf 
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
# the last line
#options snd-hda-intel model=asus-mode3


```
ive tried some models for ```
options snd-hda-intel model=
```from [here]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt"), but it doesnt seem to work

this may be useful 
```
dmesg | grep sound
[   21.288291] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:08.0/sound/card0/input10
[   21.288399] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:08.0/sound/card0/input11

```


Any help?

---

### Post by mike1312 on 2012-01-16
Hmm After several reboots headphones turned on. Everything is ok now.

---

