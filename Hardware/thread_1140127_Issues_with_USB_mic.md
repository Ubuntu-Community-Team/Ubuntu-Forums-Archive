---
title: "Issues with USB mic"
date: 2009-04-27
forum: Hardware
---

### Post by Dekafox on 2009-04-27
Running 8.04 (still :P) 64-bit Ubuntu.  I was recently given a Microsoft Lifechat LX_3000 USB headset, and I've been trying to get it to work fully with my system.  So far I've got playback working fine, the issue is with the sound capture.

I have all the pulseaudio packages installed, including padevchooser.  When I select "Volume Meter (Recording)" after setting the USB mic to default, I see the proper volume bar, and it responds correctly when I talk into it.  However, when I try to select "USB Audio" in System -> Preferances -> Sound, I get:
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for recording.

If I select "Pulseaudio Sound Server" it only uses the analog mic jack, regardless of which I have selected in padevchooser as default.

If I run "arecord -f S16_LE | aplay" the echo comes back from the USB mic, not the analog, no matter which I have set as default.

arecord -l shows:
```
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [Microsoft LifeChat LX-3000 ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have a asound.conf consisting of:
```
pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}
```

cat /proc/asound/cards gives:
```
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfc100000 irq 21
 1 [default        ]: USB-Audio - Microsoft LifeChat LX-3000 
                      Microsoft LifeChat LX-3000  at usb-0000:00:02.0-2, full speed

```

How can I correct this so I can select the USB mic for capture via Pulseaudio, and have it take over instead of the analog mic for all the apps?

---

### Post by Dekafox on 2009-04-27
Okay, Looks like I've got it half-working, via manually configuring my drivers in my Pulseaudio configuration

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
load-module module-alsa-sink device=hw:0,0
load-module module-alsa-sink device=hw:1,0
load-module module-alsa-source device_id=1 source_name=USB_Headset_Mic
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
#.endif
```

With this, the USB mic takes over as it should.  However, if I unplug the USB headset, pulseaudio crashes and won't restart until I plug it back in or change the config, presumably because it can't find the USB headset in hardware.  Is there another solution, or something I can add or change that'll let pulse keep working when I unplug the headset(and make it fall back to the analog capture)?

---

