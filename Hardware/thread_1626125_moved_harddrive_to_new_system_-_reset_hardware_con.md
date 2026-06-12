---
title: "moved harddrive to new system - reset hardware configurations?"
date: 2010-11-19
forum: Hardware
---

### Post by alldaylong on 2010-11-19
hey all,

my old laptop died, so I took the hard-drive out, put in different laptop body, and voala - I'm up and running again. Only 2 issues:

1. headphone jack not making any sound. I plug in the headphones and it mutes the speakers, but no sound through headphones. Checked alsamixer, and there is a setting for headphones but no volume bar, just a "headphones" selector.

2. Every time I boot my display is double-wide (approx 2400px display on a 1284px screen) because it is (presumably) acting as if this laptops screen is an added screen. I use the nvidia x-config utility to fix this each time I boot but am unable to save to x-org configurations file for some reason, so this becomes a recurring task every time I start up.

Is there a single solution that might fix both - for instance, a utility I can run to have the xorg configs completely updated and have ubuntu recognize the computers current hardware, something like that?

I'm on karmic on a velocitymicro notemagix - am using alsa instead of pulseaudio

---

### Post by alldaylong on 2010-11-20
Or, if each of these needs to be solved separately, please let me know.

---

### Post by iponeverything on 2010-11-20
Run dpkg-reconfigure for the packages in question.

---

### Post by jocko on 2010-11-20
To be able to save a new xorg.conf from nvidia's configuration tool, you need to give it the proper permissions, so start it with gksudo:
```
gksudo nvidia-settings
```
Or to detect the graphics card and generate a completely new xorg.conf:
```
sudo nvidia-xconfig --force-generate
```

---

### Post by alldaylong on 2010-11-20
ok great - got the nvidia problem solved. Now how do I get the headphones to work? Tried reinstalling alsa, tried installing the backports. It mutes the speakers when I plug the headphones in, just no sound through headphones and no way to turn the volume up in alsamixer.

---

