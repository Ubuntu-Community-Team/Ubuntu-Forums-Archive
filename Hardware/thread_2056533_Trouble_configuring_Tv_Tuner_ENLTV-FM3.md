---
title: "Trouble configuring Tv Tuner ENLTV-FM3"
date: 2012-09-11
forum: Hardware
---

### Post by lenon3579 on 2012-09-11
hi guys.

I'm new at Ubuntu, migrated from windows just last week and still can't configure my Tv Tuner card.

And I'm from Brazil, so sorry for the miss-writings.

well... it's the card ENLTV-FM3

```
$ sudo lspci -v
03:07.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
    Subsystem: Device 1a7f:2108
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [40] Power Management version 1
    Kernel driver in use: saa7134
    Kernel modules: saa7134

```I've tried configuring the saa7134.conf:

```
options saa7134 card=x tuner=y
```with cards 107, 108 and 149. And tuner 37, 61 and 69.

following a tutorial found on internet ([http://xoloescuintle.wordpress.com/2010/11/10/instalar-tarjeta-de-tv-encore-enltv-fm3/](http://xoloescuintle.wordpress.com/2010/11/10/instalar-tarjeta-de-tv-encore-enltv-fm3/)), i've configured the alsa-base.conf like this:

```

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
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
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { modprobe -Qb saa7134-alsa -card=107 tuner=37 ; : ; }
```and also tried

```

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
#install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
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
#install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { modprobe -Qb saa7134-alsa -card=107 tuner=37 ; : ; }
```when I try tvtime in normal user:

```
A correr tvtime 1.0.2.
A ler configuração a partir de /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/lenon/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Incapaz de alterar o dono de /home/lenon/.tvtime/tvtime.xml: Permission denied. //translating: incapable of changing the owner of
mixer: find error: Success
mixer: Can't open mixer default, mixer volume and mute unavailable.
mixer: Can't open device default/Line, mixer volume and mute unavailable.
I/O error : Permission denied
I/O error : Permission denied

[and then when I ask to search for channels]:

I/O error : Permission denied //a lot of lines like that]
I/O warning : failed to load external entity "/home/lenon/.tvtime/stationlist.xml"
station: No station file found, creating a new one.
I/O error : Permission denied
I/O error : Permission denied

and when I closed the program:

I/O error : Permission denied //another lot of lines like that]
I/O warning : failed to load external entity "/home/lenon/.tvtime/stationlist.xml"
station: No station file found, creating a new one.
I/O error : Permission denied
I/O error : Permission denied
```so I tried to run it in sudo:

```
A correr tvtime 1.0.2.
A ler configuração a partir de /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/lenon/.tvtime/tvtime.xml"
mixer: find error: Success
mixer: Can't open mixer default, mixer volume and mute unavailable.
mixer: Can't open device default/Line, mixer volume and mute unavailable.
I/O warning : failed to load external entity "/home/lenon/.tvtime/stationlist.xml"
station: No station file found, creating a new one.
Obrigado por usar o tvtime.
```and then in xawtv, it gave the same lines in normal user and in sudo:

```
This is xawtv-3.102, running on Linux/x86_64 (3.2.0-29-generic)
xinerama 0: 1024x768+0+0
vid-open-auto: using analog TV device /dev/video0
WARNING: No DGA direct video mode for this display.
WARNING: keeping fbuf pitch at: 4096, as no base addr was detected
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
v4l2: WARNING: framebuffer base address mismatch
v4l2: me=(nil) v4l=(nil)
Alsa devices: cap: hw:1,0 (/dev/video0), out: default
alsa: stream started from hw:1,0 to default (32000 Hz, buffer delay = 60,00 ms)
ALSA lib pcm.c:7339:(snd_pcm_recover) overrun occurred
ALSA lib pcm.c:7339:(snd_pcm_recover) overrun occurred
ALSA lib pcm.c:7339:(snd_pcm_recover) overrun occurred //and that line keeped on repeating all the way while the program was running]
```what can I do? what can be the problem?

I NEED TO WATCH DOCTOR WHO!!!

---

