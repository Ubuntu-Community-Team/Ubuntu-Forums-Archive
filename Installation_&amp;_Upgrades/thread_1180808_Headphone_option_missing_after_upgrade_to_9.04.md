---
title: "Headphone option missing after upgrade to 9.04"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by ccorti on 2009-06-07
I upgraded from 8.04 (to 8.10 and then) to 9.04 on Dell Dimension C521, AMD 64. Now, the Alsa Mixer Preferences does not have a headphone option. The speakers work, but when I plug in headphones, the volume immediately begins to decrease until there is silence. After removing the headphones, speakers do not work again until after reboot.  (I have tried several suggestions from the forum, but nothing seems applicable - or at least does not fix the problem). 

I would very much appreciate any help. Here are some particulars that might provide a clue:

!!Kernel Information
!!------------------

Kernel release:    2.6.28-11-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.20
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_usb_audio
snd_usb_audio


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe024000 irq 23
 1 [U0x46d0x8b6    ]: USB-Audio - USB Device 0x46d:0x8b6
                      USB Device 0x46d:0x8b6 at usb-0000:00:0b.0-7, full speed
 2 [Camera         ]: USB-Audio - Camera
                      Camera at usb-0000:00:0b.0-8, full speed


!!PCI Soundcards installed in the system
!!--------------------------------------

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:10.1 0403: 10de:026c (rev a2)
    Subsystem: 1028:01f4


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2



APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 1: U0x46d0x8b6 [USB Device 0x46d:0x8b6], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Camera [Camera], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [NVidia]

Card hw:0 'NVidia'/'HDA NVidia at 0xfe024000 irq 23'
  Mixer name    : 'SigmaTel STAC9227'
  Components    : 'HDA:83847618,102801f4,00100201'
  Controls      : 31
  Simple ctrls  : 21


!!All Loaded Modules
!!------------------

Module
binfmt_misc
ppdev
video
output
input_polldev
lp
parport
snd_hda_codec_idt
snd_usb_audio
snd_hda_intel
snd_hda_codec
snd_usb_lib
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_seq_midi_event
snd_seq
snd_timer
snd_rawmidi
snd_seq_device
snd_hwdep
psmouse
quickcam_messenger
usbvideo
pwc
snd
soundcore
snd_page_alloc
dcdbas
serio_raw
pcspkr
k8temp
i2c_nforce2
usbhid
compat_ioctl32
videodev
v4l1_compat
nvidia
b44
ssb
mii
fbcon
tileblit
font
bitblit
softcursor

Thanks in advance for your help and direction. 

Chris

---

