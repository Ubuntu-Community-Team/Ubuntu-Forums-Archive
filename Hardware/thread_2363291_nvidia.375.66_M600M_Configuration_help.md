---
title: "nvidia.375.66 M600M Configuration help"
date: 2017-06-08
forum: Hardware
---

### Post by patric-buskas on 2017-06-08
Hi,

I just bought a Lenovo P70 with Nvidia Quadro M600M
I'm trying to make my double screens work when I connect the laptop to the docking station but they won't work.
When starting the laptop already in the docking station none of the screens will work.
I had it work once with the two "docked" screens and laptop screen at the same time but after I turned off the screens I never got that working again.
This is the behaviour with the "NVIDIA binary driver - version 375.66 from nvidia-375(proprietary, tested)
It's almost the same with the Nouveau driver.
I tried to install the 375.66 driver downloaded from nvidia but it's complaining on the driver already installed.

Please, can anyone help me solve this problem. The setup is working on Windows but I'm not that much masochist.

Thank you!

---

### Post by patric-buskas on 2017-06-08
Hi again,

I think this is going to be more than a question about configuration.
I noticed when reading the file /var/log/Xorg.0.log that it's not using the nvidia-driver as the "Additional Drivers" is telling me.
It's falling back to the Nouveau driver because the nvidia driver can't be found.
Event though I'm reinstalling the nvidia-375 driver it can't be found.
Whats wrong?
How can I install the driver so that xorg will find it?

Thank you!

---

### Post by Autodave on 2017-06-08
Where did / are you getting the driver from?

---

### Post by patric-buskas on 2017-06-08
The nvidia-375 from the ubuntu repository
The Nvidia driver that won't install, NVIDIA-Linux-x86_64-375.66.run, from nvidia.com

---

### Post by Autodave on 2017-06-09
Always use the repository version. You need ti completely uninstall the driver that you got from nvidia.com.

In a terminal run:

sudo apt purge nvidia*

Reboot and then go to the settings and additional drivers. Install the recommended one.

Reboot again and report back.

---

### Post by patric-buskas on 2017-06-11
Thank you very much!
I thought that the uninstall script from Nvidia the took care of the cleaning but obviously not.
The purge and restart did the trick.
All screens are working as intended and no errors in Xorg-log.
Thank you!

---

