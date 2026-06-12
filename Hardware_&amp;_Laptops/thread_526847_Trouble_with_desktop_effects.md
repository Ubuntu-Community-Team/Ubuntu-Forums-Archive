---
title: "Trouble with desktop effects"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by fulio on 2007-08-16
Hi guys i have NVIDIA GeForce Go 6150 graphics card on my laptop.
WEll i have installed ubuntu correctyl runs good. and now when i enable the effects i had to reboot the laptop for the effects to take place. while the ubuntu boots up it goes to a black screen and freezes there. can anyone help me with this? before i did the desktop effect i tryd to install Compiz fusion and none of th effects worked. i had to go to driver restrict which made me enable it and i had to reboot and i did. when ubuntu was loading agn it freezes into a black screen. any help please?

---

### Post by overdrank on 2007-08-16
> **fulio said:**
> Hi guys i have NVIDIA GeForce Go 6150 graphics card on my laptop.
WEll i have installed ubuntu correctyl runs good. and now when i enable the effects i had to reboot the laptop for the effects to take place. while the ubuntu boots up it goes to a black screen and freezes there. can anyone help me with this? before i did the desktop effect i tryd to install Compiz fusion and none of th effects worked. i had to go to driver restrict which made me enable it and i had to reboot and i did. when ubuntu was loading agn it freezes into a black screen. any help please?

Hi if you are able to get to the desktop you may try and use the script envy
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Hopefully this will enable you to use the graphics and window manager you would like to. 
If you are not able to return to your desktop then when you see the grub load use the ctrl, alt, F1 keys all at the same time and this will bring you to the terminal. Then you can use the command
```
sudo apt-get remove compiz compizconfig-settings-manager
```
To remove compiz and then restart your system
```
sudo shutdown -r now
```
Then you may try the envy script mention above. Good luck!

---

### Post by fulio on 2007-08-18
i have all ready done the envy. and when i reboot i stilll get the failed to start x server.
and i have to boot agn and i ahve to run on vesa..

 this was the error --->


(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): The interrupt for NVIDIA graphics device PCI:0:5:0 appears to
(EE) NVIDIA(0):     be edge-triggered.  Please see Chapter 8: Common Problems
(EE) NVIDIA(0):     in the README for additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

