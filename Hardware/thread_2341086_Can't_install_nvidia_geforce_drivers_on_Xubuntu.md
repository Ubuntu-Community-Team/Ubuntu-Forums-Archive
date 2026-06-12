---
title: "Can't install nvidia geforce drivers on Xubuntu"
date: 2016-10-24
forum: Hardware
---

### Post by mareklucas on 2016-10-24
Hey everyone,
I have some trouble with installing nvidia geforce drivers on my laptop acer aspire 5742g with NVIDIA GeForce GT 540M

This is list with what I do:
1. Type: sudo service mdm stop
2. Change to the directory where I have the '.run' file stored.
3. Type: chmod 755 filename.run 
4. Type: sudo ./filename.run 

I paste you my log:

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Oct 24 16:45:03 2016
installer version: 367.57

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

nvidia-installer command line:
    ./nvidia-installer

Unable to load: nvidia-installer ncurses v6 user interface

Using: nvidia-installer ncurses user interface
-> Detected 4 CPUs online; setting concurrency level to 4.
-> License accepted.
-> Installing NVIDIA driver version 367.57.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Are you sure you want to continue? (Answer: Continue installation)
ERROR: The Nouveau kernel driver is currently in use by your system.  This driver is incompatible with the NVIDIA driver, and must be disabled before proceeding.  Please consult the NVIDIA driver README and your Linux distribution's documentation for details on how to correctly disable the Nouveau kernel driver.
-> For some distributions, Nouveau can be disabled by adding a file in the modprobe configuration directory.  Would you like nvidia-installer to attempt to create this modprobe file for you? (Answer: Yes)
-> One or more modprobe configuration files to disable Nouveau have been written.  For some distributions, this may be sufficient to disable Nouveau; other distributions may require modification of the initial ramdisk.  Please reboot your system and attempt NVIDIA driver installation again.  Note if you later wish to reenable Nouveau, you will need to delete these files: /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

I tried to fix it, but I have no idea how to install this driver and I need it because I can't adjust my brightness

Thanks

---

### Post by ajgreeny on 2016-10-24
Hi mareklucas, and a warm welcome to the forum.

I see this is your first post to the forum so I surmise that you may be a new Linux user and not used to the way in which we install applications and software in Ubuntu or Xubuntu. I doubt that you really need to go through all that palaver to get the nvidia driver for that card, though I have never had an nvidia card to deal with personally.

Go to **Additional Drivers** from the menu and I think that will search for, and find the best driver for you to use for that card which is not a very new card, so will not need, and probably will not work with the latest driver version.

Give that a try and if it is still not successful come back again and users with more experience that I will try to help you more.

---

### Post by Portaro on 2016-10-24
> [COLOR=#000000]ERROR: The Nouveau kernel driver is currently in use by your system. This driver is incompatible with the NVIDIA driver, and must be disabled before proceeding. Please consult the NVIDIA driver README and your Linux distribution's documentation for details on how to correctly disable the Nouveau kernel driver.[/COLOR]
[COLOR=#000000]-> For some distributions, Nouveau can be disabled by adding a file in the modprobe configuration directory. Would you like nvidia-installer to attempt to create this modprobe file for you? (Answer: Yes)[/COLOR]
[COLOR=#000000]-> One or more modprobe configuration files to disable Nouveau have been written. For some distributions, this may be sufficient to disable Nouveau; other distributions may require modification of the initial ramdisk. Please reboot your system and attempt NVIDIA driver installation again. Note if you later wish to reenable Nouveau, you will need to delete these files: /etc/modprobe.d/nvidia-installer-disable-nouveau.conf[/COLOR]
[COLOR=#000000]ERROR: Installation has failed. Please see the file '/var/log/nvidia-installer.log' for details. You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [/COLOR][www.nvidia.com]("http://www.nvidia.com/")[COLOR=#000000].[/COLOR]


I think that you need make this operation in text mode because the problem to install the driver is currently linked to the fact that your system stay use the nouveau and maybe this nouveau need to be unistalled to install the version of drivers that you want to install.

Here you have more info &#8594; [COLOR=#000000]/var/log/nvidia-installer.log 
[/COLOR]If you can put here the log if you have more logs maybe is important to see if the problem is other also , like Kernel version , for example I use nvidia 173 driver version and I need to use a specific version of Kernel to install it on my 14.04 , my version of Kernel is 3.13.0.49 .
In more recent Kernels I cant apply the driver so I need to stay in this version of Kernel.

You can see the process that I use to install my driver to my Nvidia FX 5500 here &#8594; [https://ubuntuforums.org/showthread.php?t=2278549](https://ubuntuforums.org/showthread.php?t=2278549)

So first I think that you need to disable the nouveau and then try to install the driver.

---

### Post by deadflowr on 2016-10-24
*Thread moved to **Hardware**.*

---

### Post by Bucky Ball on 2016-10-24
> **ajgreeny said:**
> Go to **Additional Drivers** from the menu and I think that will search for, and find the best driver for you to use for that card which is not a very new card, so will not need, and probably will not work with the latest driver version.

Give that a try and if it is still not successful come back again and users with more experience that I will try to help you more.

+1. Welcome. Do this before doing anything else and before diving round anymore in a terminal not sure what you're doing (or breaking). You may end up causing more damage you're going to need to work out how to fix later. If the above works you're done in a few minutes with a couple of clicks.

---

### Post by mareklucas on 2016-10-25
Thanks for yours answers, I did like some of you propose- I change to nvidia drivers in Additional Drivers and it works completely fine, now I can change brightness:D

---

### Post by Bucky Ball on 2016-10-25
Great news. Please mark the thread as SOLVED from 'Thread Tools' at the top right of the page or see the last link in my signature at the bottom of this post. This will not close the thread to future discussion.

Likewise, always check your package manager (Synaptic or Software Centre) for apps before installing from a third-party. Better and safer if you can get it from there. Avoiding PPAs where possible is a good idea. Other than the official Canonical ones, they are not supported by Canonical and you use at your own risk. 

Good luck and enjoy. :)

---

