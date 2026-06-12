---
title: "Drivers in Ubuntu 8.10 of a GeForce 8400GS"
date: 2009-03-08
forum: Hardware
---

### Post by Dazark on 2009-03-08
Well, I ask for help because I have this video card is an nVidia GeForce 8400GS and install the program to get the envy drivers without problem but not installed, it is what I think, because when you open System-Administration - NVIDIA X Server Settings, I receive the following error "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run` nvidia-xconfig `as root) and restart the X server." so I'm going to console and type "nvidia-xconfig" and I get the following message:

"Using X configuration file:" / etc/X11/xorg.conf ".

WARNING: Not specified Layout, Constructing implicit screen layout using section
          "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
          CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
          using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
          CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
          using the first keyboard device.


ERROR: Unable to write to directory '/ etc/X11'. "

	
now is not what to do, and I also have a dual display only when connected to another monitor and ubuntu started, I did not show the log in page and it's like to be frozen, and he left around 15 minutes but still frozen.

I hope you can help
thanks

---

### Post by balaknair on 2009-03-09
Try running nvidia-xconfig as root, type *sudo nvidia-xconfig*

---

