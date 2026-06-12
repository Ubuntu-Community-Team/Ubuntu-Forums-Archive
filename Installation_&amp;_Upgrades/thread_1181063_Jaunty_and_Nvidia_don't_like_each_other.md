---
title: "Jaunty and Nvidia don't like each other"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by dv8NoirFSq on 2009-06-07
well, this is my second request for help, 
I recently upgraded from UbuntuStudio Hardy to Jaunty, and everything was cool until I wanted to install the Nvidia driver (180 -- Listed as recommended in Hardware Drivers), since Alt+Ctrl+Backspace doesn't work I restarted the system... and here comes the error.. so I went to recovery mode, used Xfix and everything back to normal..

everytime I install any Nvidia Driver i reach the same point, the error says that it cannot run X server since Nvidia-kernel-Module version mismatch Nvidia-Driver..

I went to seach more, I find a tutorial where I download the latest package driver from Nvidia Website "NVIDIA-Linux-x86-185.18.14-pkg1.run" , installed Linux-Source via apt-get install linux-source, installed GCC via apt-get install gcc build-essential and followed on what's left in this [webpage]("http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/") , and I got stuck saying it cannot find CC and cannot compile anything...

i'm running frustrated, i tried to manipulate xorg.conf file, added the whole kind of possible things to be added and yet i couldn't do magic..

please please please, instruct me with any possible solution that could help, and i will provide you with anymore information you might need.. 

thanks in advance

---

### Post by stilling on 2009-06-07
have you tried to go to system -> administration -> hardware drivers in gnome and to activate the driver or if you done that . or with envyng to install envy open a terminal and sudo apt-get install envyng-qt after go to applications system tools Envy and install your driver .

Hope this helps you.

---

### Post by dv8NoirFSq on 2009-06-07
I installed Envy as you recommended, and selected to install Nvidia 180.60-0ubuntu2 which is compatible and recommended, but it told me that my headers for kernel are missing and cannot be installed, so I went to terminal and did apt-get install apt-get install linux-headers-2.6.28-3-rt an d all I got is this:

> root@UbuntuStudio: apt-get install linux-headers-2.6.28-3-rt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.28-3-rt is already the newest version.
linux-headers-2.6.28-3-rt set to manually installed.
The following packages were automatically installed and are no longer required:
  fakeroot nvidia-settings mdetect xinput dkms nvidia-180-kernel-source
  nvidia-180-libvdpau
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


although I know that this kernel is the one i'm using, my Grub still tells me that i'm running on hardy's Kernel 2.6.24-24-rt

could this be the problem currently caused by upgrading from hardy to jaunty??

i'm confused

---

### Post by dv8NoirFSq on 2009-06-07
i think there's some progress,
i upgraded my kernel, now using 2.6.28-3-rt, went to Envy and installed the driver, restarted the system, but DKMS installation for nvidia-glx-180 fails, and takes me to core log-in screen (no gdm)
i find that there's no xserver, so i did apt-get install xserver-xorg-video-nv, which uninstalls nvidia-glx-180 :( ...

things are screwed up, but someone recommended to install xserver-xorg-video-nouveau, so i did... 

i will re-install nvidia-glx-180 now, and i hope it do the charm

---

### Post by TrakerJon on 2009-06-07
The new Ubuntu 9.04 Jaunty Jackalope system comes with Nouveau display graphic driver by default and the advanced effects cannot be used with this driver. If you've already tried to enable restricted Ubuntu drivers and Nvidia cannot be found in the list try installing the driver with this tutorial:

1. Run Applications/Add/Remove
2. From the left menu choose System Tools
3. Next from the right menu, find and select for install: Desktop Effects (Compiz Setup) and Nvidia binary X.org Driver version 173 or 177. Selecting the driver will get the list of supported graphics card.
4. Click Apply Changes and after installation go to System/Administration/Hardware Drivers
5. The system will search for available drivers, choose the recommended option from the list and activate the driver by clicking Activate.
6. Restart your system and the new nVidia graphic display driver will be on use.

---

### Post by richardh9936 on 2009-06-08
I also use the Nvidia driver, and I, too, forgot to use ENVYNG to remove the video driver BEFORE upgrading the kernel - again - so I ended up backing up all my own data and doing a complete clean install - again - and then using ENVYNG to install the new driver.  Until I decided on doing the completely new, clean installation, I had lots of issues with X and xorg.conf, and was getting lost in rabbit burrows.  

Next time Ubuntu offers a kernel upgrade, I'll either reject it, or expect to do the complete clean install again.

All this might seem iritating, but it has delivered a much better performing system.

---

### Post by dv8NoirFSq on 2009-06-08
> The new Ubuntu 9.04 Jaunty Jackalope system comes with Nouveau display graphic driver by default and the advanced effects cannot be used with this driver. If you've already tried to enable restricted Ubuntu drivers and Nvidia cannot be found in the list try installing the driver with this tutorial:

1. Run Applications/Add/Remove
2. From the left menu choose System Tools
3. Next from the right menu, find and select for install: Desktop Effects (Compiz Setup) and Nvidia binary X.org Driver version 173 or 177. Selecting the driver will get the list of supported graphics card.
4. Click Apply Changes and after installation go to System/Administration/Hardware Drivers
5. The system will search for available drivers, choose the recommended option from the list and activate the driver by clicking Activate.
6. Restart your system and the new nVidia graphic display driver will be on use.     i did what you said, although it didn't confirm installing the Nvidia Driver 173 (which is the only one i can install) due to DKMS something  that connot install it!!! but i can see that it has a 'tick' on it... when i went to system>administration>hardware drivers, i tried to enable the driver, it didn't, there was no error message shown... it also didn't ask for reboot.

i will try to reboot now, let's see what will happen

---

