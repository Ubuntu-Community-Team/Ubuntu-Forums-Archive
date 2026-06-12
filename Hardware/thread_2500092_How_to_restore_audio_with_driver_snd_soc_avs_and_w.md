---
title: "How to restore audio with driver snd_soc_avs and with &quot;Dummy output&quot; in sound set.s"
date: 2024-08-22
forum: Hardware
---

### Post by f(fanta) on 2024-08-22
I am posting this here because the "Dummy output" sound device issue has many possible fixes, but the issue I had could be fixed only in a very specific way. I hope this can help others with the same issue find the solution.

Reproduced on: Dell XPS 15 running Ubuntu 22.04 or Ubuntu 24.04

Symptoms: there is no audio coming from the loudspeakers nor from headphones. The system doesn't detect the headphones when connected. The only audio device listed under `Settings` > `Audio` is a `Dummy output`. Audio works fine under Win10.

Reproducibility: The issue is not systematic and may disappear after a reboot, or a fresh installation of Ubuntu 24.04, but represents itself after a couple boots/reboots. Issue may occur already when booting from a USB stick for the installation of Ubuntu  24.04.

A driver `snd_soc_avs` is loaded when the issue is reproduced, instead of `snd_hda_intel`. 

When audio doens't work:
```
fanta@ribosome:~/Documents/audio$ inxi -xxz --audio
Audio:
  Device-1: Intel CM238 HD Audio vendor: Dell driver: snd_soc_avs v: kernel
    bus-ID: 00:1f.3 chip-ID: 8086:a171
  API: ALSA v: k6.8.0-41-generic status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active with: 1: pipewire-pulse
    status: active 2: wireplumber status: active 3: pipewire-alsa type: plugin
```
and also, the output of `aplay --list-devices` is blank.


When audio works OK:
```
fanta@ribosome:~$ inxi -xxz --audio
Audio:
  Device-1: Intel CM238 HD Audio vendor: Dell driver: snd_hda_intel v: kernel
    bus-ID: 00:1f.3 chip-ID: 8086:a171
  API: ALSA v: k6.8.0-40-generic status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active with: 1: pipewire-pulse
    status: active 2: wireplumber status: active 3: pipewire-alsa type: plugin
```


Solution: blacklist the offending driver. 
I found the solution provided by user `V1del` here [https://bbs.archlinux.org/viewtopic.php?pid=2164192#p2164192](https://bbs.archlinux.org/viewtopic.php?pid=2164192#p2164192)
Also see [https://wiki.archlinux.org/title/Kernel_module#Blacklisting](https://wiki.archlinux.org/title/Kernel_module#Blacklisting)
The short of it, under `/etc/modprobe.d/` make a new text file with extension `.conf` and write this line into it:
```
blacklist snd_soc_avs
```
Then reboot.

---

