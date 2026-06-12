---
title: "nVidia Drivers not loading correctly."
date: 2008-04-25
forum: Hardware
---

### Post by MeanEYE on 2008-04-25
Yesterday I upgraded to 8.04 from 7.10 version of Ubuntu. After upgrade a real nightmare. First of Xgl was not functioning correctly and kept corrupting my displays. I decided then to uninstall Xgl along with nvidia-glx-new drivers. I went to nVidia.com downloaded the latest drivers.

Installed drivers without any problem.

Now the thing is, right after the installation I started X and it worked like it should. But next time I started my system I got the following error:

```
Error: API mismatch: the NVIDIA kernel module has version 71.86.04,
but this NVIDIA driver component has version 169.12.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
Error: API mismatch: the NVIDIA kernel module has version 71.86.04,
but this NVIDIA driver component has version 169.12.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
(EE) NVIDIA(1): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(1):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(1):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(1):     Please consult the NVIDIA README for details.
(EE) NVIDIA(1):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

```

I tried installing the same drivers again. And after installation using the same xorg.conf as last time I was able to start x. After reboot same error again!

I understand what the problem is but don't know how to fix it.

---

### Post by meimato on 2008-04-25
I'm having exactly the same problem.
I've got an EN7900GS, which worked fine in 7.10 (drivers installed through Envy). Before the upgrade I removed the drivers, then I installed them again, but I had no luck: if I install the 169.12 version I get the same error of MeanEYE, if I install the 71.86.04 I get a "could not open device file /dev/nvidia0" error (but the file is in the right place).

---

### Post by MeanEYE on 2008-04-28
For all those who might come on this thread. I just wanted to say I gave up on fixing this thing. Tried everything, even removing the kernel module it self. Didn't help!

Backed up my data and downloading Ubuntu ISO. Nothing like a fresh install :)

---

### Post by oooh on 2010-06-22
well, that is not the smartest of the solutions ...

any other idea ? 

did anybody tried 

update-initramfs -u ?

or 

dkms ?

---

### Post by MeanEYE on 2010-06-22
> **oooh said:**
> well, that is not the smartest of the solutions ...

any other idea ? 

did anybody tried 

update-initramfs -u ?

or 

dkms ?

You do realize this is 2 year old thread?

---

