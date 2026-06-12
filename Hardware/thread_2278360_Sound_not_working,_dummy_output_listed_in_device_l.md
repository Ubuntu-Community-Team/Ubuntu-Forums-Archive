---
title: "Sound not working, dummy output listed in device list"
date: 2015-05-16
forum: Hardware
---

### Post by miatawnt2b on 2015-05-16
I am running a fresh 15.04 install and am having problems with sound. The devices in gnome only lists "dummy output" and sound is not actually working.

cat /proc/asound/cards lists nothing, but if I do a 'alsa force-reload' i can see the audio device. Sound still however doesn't work.

```

root@switch:~# cat /proc/asound/cards
--- no soundcards ---

root@switch:~# sudo alsa force-reload
Unloading ALSA sound driver modules: snd-soc-sst-baytrail-pcm snd-soc-sst-dsp snd-soc-sst-byt-rt5640-mach snd-soc-rt5640 snd-intel-sst-acpi snd-intel-sst-core snd-soc-sst-mfld-platform snd-soc-rl6231 snd-seq-midi snd-soc-core snd-seq-midi-event snd-compress snd-rawmidi snd-pcm-dmaengine snd-pcm snd-seq snd-seq-device snd-timer snd-soc-sst-acpi.
Loading ALSA sound driver modules: snd-soc-sst-baytrail-pcm snd-soc-sst-dsp snd-soc-sst-byt-rt5640-mach snd-soc-rt5640 snd-intel-sst-acpi snd-intel-sst-core snd-soc-sst-mfld-platform snd-soc-rl6231 snd-seq-midi snd-soc-core snd-seq-midi-event snd-compress snd-rawmidi snd-pcm-dmaengine snd-pcm snd-seq snd-seq-device snd-timer snd-soc-sst-acpi.

root@switch:~# cat /proc/asound/cards
 0 [baytrailcraudio]: baytrailcraudio - baytrailcraudio
                      baytrailcraudio
root@switch:~# 

```

Any ideas on getting this working would be appreciated. I have tried all the standard 15.04 kernels, but have also installed teh 4.0 stable kernel, but that didn't help.

Any thoughts on getting this working?

---

### Post by jkoch-contact on 2015-05-17
i have the same issues on a Asus x205ta netbook but alsa force-reload doesn't change anything on /proc/asound/cards

---

### Post by MickM on 2015-05-19
I too have no sound after upgrading to 15.04  I have sound when I plug in a set of speakers.

---

### Post by miatawnt2b on 2015-05-20
bumping this up... please help

---

### Post by coffeecat on 2015-05-20
*Thread moved to **Hardware**.*

---

### Post by zhangweiwu on 2015-05-26
Same problem on T100 ASUS here. Strange enough, although Windows sounds ok, and list a Intel SST Audio Device, which I assume same as yours 'cos of sst keyword, lspci and lsusb doesn't show any audio device for me.

---

### Post by miatawnt2b on 2015-07-27
Bumping this up to see if anyone has further ideas.

---

### Post by Melodie on 2015-07-27
Hi, 

Please give the output for the command:

```
aplay -l
```

---

### Post by zhangweiwu on 2015-07-27
In my case:

```

$ sudo LANG=en_US aplay -l
aplay: device_list:268: no soundcards found...

```

In my case, alsa force-reload (as root) doesn't make any difference, still no soundcards.

---

### Post by miatawnt2b on 2015-07-27
nothing after boot, but baytrail listed after an alsa force-reload

```

root@switch:~# aplay -l
aplay: device_list:268: no soundcards found...
root@switch:~# 
root@switch:~# sudo alsa force-reload
Unloading ALSA sound driver modules: snd-soc-sst-byt-rt5640-mach snd-soc-sst-baytrail-pcm snd-soc-sst-ipc snd-soc-sst-dsp snd-intel-sst-acpi snd-intel-sst-core snd-soc-rt5640 snd-soc-sst-mfld-platform snd-soc-rl6231 snd-soc-core snd-compress snd-seq-midi snd-pcm-dmaengine snd-seq-midi-event snd-rawmidi snd-pcm snd-seq snd-seq-device snd-timer snd-soc-sst-acpi.
Loading ALSA sound driver modules: snd-soc-sst-byt-rt5640-mach snd-soc-sst-baytrail-pcm snd-soc-sst-ipc snd-soc-sst-dsp snd-intel-sst-acpi snd-intel-sst-core snd-soc-rt5640 snd-soc-sst-mfld-platform snd-soc-rl6231 snd-soc-core snd-compress snd-seq-midi snd-pcm-dmaengine snd-seq-midi-event snd-rawmidi snd-pcm snd-seq snd-seq-device snd-timer snd-soc-sst-acpi.
root@switch:~# 
root@switch:~# 
root@switch:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: baytrailcraudio [baytrailcraudio], device 0: Baytrail Audio (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@switch:~# 

```

---

### Post by miatawnt2b on 2016-05-20
OK, I'm trying again using 16.04. I've had pretty much the same issues.  I blacklisted snd-soc-sst-acpi snd_soc_sst_acpi and now aplay -l will show the baytrail audio on boot.  I still however have dummy output and no sound. If anyone can help I would appreciate it.

---

### Post by miatawnt2b on 2016-05-27
Does anyone have any ideas?

---

