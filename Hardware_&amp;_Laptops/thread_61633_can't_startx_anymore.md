---
title: "can't startx anymore"
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by darkrad on 2005-09-01
hello, i had the nvidia drivers installed with apt-get install nvidia-glx. then i tried to install the ones on nvidia.com. Doing so i uninstalled all nvidia* entries from Kynoptics. then i closed X with ctrl-alt-backspace and tried to install the nvidia.com drivers. Installation was succesfull: it created a nvidia kernel module and so on.. after it i rebooted and tried to "startx", nothing happened. so i "nvidia-installer --uninstall" it and did again "apt-get install nvidia-glx" etc..
Now when i try to "startx" i get:

```

Error: API mismatch: the NVIDIA kernel module is version 1.0.7676, but this X module is version 1.0.7174. Please be sure that your kernel module and all NVIDIA driver files have the same driver version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error: no screens found

```

anybody have any clue on what to do now?  ](*,) 
thanks

---

### Post by lol on 2005-09-01
try this first : apt-get install --reinstall linux-restricted-modules-2.6.12-8-k7

of course, you have to change the name "linux-restricted-modules-2.6.12-8-k7" to match your running kernel...

---

