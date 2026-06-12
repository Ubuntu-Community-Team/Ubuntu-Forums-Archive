---
title: "Problems with Nvidia Drivers"
date: 2015-05-06
forum: Hardware
---

### Post by erik23 on 2015-05-06
Hi guys, i have Ubuntu 15.04 64 bit and i really want to install the driver for my Nvidia GeForce gt 820 m ( i've downloaded the .run file from Nvidia's Website) , but i'm having a lot of problems:

[LIST]
[*]-Initially the installer gaves me problems, it said that i had an x server opened and i had to disable it, i solved by insert the option --no-x-check after the sh command (  for install the driver) 
[*]-Next, the installer said me that there are hte "Nouveau driver" that interferes, and to consult the README int the Nvidia Website ( the readme said to add these strings: 
[/LIST]
blacklist nouveau
options nouveau modeset=0
)
 in a file in /etc/modprobe.d ,i've done it, i've tried also to edit the blacklist.conf file and adding the same strings but nothing was changed.

[LIST]
[*]- Afterwards i've read in the nvidia README that, after the reboot ( you must do it after editing these files) the Nouveau Driver can start at the boot, and to edit the l file initrd for stopped it, with the command 
[/LIST]
```
update-initramfs
```


it created a file in  /boot/initrd.img-3.19.0-16-generic

i've checked this folder and it was this file near another file:  /boot/initrd.img-3.19.0-15-generic
I have no idea what it is, it seems like a "duplicate" (?)
anyway, i mounted the ISO image and i found kernel/x86/microcode/GenuineIntel.bin

What's this file? i can't open it...

[LIST]
[*]Why if i try to open the ctrl+alt+f2 mode the display begins to warp and all begins to look bad ( almost impossible to read) 
[/LIST]

Thanks for reading until here, if you have a solution for install these drivers, please let me know ;) ( Sorry for my bad english, i live in England, but i'm not english :p)

---

### Post by papibe on 2015-05-06
Hi erik23.

I recommend to uninstall the driver from the Nvidia site, and left it as a last resort.

Install the Nvidia driver prepackaged for Ubuntu. Open 'Additional Drivers', and install the driver from there.

Hope it helps, let us know how that goes.
Regards.

---

### Post by erik23 on 2015-05-06
> **papibe said:**
> Hi erik23.

I recommend to uninstall the driver from the Nvidia site, and left it as a last resort.

Install the Nvidia driver prepackaged for Ubuntu. Open 'Additional Drivers', and install the driver from there.

Hope it help, let us know how that goes.
Regards.

Thanks for the help, i just solved by follow this guide [http://ubuntuhandbook.org/index.php/2014/09/nvidia-343-22-install-in-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/09/nvidia-343-22-install-in-ubuntu-1404/), (first method) but with the latest Nvidia software (346.59)

Regards

---

