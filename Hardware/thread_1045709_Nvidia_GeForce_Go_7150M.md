---
title: "Nvidia GeForce Go 7150M"
date: 2009-01-20
forum: Hardware
---

### Post by gordanr on 2009-01-20
Please can anyone help me.

I am new to Ubuntu and Linux, I have installed Ubuntu latest version on my Laptop. It's fine, but have trouble with my graphic card. I don't know where to find this driver or how to install it at all. I am using:

HP dv2000 AMD Turion64 x2 processor, 3 GB RAM, 250 Gb HDD, and the problem is with : Nvidia GeForce Go 7150M driver..

Please help. 
Thank you All.

---

### Post by taurus on 2009-01-20
Look in System -> Administration -> Hardware Drivers to see if your graphic card is on the list and whether there is a driver (recommended) for it.

---

### Post by gordanr on 2009-01-20
I have checked, and this is what tells me: NVIDIA Accelerated graphic driver (version 173)

Now I click button Activate, and nothing happens.

What to do??

---

### Post by taurus on 2009-01-20
It doesn't download and install nvidia driver for your card?  Do you see an icon on the upper right corner (blue arrows) asking you to reboot?

---

### Post by Tim Drallmeier on 2009-01-29
I have the same problem with my laptop, it has the same card, I recently installed 8.1 on it and now the only resolution i can get is 800x600. My laptop is a DV2845SE, and for the plugins, only one works, for the wireless network, there are two plugins for the Nvidia card, and neither works, it loads for a while, and then quits, and does not enable the driver... I have the option to install NVIDIA advanced graphics driver 173, or 177, and 177 is the recommended... when i go to activate driver, it says downloading and installing driver, shows 0% and does nothing

---

### Post by warlog on 2009-02-10
I have compaq v6608au laptop with same graphic card. I know how to install the driver. First get it from [COLOR="Red"]http://us.download.nvidia.com/XFree86/Linux-x86/180.22/NVIDIA-Linux-x86-180.22-pkg1.run[/COLOR]. 
Now for installing this driver you need to boot in _recovery mode_ from the boot loader. In recovery mode the system will leave u in text mode. There you can install it with the following command:

**sudo sh NVIDIA-Linux-x86-180.22-pkg1.run**

I am assuming that the driver file is in the _present working directory_.
After this follow the on screen instructions. after completion restart your PC in normal mode.
[B]
_The real problem begins now._[/B] 
After booting you will be promted for your login details with perfect graphic resolution. 
But in my laptop after giving username and password my screen goes off. For this problem I am unable to find any solution. If anyone can solve it then please post it here.

---

