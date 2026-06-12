---
title: "NVIDIA graphics driver gone"
date: 2020-06-27
forum: Hardware
---

### Post by claus on 2020-06-27
Hi all,

today, all-of-a-sudden and for no apparent reason I realized that gThumb wasn't starting anymore. After that, Blender didin' start as well, and the shell gave me the following error message:
```

Read prefs: /home/claus/.config/blender/2.82/config/userpref.blend
Error! Unsupported graphics card or driver.
A graphics card and driver with support for OpenGL 3.3 or higher is required.
The program will now close.

```
Yesterday, everything worked without a problem. I have an NVIDIA GeForce GT 710 installed, and until today, everything worked fine. In the Control Center, the NVIDIA Settings are present, but I didn't change anything. Did someone experience a similar problem & knows a solution?

TIA,

Claus

---

### Post by CelticWarrior on 2020-06-27
Please check the drivers are installed and reinstall if needed. Also make sure Secure Boot, if applicable, is disabled.

---

### Post by claus on 2020-06-27
After I logged out & opened a virtual shell, I tried to install the NVIDIA driver anew, but I got the error message saying that an xserver was running. When I performed 'reboot', the issue was gone & everything worked fine. :-)

Claus

---

### Post by CelticWarrior on 2020-06-27
The situation resolved itself, that's nice.

That said, the likely cause of such issues is installing the drivers using the Nvidia binaries. NEVER do that. ALWAYS install the correct drivers from the Ubuntu official repositories.

---

### Post by claus on 2020-06-27
> **CelticWarrior said:**
> The situation resolved itself, that's nice.

That said, the likely cause of such issues is installing the drivers using the Nvidia binaries. NEVER do that. ALWAYS install the correct drivers from the Ubuntu official repositories.

I did install the NVIDIA binaries, and so far, everything worked fine. I checked with Synaptic, and there are in fact several NVIDIA packages installed. Is this suffícient? And how do I uninstall the NVIDIA binaries?

Claus

P. S.: When taking a look at 'Software & Updates > Additional Drivers', I found that 'nvidia-driver-440' is installed & I am told that my NVIDIA GeForce GT 710 is using the recommended driver.

---

### Post by CelticWarrior on 2020-06-27
To uninstall those run the same command with the argument to uninstall.
The main problem with installing that way is that you need to reinstall each and every time there's a kernel update. 
Once uninstalled completely you can simply open Additional Drivers, select and apply the recommended driver version.

---

### Post by claus on 2020-06-27
Hi,

and thanks for your recommendation. When I executed 'sudo sh NVIDIA-Linux-x86_64-340.107.run -uninstall', I got

[sudo] password for claus: 
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 340.107..................................................................................................................................................................................................................................

and a window informing me that 'currently there is no NVIDIA driver installed'. Hm, so it seems that I only have the Ubuntu driver installed.

Claus

P. S.: Are the 'NVIDIA X Server Settings' I can find under 'Administration' in the Ubuntu Menu the options to adjust the Ubuntu driver 440?

[IMG]https://res.cloudinary.com/dxaodmaf4/image/upload/v1593280899/Screenshot_at_2020-06-27_20-00-38_if6jcv.png[/IMG]

---

