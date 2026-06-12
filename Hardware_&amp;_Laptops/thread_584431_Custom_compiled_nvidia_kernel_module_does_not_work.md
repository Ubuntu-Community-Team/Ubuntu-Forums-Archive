---
title: "Custom compiled nvidia kernel module does not work on Gutsy?"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by worc on 2007-10-21
Laptop: TOSHIBA Satellite p105 s9337

Fresh install Gutsy on the laptop. Nvdia driver come from restrict-modules works fine.

For some reason, to fix the DSDT issue if you care, I have to compile a custom kernel. My first try was to compile a kernel version 2.6.23.1. The kernel was compiled smoothly and booted very well. Then I have to  manuly install nvidia driver because there is no restrict-module for kernel 2.6.23.1. But the nvidia kernel module can not be built for some reason. After some google I guess it was caused by the mismatch between nvidia driver and kernel 2.6.23. 
Fine, I switched to kernel 2.6.22.10 (this is the latest of 2.6.22 I can find from kernel.org, how Gutsy get the kernel 2.6.22.14?). Kernel 2.6.22.10 was compiled well and booted OK. Now the nvidia part. 
Nvidia drver version 9755 was built with no error in the new kernel 2.6.22.10, and at the end of the built, where the script asks if I want it to config x for me, I said yes, which just means the xorg.conf will be modified to use nvidia driver I guess. But when I tried to start X, it fails and automaticaly swithed to the "low graphic mode" using vesa driver. /var/log/Xorg.log.0 was also overrided by vesa load info, I don't know where to find info to know what happened to my nvidia module.
Sudo moprobe nvidia fails and says failed to install or something. I followed [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) to uninstall nvidia driver comes from restrict-modules and removed /lib/linux-restricted-modules/.nvidia_new_installed, now sudo modprobe nvidia runs with no error and lsmod | grep nvidia shows the nvidia module was loaded. But I still can not start X with nvidia driver.I mean the xorg.conf was modified to use nvidia driver, and /etc/init.d/gdm start just lead me to the "low graphic mode". I can not find any info to show what happened to the already loaded nvidia module!

Can someone help me out on this?

---

### Post by worc on 2007-10-21
Come on, no one compile nvidia driver on custom kernels?

---

### Post by LanDan on 2007-10-21
can you post your xorg.conf?

---

### Post by TheCursor on 2007-10-22
I'd like to verify that this is indeed a problem. I have to have a custom kernel (otherwise sound will not work). The NVIDIA driver doesn't work (always taken to the low-graphics-mode screen upon gdm restart after installing the driver). The problem IS NOT the xorg.conf file, as it has been modified correctly by the NVIDIA installer.

The error gotten upon 'sudo modprobe nvidia' is:

FATAL: Error running install command for nvidia

Any ideas?

---

### Post by nick_h on 2007-10-23
Did you modify the DISABLED_MODULES line in /etc/default/linux-restricted-modules-common as well as removing /lib/linux-restricted-modules/.nvidia_new_installed ?

What version of the driver is loaded in /var/log/Xorg.0.log ?

---

### Post by worc on 2007-10-25
Don't know why, but it seems NVIDIA driver version 100.14.19 works just fine in this case.

When I download driver from NVIDIA, it leads me to version 9755 for a Geforce Go 7900GS card, while version 100.14.19 is for Quadro FX card. 

Somehow, when I tried to install driver version 100.14.19 for my 7900GS card (9755 can be built but can not be loaded), it looks nothing wrong to me. After reboot, the driver was loaded with no error! And what is interesting is that, glxgears gives me a core around 17000 with version 100.14.19, which is used to be around 13000 with 9755. Fun?

Now I'm stick with ersion 100.14.19. Although desktop effects seems a little more buggy than with 9755, but it's not a big issue to me.  

Can anyone tell what is the difference between 100.14.19 and 9755? Is 100.14.19 "safe" to be used on 7900GS?

Another issue I'd like to point out here is, the custom built kernel does get the sound back for me as expected and the suspend works ok too, but the temperature of GPU is still very high (fan is not running). This is not true with Ubuntu 7.04. The custom kernel was built to solve the DSDT issue of my laptop, and successfully solved the acpi problem (sound/suspend all works, and GPU stay cool) in Feisty. So, I guess something changed in Gutsy, which leads to all these problem.

For now, I have to append "acpi=off" to the kernel boot option to keep the GPU cool, that means I have to sacrifice acpi feature like suspend. What else can I do?

---

