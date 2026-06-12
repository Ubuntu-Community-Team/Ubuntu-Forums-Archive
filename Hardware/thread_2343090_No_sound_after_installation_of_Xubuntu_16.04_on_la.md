---
title: "No sound after installation of Xubuntu 16.04 on laptop Toshiba Satellite L30-115"
date: 2016-11-13
forum: Hardware
---

### Post by namruf152 on 2016-11-13
Hello.
Recently I bought an old laptop and I wanted to install some light-weight Linux OS. So I've chosen Xubuntu in version 16.04. Previously I have Windows XP OS installed and everything work properly. Unfortunately after Xubuntu installation, laptop is no longer make any sound from speakers (no system notification sound, no sound from media players, no sound from Youtube). I can hear sound from headphones when these are connected in but volume is very low.

I've googled around a bit and tried every solution which I found but none of these have helped:

[LIST]
[*] reloading the drivers via *sudo alsa force-reload,* 
[*]reinstaling Puseaudio and Alsa via *sudo apt-get remove --purge pulseaudio alsa-base; sudo apt-get install pulseaudio alsa-base,* 
[*]checking *alsamixer *if everything is unmuted, 
[*]adding some additional options to */etc/modprobe.d/alsa-base.conf*. As I'm not very experianced in this subject I only tried to add some additional lines from example solutions, make reload and reboot. None of them have help so I left the default version, 
[*]installing additional packages *[I]sudo apt-get install ubuntu-restricted-extras ubuntu-restricted-addons,*[/I] 
[*]installing VLC and reseting configuration via its GUI (some users have noticed that somtimes this helps) 
[/LIST]

I assume that the problem is connected to Alsa and my sound card HDA ATI SB. Some additional information:

Hardinfo report:
[http://pastebin.com/uG3LeZCM](http://pastebin.com/uG3LeZCM)

```
pawel19@pawel-Satellite-L30:~$ cat /etc/modprobe.d/alsa-base.conf 
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
install  snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && {  /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe  --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install  snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install  snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install  snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ;  /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install  snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install  snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install  snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install  saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
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

```
pawel19@pawel-Satellite-L30:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Alsa-info.sh output:
[http://pastebin.com/bhZhkUsY](http://pastebin.com/bhZhkUsY)


[ATTACH=CONFIG]272110[/ATTACH][ATTACH=CONFIG]272111[/ATTACH]

I would appertiace any help. Thanks in advance!

---

