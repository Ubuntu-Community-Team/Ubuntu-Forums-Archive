---
title: "Nvidia &quot;No screens found&quot;"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by JMO707 on 2007-04-24
I've tried with: 

- purge & install *nvidia-glx nvidia-glx-new nvidia-glx-legacy* in various combinations.
- [Envy]("http://albertomilone.com/nvidia_scripts1.html"), from Alberto Milone's
- [Automatix]("http://www.getautomatix.com/").
- Doing what is told by Eigenwert in [this thread]("http://ubuntuforums.org/showthread.php?t=363466&highlight=nvidia+no+screen+found").

Everything started when, for curiosity, I installed the nvidia-glx-new with Synaptic. Just that.

Now, I can't make the *nvidia* driver work at all. I use *nv* with my ol' Geforce4 MX440.

It say's something like:

```
FATAL: Error running install command for nvidia
(EE) NVIDIA (0): Failed to load NVIDIA kernel module!
(EE) NVIDIA (0): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
        after 0 requests (0 known processed) with 0 events remaining
```

:confused:

---

### Post by hanzomon4 on 2007-04-24
Did you install the restricted modules for your kernel version? Do this:```
sudo apt-get install linux-restricted-modules-generic
``` I'm assuming that you use the generic kernel and not a i686, K7, yada yada

---

### Post by JMO707 on 2007-04-24
It hangs as before, but now says something like "the *nvidia.ko *file is missing".

Edit:

```
FATAL: Could not open '/lib/modules/2.6.20-15-generic/kernel/drivers/video/nvidia.ko': No such file or directory
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.
```

---

### Post by JMO707 on 2007-04-24
mmm, this is getting worse. Now it doesnt even detect the card via the restricted modules tool, and the best resolution I can get is 800x600.

Plus, my language changed in the session from italian to spanish (¿?)

---

### Post by JMO707 on 2007-04-24
Thanks to [this guide]("http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/") now its solved ^^

(Phew...)

---

