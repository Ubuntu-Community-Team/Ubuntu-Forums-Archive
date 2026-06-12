---
title: "[SOLVED] Kernel Update Problem"
date: 2008-10-22
forum: General Help
---

### Post by dethredic on 2008-10-22
So, I have been using a custom kernel for a while, but I ran into some slight problems, and I really didn't notice any performance increase, so I figure I will just go back the the generic kernels.

Earlier this week, one came up in the Update manager, so I installed it, but when I boot into it there is some problem and I am taken into low graphics mode or something like that. I don't remember exactly, but I am pretty sure I couldn't get past that screen.

Is there anything I can do to fix this? I can still boot up into my custom kernel.

---

### Post by cariboo on 2008-10-22
You more than likely have to reinstall your video drivers. Go to System-->Administration--Hardware Drivers and follow the prompts.

Jim

---

### Post by dethredic on 2008-10-23
I am unable to login. Is there a command I can run from the recovery coommand line?

---

### Post by macabro22 on 2008-10-23
> **dethredic said:**
> I am unable to login. Is there a command I can run from the recovery coommand line?

Go into recovery mode, plug in your cable,

This will get your internet connection going (assuming your etherned card is eth0):

```
sudo ifconfig eth0 up
``` and ```
sudo dhclient eth0
```

This will get a little application that install the latest nvidia drivers (in case you have an nvidia or ati video device):
 ```
sudo apt-get install envyng
```

run it in text mode and follow the instructions on-screen:
```
sudo envyng -t
```

Hope that helps.

---

### Post by dethredic on 2008-10-23
> **macabro22 said:**
> Go into recovery mode, plug in your cable,

This will get your internet connection going:

```
sudo ifconfig eth0 up
``` and ```
sudo dhclient eth0
```

This will get a little application that install the latest nvidia drivers (in case you have an nvidia or ati video device):
 ```
sudo apt-get install envyng
```

run it in text mode and follow the instructions on-screen:
```
sudo envyng -t
```

Hope that helps.

Well, I already have envyng installed, so I will just skip to the last step.

---

