---
title: "nVidia 9500GT Driver Install/Fix"
date: 2009-01-19
forum: Hardware
---

### Post by mrfr0g on 2009-01-19
I know this topic has been talked to death, but, I wanted to post my experience with installing Ubuntu, with the nVidia driver's, and getting them working.

Let me preface this by saying, that this fix may not work for any other version of nVidia graphics cards, but it has worked for me, on two separate computers.

After some exhaustive research, I have found that the only way for me to get the drivers working for these cards, is to start by installing Ubuntu 8.04, and using the envyng application to install the drivers. Each time I've attempted to use the default restricted driver manager drivers, it has failed to reload xserver. Specifically, after enabling the drivers, I restart, and come back to the terminal screen. When attempting to manually restart x, (/etc/X11/X), it tells me that no screens could be found.

Step 1: Install Ubuntu 8.04
Step 2: Go to System->Administration->Synapic Package Manager
      : Search for, "build-essential" and mark it to install.
      : Search for, "kernel-package" and mark it to install
      : Search for, "envyng-gtk" and mark it to install
      : Click apply.
Step 2(ALT):Open a terminal window
      : Type, sudo apt-get install build-essential kernel-package envyng-gtk
Step 3: Open a terminal window
      : Type, sudo envyng -t
      : Select option, 5, "Install the ATI/NVIDIA driver manually"
      : Select option, 2, "NVIDIA"
      : Select option, 1, "173.x.x (latest)
      : It will ask you to restart, press y, or just press enter.

That's pretty much it. After Step 3, it should be working correctly, or at least it has for me. 

Here is a link to another post which has a few solutions,
[http://ubuntuforums.org/showthread.php?t=965180](http://ubuntuforums.org/showthread.php?t=965180)

The community nVidia page,
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

And the envyng page,
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Best of luck

---

