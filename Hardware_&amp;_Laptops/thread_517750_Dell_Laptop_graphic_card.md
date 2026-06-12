---
title: "Dell Laptop graphic card"
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by catch2two on 2007-08-04
I just finished installing ubuntu studio on my laptop. It has gone really well i also i have a version working on my desktop.

The laptop is a dell inspiron B120. I was actually suprised how easy it was to set up wireless. I set the resolution using 915resolution which also went well. 

The graphics seem to run slow. Is the driver actually installed? I used ENVY for my desktop which was easy but for this intel chipset i am not sure what to do. 

Any ideas???

---

### Post by hedgefighter on 2007-08-05
Just install the updated intel drivers in the repo. There's no need for 915resolution.

```
sudo apt-get install xserver-xorg-video-intel
```

Or just install it through adept manager.

---

### Post by catch2two on 2007-08-05
I show that as being installed.  Is their someway i can configure it or so shoudl i take out the coe i added for 915resolution?

---

### Post by hedgefighter on 2007-08-05
Are you sure that that's the one installed? There are two packages. xserver-xorg-video-i810 (the default) and xserver-xorg-video-intel (the new one). It should remove the old one when it installs. If they're both installed that may be an issue.

---

### Post by catch2two on 2007-08-05
xserver-xorg-video-i810 is not installed. Just for e.g. sake if i go and play a DVD from my dvd rom it plays plays in jumpy frames. Also when i drag a window across other windows it leaves an image. It did not do this in window just to confirm it is not a ram issue.

---

### Post by hedgefighter on 2007-08-05
What card do you have? You can find out what it is from "lspci" in a terminal. You'll have to search the list of hardware for it. Everything seems to be made by intel so a grep wouldn't help much. My card says "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller". And mine runs super smooth.

---

### Post by catch2two on 2007-08-05
this is what i have mobile 915gm/gms/910gml express graphics controller

---

### Post by hedgefighter on 2007-08-05
Well, I looked around and I didn't see anyone else with a 915GM having the same issues. I don't know what else to try. Anyone else have any ideas?

---

### Post by catch2two on 2007-08-05
Thanks for your help though. It is not a deal breaker i will live with it.

---

