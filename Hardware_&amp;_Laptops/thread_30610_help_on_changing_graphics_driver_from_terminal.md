---
title: "help on changing graphics driver from terminal"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by GazaM on 2005-04-29
I managed to get the LiveCD working by using the VESA drivers and VGA output (on my ATI x700Pro) and I loved it, so I decided to install the full thing on an extra SATA hardrive I had. I done that and I didn't get any options during the installation to configure my graphics options (besides telling xorg what resolutions to use) and now whenever I startup I'm just left at a non-graphical shell telling me that xorg failed to start. This is exactly what was happening with the LiveCD, but I don't know how to change the driver xorg uses from the shell as I'm completely new to Linux. I've tried typing 'sudo gedit /etc/X11/xorg.conf' but it just tells me that it can't open GTK+! How can I fix this problem?

---

### Post by shakin on 2005-04-29
[QUOTE=GazaM]I managed to get the LiveCD working by using the VESA drivers and VGA output (on my ATI x700Pro) and I loved it, so I decided to install the full thing on an extra SATA hardrive I had. I done that and I didn't get any options during the installation to configure my graphics options (besides telling xorg what resolutions to use) and now whenever I startup I'm just left at a non-graphical shell telling me that xorg failed to start. This is exactly what was happening with the LiveCD, but I don't know how to change the driver xorg uses from the shell as I'm completely new to Linux. I've tried typing 'sudo gedit /etc/X11/xorg.conf' but it just tells me that it can't open GTK+! How can I fix this problem?[/QUOTE]

```

$ sudo nano /etc/X11/xorg.conf

```

Now find the device section for your video card and change the driver to vesa

OR

Follow the instructions at [http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557) to install ATI's driver. Whenever that tutorial asks you to run gedit, use nano instead.

---

### Post by GazaM on 2005-04-29
Thanks, that allowed me to edit my xorg config, but when I changed it to vesa I just got a black screen at boot and I wasn't able to do anything, now I'm reinstalling Ubuntu for the 5th time in 1 day! For a first time Linux user this hasn't turned out to be a great experience. I'm beginning to doubt if I'll ever get it to work for my PC.

---

### Post by nad on 2005-04-29
I'm sorry that you are having problems. I admire your persistence and agree that it shouldn't be this difficult, but, automatically configuring for every possible permutation of hardware will always be less than perfect.

If you able to get to the shell prompt, you may find your specific error with the commands: tail var/log/Xorg.0.log  or  tail /var/log/gdm/:0.log  or  tail ~/.xsession-errors  or  dmesg | tail .

If you would post any obvious noted problem we may begin to help. Some system information would be useful also. The output of the command: lspci  will give a description of your computer hardware.

---

### Post by GazaM on 2005-04-30
[QUOTE=nad]I'm sorry that you are having problems. I admire your persistence and agree that it shouldn't be this difficult, but, automatically configuring for every possible permutation of hardware will always be less than perfect.

If you able to get to the shell prompt, you may find your specific error with the commands: tail var/log/Xorg.0.log  or  tail /var/log/gdm/:0.log  or  tail ~/.xsession-errors  or  dmesg | tail .

If you would post any obvious noted problem we may begin to help. Some system information would be useful also. The output of the command: lspci  will give a description of your computer hardware.[/QUOTE]
 Thanks nad, I'll try those commands later as last night after the fifth time trying to get Ubuntu to work I tried Kubuntu, had no luck and then tried Fedora Core 3 which won't even detect that I have a video card at all! I know that my hardware is relatively new but it just seems that my specific hardware isn't very well suited to any form of Linux. I have an ATI X700Pro PCI-Express, MSI K8N Platinum nForce4 motherboard, 1gig RAM and a 19" BenQ LCD. Funnily enough at the Fedora Core install when it failed to recognize a video card for the graphical installer it actually perfectly detected my monitor (BenQ FP937s) which should be impossible if doesn't see a video card as the thing is connected through the video card!

---

### Post by GazaM on 2005-04-30
OK, I haven't got around to wiping the hard drive and reinstalling ubuntu yet, but I have been doing a bit more reading on forums and the such and someone on this forum said that they think the Open Source ATI driver with ubuntu doesn't work with the PCI-Express variants and that people with them should download and install the ATI Proprietry linux drivers. Thing is I haven't got an internet connection on this PC in linux as I use a wireless card which can't be set up during install so I'll have to get them on Windows and burn them to a CD and install them from that in the shell, but I'm a total newbie and haven't got a clue how to do this using commands etc. so if someone could link to a guide or even guide me through it in a post or using the IM links to the left if I'm online, preferebly MSN).

---

### Post by GazaM on 2005-05-01
Finally I got it to work!!! I re-installed the 32-bit Ubuntu and got to the shell as the xorg failed again, then I typed 'sudo dpkg-reconfigure xserver-xorg' and changed the settings to vesa etc. and rebooted to a lovely graphical login! I so think that the xorg configure tool should come up at installation though.

---

