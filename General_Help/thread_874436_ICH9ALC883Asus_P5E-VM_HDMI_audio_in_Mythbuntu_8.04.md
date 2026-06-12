---
title: "ICH9/ALC883/Asus P5E-VM HDMI audio in Mythbuntu 8.04"
date: 2008-07-29
forum: General Help
---

### Post by ashgromnies on 2008-07-29
So I am using Ubuntu 8.04(Mythbuntu actually) for my HTPC install and everything is working fine except for the sound. I've Googled and found other people with this problem and tried every solution I've found and nothing's worked so I'm turning here hoping someone knows something the rest of the internet doesn't or can spot something drastically stupid I'm doing.

I have the Asus P5E-VM HDMI motherboard which has an Intel ICH9 chipset for audio. I am trying to output via HDMI.

I've followed EVERYTHING I found here: [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=(HdaIntelSoundHowto)](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=(HdaIntelSoundHowto))

I've tried using alsa 1.0.16, 1.0.17 and the version from [www.realtek.com.tw](www.realtek.com.tw) and none worked. I have my volume turned up all the way in the mixer.

I am trying to get the audio over HDMI to work - it worked fine in Windows and everything is connected EXACTLY the way it was when Windows was working - I get a slight staticky hum when the computer comes up but no sound.

```
chris@htpc:~$ uname -r
2.6.24-19-generic

```

```
chris@htpc:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe7f4000 irq 22
```

```
chris@htpc:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

```

```

**/etc/modprobe.d/alsa-base**

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
options snd-hda-intel position_fix=1 model=6stack-dig-demo


  alias char-major-116 snd
  alias snd-card-0 snd-hda-intel
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

(note: using the ALSA driver I got from Realtek right now... I also tried the 1.0.16 that came with Ubuntu and 1.0.17 from ALSA's site)

```

chris@htpc:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Jun 18 2008 for kernel 2.6.24-19-generic (SMP).

```

```

chris@htpc:~$ cat /proc/asound/card0/codec\#* | grep Codec
Codec: Realtek ALC883
Codec: Generic 1095 SI HDMI

```

```

chris@htpc:~$ sudo alsactl -d names 0
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM rear:0
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM rear:0
ALSA lib rawmidi_hw.c:233:(snd_rawmidi_hw_open) open /dev/snd/midiC0D0 failed: No such device
ALSA lib rawmidi_hw.c:233:(snd_rawmidi_hw_open) open /dev/snd/midiC0D0 failed: No such device

```

```
chris@htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I think I want card 0, device 3 - how do I make sure I'm outputting to that?

Nothing shows up in `dmesg | grep -i audio` or `dmesg | grep -i hda`.


If there's any more information you need from me, please let me know. I'm at my wit's end with this.

---

### Post by ashgromnies on 2008-07-30
Bumping to catch the day crowd... still haven't had any luck with this. I know some other people have gotten the HDMI audio on this motherboard working.

---

### Post by ashgromnies on 2008-08-01
No ideas from anyone :confused:

---

### Post by jtyoder on 2008-08-07
There are a couple items happening here. The first issue is the HDMI Audio is the second device for ALSA. You are correct that it is card 0, device 3. This can be varified by doing 2 commands. The first is:
  $ aplay -L

The output should have a similar look to the following:
------------------------------
default:CARD=SB
HDA ATI SB, ALC882 Analog
Default Audio Device
front:CARD=SB,DEV=0
HDA ATI SB, ALC882 Analog
Front speakers
surround40:CARD=SB,DEV=0
HDA ATI SB, ALC882 Analog
4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
HDA ATI SB, ALC882 Analog
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
HDA ATI SB, ALC882 Analog
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
HDA ATI SB, ALC882 Analog
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
HDA ATI SB, ALC882 Analog
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
HDA ATI SB, ALC882 Digital
IEC958 (S/PDIF) Digital Audio Output
null
Discard all samples (playback) or generate zero samples (capture)
front:CARD=HDMI
HDA ATI HDMI
Front speakers
surround40:CARD=HDMI
HDA ATI HDMI
4.0 Surround output to Front and Rear speakers
surround41:CARD=HDMI
HDA ATI HDMI
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=HDMI
HDA ATI HDMI
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=HDMI
HDA ATI HDMI
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=HDMI
HDA ATI HDMI
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
------------------------------

The second is:

  $ asoundconf list

The output of this command should look like:
------------------------------
Names of available sound cards:
SB
HDMI
------------------------------

These query the device and determine where the HDMI port for ALSA resides. To make HDMI the default output issue:

  $ asoundconf set-default-card HDMI

This will make HDMI the default and it should be mostly happy. To test if HDMI is avtually working issuing:
  
  $ mplayer <media clip> -ao alsa:device=hw=<CARD>.<DEVICE>

Where <CARD> is 0, and <DEVICE> is 3 should output audio through HDMI. 

The only other item found that may cause issues is that ALSA apparently looks by default for devices to be at DEVICE 0 and this appears to be at DEVICE 3. The temporary workaround for this is to create a symbolic link from /dev/snd/pcmC<CARD>D<EVICE>p to /dev/snd/pcmC<CARD>D0p. This may not be necissary in your case. Also, I have not figured out why this the sym link was required. I am still investigating this.

---

