---
title: "Problem with NVidia GeForce GT 330M"
date: 2010-09-08
forum: Hardware
---

### Post by dakochan on 2010-09-08
Hi,

I'm using Sony Vaio VPCCW26FG (CW Series). It's graphic card is NVidia GeForce GT 330M.
Recently I installed new driver from NVidia 256.53, but looks like this driver is not so stable on my notebook.
Sometimes the NVidia driver is successfully loaded, but sometimes its failed to load.

This is the last few lines of log message from Xorg.0.log:
```
(**) Sep 06 22:25:38 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 06 22:25:38 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 06 22:25:38 NVIDIA(0):     enabled.
(EE) Sep 06 22:25:39 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) Sep 06 22:25:39 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) Sep 06 22:25:39 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) Sep 06 22:25:39 NVIDIA(0):     README for additional information.
(EE) Sep 06 22:25:39 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

If I use lspci I get:
```
$ lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation Device 0a2b (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

```

I don't know what is the problem. Please help... :(

Regards,
DakoChan

---

### Post by ellgor on 2010-09-08
Hi,

I read somewhere that the Nvidia drivers for some reason don't get istalled correctly, I found this guide that gets them installed and working correctly:

1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Hope this helps,

Regards, Ellgor.

---

### Post by dakochan on 2010-09-09
Hi Ellgor,

I've tried your suggestion on my notebook. Let's see in a week or two, how it is going.
Thanks a lot.

Regards,
DakoChan

---

### Post by gaby_loose on 2010-11-20
Hi Dakochan,

I wonder if you've got your nvidia gt 330 M working on your laptop with the suggestions made by Ellgor.

I'd like to buy a vostro 3700 with this graphics card 1G on board for use with ubuntu 10.04, but reading your messages and other info make me hesitating,

thanks,

gaby;)

---

### Post by Icebear on 2010-11-20
Hi 

I got my sony with the NVIDA 330m to work with the information found at 
[http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)

---

### Post by thewooleymammoth on 2010-11-21
i have an acer 5745g, it has the nvidea geforce 330m on it and i got the same error with 10.10, Figured out that in my  bios there was an option to switch my graphics mode from switchable to discreet. After that it works fine. (im dualbooting) and my windows 7 install no longer works in this mode, so i have to switch based on the os i want. But it works. and takes about 2 seconds.

Anyone know what the difference in the modes is? I dont see a real performance drop. Although i suppose i havn't done any benchmark stuff.

---

