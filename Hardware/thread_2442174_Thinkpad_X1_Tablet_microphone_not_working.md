---
title: "Thinkpad X1 Tablet microphone not working"
date: 2020-04-30
forum: Hardware
---

### Post by giancarlo642 on 2020-04-30
Hi,
I have a thinkpad X1 tablet 3rd Gen and I have installed Ubuntu 20.4 on it. I have a problem with the microphone. It is recognized but I can't record.
I have searched on the web but nothing helped me.

Some information on my HW

inxi -Fxz
```

System:    Kernel: 5.4.0-26-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Cinnamon 4.4.8 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Detachable System: LENOVO product: 20KKS0DH00 v: ThinkPad X1 Tablet Gen 3 
           serial: <filter> 
           Mobo: LENOVO model: 20KKS0DH00 v: SDK0J40697 WIN serial: <filter> UEFI: LENOVO 
           v: N1ZET76W(1.32 ) date: 07/18/2019 
...........
Graphics:  Device-1: Intel UHD Graphics 620 vendor: Lenovo driver: i915 v: kernel bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
           resolution: 3000x2000~60Hz 
           OpenGL: renderer: Mesa Intel UHD Graphics 620 (KBL GT2) v: 4.6 Mesa 20.0.4 
           direct render: Yes 
Audio:     Device-1: Intel Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Imaging Unit 
           vendor: Lenovo driver: ipu3-imgu bus ID: 00:05.0 
           Device-2: Intel vendor: Lenovo driver: ipu3-cio2 bus ID: 00:14.3 
           Device-3: Intel Sunrise Point-LP HD Audio vendor: Lenovo driver: snd_hda_intel v: kernel 
           bus ID: 00:1f.3 
           Sound Server: ALSA v: k5.4.0-26-generic 
...........
Sensors:   System Temperatures: cpu: 49.0 C mobo: N/A 
           Fan Speeds (RPM): cpu: 0 
........................... 
```

cat /proc/asound/cards
```
0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0x2ffb438000 irq 174
```
arecord -l

```
**** Lista di CAPTURE dispositivi hardware ****
scheda 0: PCH [HDA Intel PCH], dispositivo 0: ALC295 Analog [ALC295 Analog]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
```

amixer

```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 60 [69%] [-20.25dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Speaker',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Bass Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB]
  Front Right: Playback 87 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]
Simple mixer control 'Mic Mute-LED Mode',0
  Capabilities: enum
  Items: 'On' 'Off' 'Follow Capture' 'Follow Mute'
  Item0: 'Off'
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',3
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',4
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 63
  Front Left: Capture 63 [100%] [30.00dB] [on]
  Front Right: Capture 63 [100%] [30.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
```

I also found this [patch]("https://github.com/da-cali/linux-x1-tablet") but not for the microphone
It seems that the HW is recognized but there is something with the driver.
Does anyone can help me go further in the investigation?

Thanks

Gian Carlo

---

### Post by giancarlo642 on 2020-05-03
I'm also programming in C language (also some python and C++ but not so experienced as C). Is it possible to me to try to find the problem? How to do it?

Regards

Gian Carlo

---

