---
title: "Issue with nvidia drivers + 8800GTX on Kubuntu Feisty Fawn"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by CoreInsanity on 2007-07-10
Alright, first off I will explain what I have done:

Here are the steps I took to install the drivers:
1) updated the fresh install of Kubuntu
2) installed the build-essentials
3) Proceeded to download the drivers (nvidia.com -> driver downloads -> (In the 3 boxes) Graphics Drivers -> GeForce 8 Series -> Linux x86).
4) Proceeded to install the drivers using this process: 
> 
hold ctrl+alt+f1
 sudo invoke-rc.d kdm stop
 cd ~ (Where I downloaded the drivers to)
 sudo chmod 777 (Driver file name)
 sudo ./(Driver file name)

5) ran "startx" (I am not sure if I should be starting the kdm again? mate told me to do startx, and he knows more linux than me so I did it)

Now, this worked fine... I could configure the Nvidia X Server Settings, run it at 1680x1050 (My LCD Monitors recommended / native res), and save the xorg.conf file. However, some things were still odd. In K -> System Settings -> Monitor & Display -> Hardware, the card shows as following:

> 
Graphics Card: VESA driver(generic)
Driver: vesa


Also, whenever I start the comp and boot Kubuntu, I get taken to a blank screen with a blinking underscore in the top left. From there I have tried:
> Doing startx, it outputs a log file supposedly (I can locate it and post it, if its needed)
> Stopping the kdm, and restarting it and then doing startx, still get an error.
> doing sudo nvidia-xconfig to redo the xorg.conf file

However, nothing seams to let me get back into the desktop except reinstalling the graphics driver like I did above (Just without everything before the chmod) and then doing startx when its done.

Does anyone have any idea how I can go about fixing this? It is highly annoying lol.

I am using the following:
> 
Driver Version: 100.14.11 from nvidia.com


via: [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

My Hardware is:
> 
Intel Core 2 Duo E6600 (2.4Ghz, non-OCed)
XFX 8800GTX
2GB Corsair XMS2 DDR2 dual channel ram
P5N32 - SLI SE Deluxe motherboard


Thanks.

---

