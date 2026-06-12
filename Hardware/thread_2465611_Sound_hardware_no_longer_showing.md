---
title: "Sound hardware no longer showing"
date: 2021-08-06
forum: Hardware
---

### Post by lsutiger on 2021-08-06
When I go to Sound in Settings, the hardware is no longer listed. 
Output from aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Not sure how to figure this one out.
From another post, I installed pavucontrol. When I run it I get the following
```
Connection to PulseAudio failed. Automatic retry in 5s
In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server in client.conf is misconfigured.
If this is the cased, then PulseAudio should autospawn again, or if this is not configured you should run start-pulseaudio-x11 manually

```
When I run that I get the following
```
Connection failure: Connection refused
pa_context_connect() failed: Connection refused
```

I've reinstalled pulseaudio. When I try to run it I receive the following```
E: [pulseaudio] module-ladspa-sink.c: Master sink not found
E: [pulseaudio] module.c: Failed to load module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master=bluez_sink.EB_06_EF_8B_61_91 plugin=mbeq_1197 label=mbeq control=0.0,3.6,1.3,-2.3,3.5,6.3,3.5,3.5,3.5,3.5,3.5,2.5,2.5,0.0,0.0"): initialization failed.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.

```

Created temporary user and sound hardware is showing under that user. :-/

Update: Renamed the ~/.config/pulse folder and restarted. It is now available. Not at home so I will see if this worked to get audio back.
Note: Audio icon is no longer in the task bar
Additional note: Got home and touched the volume button on keyboard and volume control appeared on panel.

---

