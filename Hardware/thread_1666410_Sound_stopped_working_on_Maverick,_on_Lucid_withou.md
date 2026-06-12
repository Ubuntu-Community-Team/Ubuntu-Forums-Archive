---
title: "Sound stopped working on Maverick, on Lucid without problems"
date: 2011-01-13
forum: Hardware
---

### Post by Heliooos on 2011-01-13
Hi,
last weekend we installed new Vinux 3.1 (based on ubuntu Maverick) on my sister`s laptop. First it seemed to work OK. Then my sister removed few games installed there (Warzone etc.) and after reboot there was no sound. In settings the audio card panel was empty and as output there is only *"dummy output"* available.

Sound card is following type:
```
aplay -l
**** Seznam PLAYBACK Hardwarových za&#345;ízení ****
karta 0: Intel [HDA Intel], za&#345;ízení 0: AD198x Analog [AD198x Analog]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
petra@psychopetra:~/Plocha$ 
```

I also checked google and found something here [on this forum](http://ubuntuforums.org/showthread.php?t=1611131&page=2).
I did this according to the advices there
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils
```
then:
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
```
and finally:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
the file is here:
```
alsa-base.conf:

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

```
and I also added ```
options snd-hda-intel model=auto
```

I do not know, why, but after reboot the sound worked. However, my sister later reported, that problem remains.

I also found some info, that this could be caused by pulseaudio and using this  [tutorial](https://wiki.ubuntu.com/PulseAudio/Log) I created the [log]("http://sharetext.org/AP6").

While performing the testing and creating the log, Orca and sound (tested some video in SMPlayer) was working. So I assume, that there is some problem - that pulseaudio is not running. When executing *pulseaudio*, in terminal, the sound works and in PulseAudio Device Chooser I have then also alsa.output.pci-0000_00_1b.0.analog-stereo instead of only Dummy Output. Unluckily, after some time pulseaudio suddendly dies.

any advice? :(
I am currently thinking about downgrade back to Lucid, which worked OK.

---

