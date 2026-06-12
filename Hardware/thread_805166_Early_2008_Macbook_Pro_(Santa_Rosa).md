---
title: "Early 2008 Macbook Pro (Santa Rosa)"
date: 2008-05-23
forum: Hardware
---

### Post by lat2005 on 2008-05-23
I've installed ubuntu 7.10 on the machine and most is running fine.
I got wireless through ndiswrapper.

My machine is very new, with the broadcom wireless.

However, I can't get several things going:

1) I'm worried about heat, and I can't find applesmc.
sudo apt-get install applesmc
finds nothing. I know this is needed for the fans.
I was however able to enable all those sensors to tell me the temperature in the upper bar, although sometimes they give an error,
I'd like to control the fans and be able to monitor the temperature.

2) Is is ok to upgrade to Ubuntu 8.04? Will that help?

3) My function key doesn't work and I can't control the contrast of the screen or anything else. If I do that the F1 or whichever key I press is activated.

4) For some reason my mac came with a strange MAC address( I was told it's not IEEE compatible although it has the correct 12 characters format) which I had to change in windows in order for it to work. Has this happened to anyone else?

5) Is there any way to avoid using ndiswrapper? I would like to be able to use aircrack-ng and those tools.

6) My screen resolution settings are strange. They show up at 1440*900 but at 0 Hz. When I try to change to a lower resolution because the resolution I see currently seems to be about 800*600 or a little more but not 1440*900, it shows larger icons but most of the screen is cut off.
My screen always worked automatically. Do I need to install any NVIDIA drivers?

Thank you.

---

### Post by hotweiss on 2008-05-23
> **lat2005 said:**
> I've installed ubuntu 7.10 on the machine and most is running fine.
I got wireless through ndiswrapper.

My machine is very new, with the broadcom wireless.

However, I can't get several things going:

1) I'm worried about heat, and I can't find applesmc.
sudo apt-get install applesmc
finds nothing. I know this is needed for the fans.
I was however able to enable all those sensors to tell me the temperature in the upper bar, although sometimes they give an error,
I'd like to control the fans and be able to monitor the temperature.

2) Is is ok to upgrade to Ubuntu 8.04? Will that help?

3) My function key doesn't work and I can't control the contrast of the screen or anything else. If I do that the F1 or whichever key I press is activated.

4) For some reason my mac came with a strange MAC address( I was told it's not IEEE compatible although it has the correct 12 characters format) which I had to change in windows in order for it to work. Has this happened to anyone else?

5) Is there any way to avoid using ndiswrapper? I would like to be able to use aircrack-ng and those tools.

6) My screen resolution settings are strange. They show up at 1440*900 but at 0 Hz. When I try to change to a lower resolution because the resolution I see currently seems to be about 800*600 or a little more but not 1440*900, it shows larger icons but most of the screen is cut off.
My screen always worked automatically. Do I need to install any NVIDIA drivers?

Thank you.

First of all, I would try Hardy Heron 8.04 before proceeding any further.

The only thing that I can help you with is the Nvidia drivers:

A) First we’ll need to update Ubuntu’s repositories by typing the following in Terminal:
> sudo apt-get update

B) Now we’ll need to install Envy by typing the following in Terminal:
> sudo apt-get install envyng-gtk

C) Next we’ll need to execute Envy by typing the following in Terminal:
> sudo envyng -g

D) Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 169.12, and finally click Apply.

E) Once the installation is completed, reboot and you will once again have a crisp screen.

---

### Post by lat2005 on 2008-05-23
Thanks. 
I got 8.04 and the driver seems to have helped a lot. I enabled the restricted driver for the NVIDIA and it is working fine now.

---

### Post by ditsch on 2008-05-23
> **lat2005 said:**
> I've installed ubuntu 7.10 on the machine and most is running fine.
I got wireless through ndiswrapper.

My machine is very new, with the broadcom wireless.

However, I can't get several things going:

1) I'm worried about heat, and I can't find applesmc.
sudo apt-get install applesmc
finds nothing. I know this is needed for the fans.
I was however able to enable all those sensors to tell me the temperature in the upper bar, although sometimes they give an error,
I'd like to control the fans and be able to monitor the temperature.
The module is already in the kernel, but not loaded by default. Just insert applesmc into your /etc/modules to have it enabled on system startup.
> **lat2005 said:**
> 
3) My function key doesn't work and I can't control the contrast of the screen or anything else. If I do that the F1 or whichever key I press is activated.
Switch the fnmode to fnmode=2 in your /etc/pommed.conf.
> **lat2005 said:**
> 
5) Is there any way to avoid using ndiswrapper? I would like to be able to use aircrack-ng and those tools.
Do you have a Broadcom Airport or an Atheros Airport? ```
lspci | grep -i net
```

---

### Post by lat2005 on 2008-05-23
Ok. Got applesmc in the file and even did sudo modprobe applesmc.


I tried changing the pommed.conf back to 2, but still no change. Whether I press 
Fn or not, F1 and the rest are at work, not the regular mac keys.

My wireless is Broadcom. If it was atheros of course madwifi would be working with that. Any options for broadcom?

---

