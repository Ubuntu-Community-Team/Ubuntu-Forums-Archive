---
title: "Order of ALSA HDMI audio devices change on suspend"
date: 2019-01-12
forum: Hardware
---

### Post by arzkah on 2019-01-12
ALSA lists Nvidia GPUs as four separate HDMI outputs. The outputs are identical, but obviously one of them is the one where the HDMI cable is connected. My problem is, that these devices change their order when the machine is put to suspend.

After booting, the sounds are output to speakers when the selected output is device 7 [HDMI1]. When going to suspend for the first time, then correct device changes its number to device 3 [HDMI 0]. Device 3 stays with subsequent suspends until the next reboot. Therefore, I have set my asound.conf to default to device 3 and go to suspend once after every reboot to get the sounds working again. I dualboot to Win10 for gaming, so I have to do this quite often.

The problem started after an apt dist-upgrade on June 2018. First I suspected the Nvidia proprietary drivers that were upgraded from 370 to 396 at the same time, but I've now verified that the problem seems to be elsewehere. Earlier I had GTX960 on my PC but the problem persisted over the GPU upgrade to GTX1060. 

My Ubuntu is a minimal install of 16.04 with Openbox and ALSA (no Pulseaudio). I did a clean install of 18.04 minimal on a separate partition and the problem appeared even though the Nvidia proprietary drivers or any other packages were not installed. This led me thinking that it's not an Nvidia driver problem.

A dirty fix would be to modify asound.conf with a suspend script, but I have some software which don't use the default device in asound.conf and the output is declared manually. Therefore, this fix wouldn't be feasible and I'm eager to find a better solution if anyone had an idea about what's causing this. Please ask me if you want to see more output, log files etc. I'm not sure myself where to look, as the devices seem completely identical.

aplay -l reports:
```

me@htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

My asound.conf:
```

pcm.!default {
 type plug
 slave {
   pcm "avr_dmix"
 }
}


pcm.avr0 {
 type hw
 card NVidia
 device 7
}
pcm.avr1 {
 type hw
 card NVidia
 device 3
}

pcm.avr_dmix {
 type dmix
 ipc_key 1024
 ipc_perm 0666
 slave {
  pcm avr1
  channels 8
  period_time 0
  period_size 1024
  buffer_size 4096
  rate 48000
 }
 bindings {
  0 0
  1 1
  2 2
  3 3
  4 4
  5 5
  6 6
  7 7
 }
}

```

---

### Post by CatKiller on 2019-01-12
You know what's really great for this kind of thing?

PulseAudio.

---

### Post by arzkah on 2019-02-25
> **CatKiller said:**
> You know what's really great for this kind of thing?

PulseAudio.

Would Pulseaudio somehow detect the correct output? Isn't it just a new layer on top of ALSA?

The machine is a HTPC and runs only Kodi, so I'd prefer to keep it simple. Pulseaudio would bring other problems, and it's generally recommended to disable it on Kodi forums.

---

### Post by CatKiller on 2019-02-25
There is zero reason to ever disable PulseAudio. Anyone who tells you to is just wrong.

You've created an elaborate and fragile configuration file, and now you're contemplating writing your own set of scripts to enumerate all your outputs on every resume. That is a **long** way from "keeping it simple."

I, too, have an HTPC that runs Kodi, as well as being a client for Steam's in-home streaming. I'll tell you how much configuration I needed to do to get perfect audio in every single application, across reboots and suspends and updates: none at all.

Come out of the dark ages.

---

### Post by arzkah on 2019-02-26
> **CatKiller said:**
> There is zero reason to ever disable PulseAudio. Anyone who tells you to is just wrong.


Is the information in this wiki badly outdated? [https://kodi.wiki/view/PulseAudio](https://kodi.wiki/view/PulseAudio)

From the wiki it seems that there is a choice between stereo + passthrough or resampled multichannel without passthrough. And the passthrough doesn't handle TrueHD or DTS-HD.
I'm trying to fix the new quirks in my previously working setup with multichannel + passthrough.

I will give Pulse a try with the second Ubuntu installation and find out.

> 
You've created an elaborate and fragile configuration file, and now you're contemplating writing your own set of scripts to enumerate all your outputs on every resume. That is a **long** way from "keeping it simple."

- By simple I meant simplicity only in a manner of number of packets installed and the amount of software layers required for audio output
- I specifically said that the script is not a solution and I'm wondering if there's a real fix for that

 > 
I, too, have an HTPC that runs Kodi, as well as being a client for Steam's in-home streaming. I'll tell you how much configuration I needed to do to get perfect audio in every single application, across reboots and suspends and updates: none at all.

Come out of the dark ages.

Peace, I'm just asking if someone else encountered the same issue and perhaps had an idea what kind of software/driver update could have been the reason for this. I don't think I'm the only one living in the dark ages.

---

### Post by CatKiller on 2019-02-26
> **arzkah said:**
> I'm just asking if someone else encountered the same issue and perhaps had an idea what kind of software/driver update could have been the reason for this.

It wasn't necessarily an update that changed the behaviour specifically. Device numbers change unpredictably all the time. You see it commonly in hard drive numbers, too. Any change that caused some part of the initialisation to run better would cause this kind of thing.

Pulseaudio does a very good job of tracking which output is which, in a way that a static configuration file can't hope to do.

There is a *lot* of false advice out there regarding pulseaudio, either because of misinformation, or because it's fashionable to hate the developer for some reason in whichever bubble that person inhabits. I am saddened to learn that the Kodi developers are partaking in that.

---

