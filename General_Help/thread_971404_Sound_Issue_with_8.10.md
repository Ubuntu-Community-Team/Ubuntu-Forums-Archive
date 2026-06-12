---
title: "Sound Issue with 8.10"
date: 2008-11-04
forum: General Help
---

### Post by unix192 on 2008-11-04
I have been using ubuntu for a year now and it is GREAT!!

This is my first time posting in the Forum I have been able to figure out every thing up to now, so in the last 6 months my sound just shuts off and a reboot fixes it every time. When I go to the sound manager and hit test it says there is another application using. I mess around a lot bash, apps u name so I just figured I broke it but now this is happening with my fresh install of Ubuntu 8.10. Please help:

:confused:

---

### Post by unix192 on 2008-11-07
any one have any suggestions on how to troubleshoot a sound issue out there? I have been looking through forums for days I have tried to kill/restart pulse audio, change sound setting with no effect only a restart will bring the sound back. any help is appreciated

**here is what I have**
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


](*,)

frustrated ubuntu user

---

### Post by Wayne_V on 2008-11-07
This happens to me as well with 8.10.   I haven't had time to try to figure out why yet, but the following command fixes things without a reboot:

$ sudo /sbin/alsa force-reload

My config is:

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by unix192 on 2008-11-07
Thanks you very much for this information very helpful, this command works great to restore sound with out a restart. At least I know where to start looking for issues, alsa must be the culprit. an additional note I went to the sound preferences when my sound stoped and hit test and get the following error.

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect: Connection refused

\\:D/

---

### Post by unix192 on 2008-11-20
Well after weeks of research and troubleshooting I think I have fixed this issue on my machine. Only further monitoring will tell I guess but so far so good.

I followed this link
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

1) ended up uninstalling/reinstalling ALSA and pulse audio
2) changing all devices in   system -> Preferences -> Sound  to ALSA 
3) made pulse audio start up on boot by placing in  system -> Preferences -> sessions
4) opened terminal type in "alsamixer"
5) unmute all channels
6) restarted PC

EVERY THING WORKS FINE!!!
:guitar:

HOPE THIS HELPS  =D>

---

