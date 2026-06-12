---
title: "amixer help"
date: 2012-11-12
forum: Hardware
---

### Post by b49P23TIvg on 2012-11-12
I do not understand the amixer man page or amixer tutorial I found.  I would like to control the microphone from the command line.  System is ubuntu 12.10 Lenovo T500 laptop without external hardware, without a dock.  And it all seems to work when I use the GUI controls ( $ arecord | aplay makes a nice echo feedback loop building to a delightful squeal.)  I presume enough information is here.  How, please, do I translate it to a valid and useful amixer command?

amixer contents  command output follow with microphone muted.

Thank you, Dave.


$ amixer contents
numid=22,iface=CARD,name='Dock Headphone Jack'
  ; type=BOOLEAN,access=r-------,values=1
  : values=off
numid=24,iface=CARD,name='Dock Mic Jack'
  ; type=BOOLEAN,access=r-------,values=1
  : values=off
numid=23,iface=CARD,name='Headphone Jack',index=1
  ; type=BOOLEAN,access=r-------,values=1
  : values=off
numid=26,iface=CARD,name='Internal Mic Phantom Jack'
  ; type=BOOLEAN,access=r-------,values=1
  : values=on
numid=25,iface=CARD,name='Mic Jack'
  ; type=BOOLEAN,access=r-------,values=1
  : values=off
numid=27,iface=CARD,name='SPDIF Phantom Jack'
  ; type=BOOLEAN,access=r-------,values=1
  : values=on
numid=21,iface=CARD,name='Speaker Phantom Jack'
  ; type=BOOLEAN,access=r-------,values=1
  : values=on
numid=18,iface=MIXER,name='Master Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=17,iface=MIXER,name='Master Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=74,step=0
  : values=54
  | dBscale-min=-74.00dB,step=1.00dB,mute=0
numid=4,iface=MIXER,name='Headphone Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=3,iface=MIXER,name='Headphone Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=74,step=0
  : values=74,74
  | dBscale-min=-74.00dB,step=1.00dB,mute=1
numid=28,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=255,step=0
  : values=254,254
  | dBscale-min=-51.00dB,step=0.20dB,mute=0
numid=8,iface=MIXER,name='Mic Boost Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=4,step=0
  : values=0,0
  | dBscale-min=0.00dB,step=10.00dB,mute=0
numid=9,iface=MIXER,name='Mic Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=80,step=0
  : values=0,0
  | dBscale-min=-74.00dB,step=1.00dB,mute=0
numid=16,iface=MIXER,name='IEC958 Default PCM Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=12,iface=MIXER,name='IEC958 Playback Con Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0xff AES2=0x00 AES3=0x00]
numid=13,iface=MIXER,name='IEC958 Playback Pro Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0x00 AES2=0x00 AES3=0x00]
numid=14,iface=MIXER,name='IEC958 Playback Default'
  ; type=IEC958,access=rw------,values=1
  : values=[AES0=0x04 AES1=0x00 AES2=0x00 AES3=0x00]
numid=15,iface=MIXER,name='IEC958 Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=5,iface=MIXER,name='Auto-Mute Mode'
  ; type=ENUMERATED,access=rw------,values=1,items=2
  ; Item #0 'Disabled'
  ; Item #1 'Enabled'
  : values=1
numid=20,iface=MIXER,name='Beep Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=19,iface=MIXER,name='Beep Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=3,step=0
  : values=0
  | dBscale-min=-18.00dB,step=6.00dB,mute=0
numid=29,iface=MIXER,name='Digital Capture Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=120,step=0
  : values=60,60
  | dBscale-min=-30.00dB,step=0.50dB,mute=0
numid=6,iface=MIXER,name='Dock Mic Boost Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=4,step=0
  : values=0,0
  | dBscale-min=0.00dB,step=10.00dB,mute=0
numid=7,iface=MIXER,name='Dock Mic Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=80,step=0
  : values=0,0
  | dBscale-min=-74.00dB,step=1.00dB,mute=0
numid=10,iface=MIXER,name='Internal Mic Boost Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=4,step=0
  : values=4,4
  | dBscale-min=0.00dB,step=12.00dB,mute=0
numid=11,iface=MIXER,name='Internal Mic Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=80,step=0
  : values=80,80
  | dBscale-min=-74.00dB,step=1.00dB,mute=0
numid=2,iface=MIXER,name='Speaker Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=1,iface=MIXER,name='Speaker Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=74,step=0
  : values=74,74
  | dBscale-min=-74.00dB,step=1.00dB,mute=1

---

