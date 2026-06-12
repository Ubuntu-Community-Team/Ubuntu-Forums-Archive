---
title: "no sound after kernel update 2.6.22-14.47"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by hrabeX on 2007-12-19
Today (2007-12-19) my system updated to 2.6.22-14.47 kernel. After reboot I have no sound. 
alsamixer:
```
alsamixer: function snd_ctl_open failed for default: No such device
```

aplay:
```
aplay: device_list:204: no soundcards found...
```

lshw -C multimedia:
```
  *-multimedia UNCLAIMED
       description: Audio device
       product: High Definition Audio/AC'97 Host Controller
       vendor: ALi Corporation
       physical id: 1d
       bus info: pci@0000:00:1d.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=128 maxlatency=80 mingnt=16
```

Any ideas?

---

### Post by reckless2k2 on 2007-12-19
this wouldn't be the first time trust me. guery the community docs on troubleshooting sound. it'll instruct you to reinstall alsa and a few more things ..yadda...on how to do it all.

---

### Post by heffo_j on 2007-12-19
Hi HrabeX,

1. Go to Synaptic and check to see that everything is up to date. Do this by clicking "mark all upgrades"

If this doesn't solve the problem:

2. Reinstall the ALSA driver

Cheers
John

---

