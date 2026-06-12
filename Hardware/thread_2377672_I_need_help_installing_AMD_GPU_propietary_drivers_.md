---
title: "I need help installing AMD GPU propietary drivers on UBUNTU 17.10"
date: 2017-11-15
forum: Hardware
---

### Post by thelocust2 on 2017-11-15
I currently have a Sapphire Dual X AMD R9 280x and I'm trying to  install the official drivers from AMD website but I keep getting a black  screen when I reboot. Does anyone have any specific instructions on how  to do this successfully? Any help would be appreciated.

---

### Post by QIII on 2017-11-15
Hello!

Which "official driver" are you trying to install?

---

### Post by thelocust2 on 2017-11-15
I guess the latest that works, it does not matter as long as it works.

---

### Post by QIII on 2017-11-15
Which did you try to install?

---

### Post by QIII on 2017-11-15
With the R9 280X, you will not be able to successfully install AMDGPU or AMDGPU-PRO.  It is a Graphics Core Next (GCN) 1.0 unit.  AMDGPU currently works only with GCN 1.1 and later GPUs, except for a few GCN 1.0 cards supported by updates.

At install time, Ubuntu checks to see if there is an AMD GPU present, and if so whether it is supported by the open source AMDGPU driver.  If so, AMDGPU is installed by default.  If not, the open source Radeon driver is used.  In your case, Radeon would have been installed.

Since AMDGPU-PRO (the proprietary overlay to AMDGPU) requires that AMDGPU exists, AMDGPU-PRO cannot be installed.

You will need to uninstall AMDGPU (or PRO, or both, whichever you have attempted to install -- which is why I asked) and use the default Radeon driver.

---

### Post by thelocust2 on 2017-11-15
This is the one I tried to install: [https://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064](https://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064)

---

### Post by QIII on 2017-11-15
OK.  Did you notice the Ubuntu versions and the hardware supported?

---

### Post by thelocust2 on 2017-11-15
I also tried this one: [https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx](https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx)

---

### Post by QIII on 2017-11-15
OK.  As I said,  AMDGPU (and therefore AMDGPU-PRO) does not support your hardware.  

You'll need to follow AMD's instructions for un-installation.

---

### Post by thelocust2 on 2017-11-15
So there's no possible way whatsoever to get any AMD proprietary drivers to work on Ubuntu 17.10 for R9 280x cards?

---

### Post by QIII on 2017-11-15
If you are interested in trying an experimental version, you may try what Phoronix describes here:  [https://www.phoronix.com/scan.php?page=article&item=amdgpu-radeon-414&num=1](https://www.phoronix.com/scan.php?page=article&item=amdgpu-radeon-414&num=1)

However, this adds a PPA and requires some fiddling.  You could render your machine inoperable.  It is, after all, experimental.  Support is coming for GCN 1.0 eventually, but it's not just a matter of downloading and installing yet.

Personally, I'd just roll with Radeon right now.

---

### Post by thelocust2 on 2017-11-15
Thanks, I really don't care if I have to reinstall the OS. Do you know where can I find like a step by step guide on how to get this done?

---

### Post by Yellow Pasque on 2017-11-16
> Personally, I'd just roll with Radeon right now. 

Yeah, that. Switching to amdgpu gets you a few more FPS in certain games, but you lose video decode acceleration, at least until 4.15 kernel comes out (assuming Linus accepts the code) 
radeon's had much more testing/use.

---

