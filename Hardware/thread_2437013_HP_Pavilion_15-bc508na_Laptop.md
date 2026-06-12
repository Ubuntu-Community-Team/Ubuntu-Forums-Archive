---
title: "HP Pavilion 15-bc508na Laptop"
date: 2020-02-17
forum: Hardware
---

### Post by dbee on 2020-02-17
Thinking about buying this laptop. Want to know whether there'll be any compatibility issues with the latest version of LTS Ubuntu? 

HP Pavilion 15-bc508na 15.6 Inch FHD Gaming Laptop, Intel Core i5-9300H, 8 GB RAM, 512 GB SSD, NVIDIA GeForce GTX 1050 (3 GB Dedicated) Graphics, Windows 10 Home - Black

I want to work with video editing program lightworkso to edit short web videos ...


Does anyone have any experience of this ?

Thanks in advance

---

### Post by CelticWarrior on 2020-02-17
No compatibility issues are expected.

Worst case scenario the WiFi card will need drivers. The graphics should run also with Nvidia proprietary drivers already available in the Ubuntu repositories. If using a new release this drivers as well as most drivers for WiFi can be automatically installed if the option for third-party stuff is enabled during the installation.

---

### Post by dbee on 2020-02-17
Thanks Celtic warrior.

---

### Post by dbee on 2020-02-21
Ok got the new computer. 

Booting Ubuntu Live LTS 18.4.04 - the latest LTS version of ubuntu.

Computer keeps crashing. All i see as it winds down is 
> 
Noveau .... something .... fffffffffff

or something like that. 

Does Ubuntu Live keep logs ? I can post more info if it does.

I guess it could be a driver issue. Maybe if i do an install and enable 3rd party drivers that'll fix it ?

Should i go ahead and install ubuntu anyway ?

Thanks

---

### Post by CelticWarrior on 2020-02-21
You need to add a boot parameter - nomodeset -: When at the Grub menu, with the "Try Ubuntu" option highlighted, press 'e' to edit and then add 'nomodeset' (without the quotation marks) to the same line starting by "quiet splash". It doesn't matter where in that line but make sure there are spaces between the words. This will give you a generic and probably low resolution graphical environment that allows installation without freezes. Do the same before the first boot after installation and then open Additional Drivers, select and install the recommended NVIDIA driver version. Reboot.

Note 1: This is necessary because the included open-source default driver *nouveau* doesn't properly support your graphics card therefore proprietary drivers are a must.

Note 2: Better install 19.10 instead of 18.04 or even the not yet released 20.04 (will be released in April) that is sufficiently stable now. Newer hardware benefits a lot from newer releases and, on top of that, with 19.10 or newer you can select an option to install third-party drivers and firmware that now includes the Nvidia drivers you need (and is also possible but not guaranteed, of course, that the newer nouveau version have better support for your graphics card in which case you wouldn't need the workaround with nomodeset).

---

### Post by dbee on 2020-02-21
Thanks CelticWarrior. 

That's the price i pay for getting new hardware. It takes a little while for the software/drivers to catch up.

I'll try that and get back to you if i have any problems :-)

All the best

---

### Post by dbee on 2020-02-22
I don't get it - why does Ubuntu version 18.04 come as an LTS with 5 years support. 

While ubuntu 19.10 come with support only till July ?

---

### Post by dbee on 2020-02-22
OK I've updated grub and booted up into ubuntu live 19.04.
It no longer crashes.

But I can't connect to WiFi. ... I guess that's expected.

So basically you're saying I should boot up using nomodeset in grub. install from there. Also enter nomodeset in grub on first boot of the new installation. Then boot up into the low res gui and go to additional drivers. Install nvidia third party drvers rather than enabling third party drivers in the installation process ?

---

### Post by mörgæs on 2020-02-22
If you have studied the support scheme you will notice that 19.04 has reached end of life. As mentioned above 19.10 is your best chance. 

First try to see if it all works using 19.10 and a wired internet connection.

By the way, using Thread Tools you can mark the thread solved when it is. Better than editing the thread title.

---

### Post by him610 on 2020-02-22
> As mentioned above 19.10 is your best chance.
Or you could download and install 20.04 Developmental which will be upgraded to LTS in April and will be good for 5 years. I have 20.04 installed on two computers and have not experienced in serious issues yet.

---

### Post by dbee on 2020-02-22
I don't really trust daily builds ... I need this computer for work...

---

### Post by dbee on 2020-02-22
Yeah, sorry typo. I've downloaded and burned 19.10 onto my usb key but the live version doesn't work without adjusting grub.

I don't have an ethernet cable handy and tomorrow is Sunday. So i think i'll just install and hope for the best.

---

### Post by jeremy31 on 2020-02-22
Can you tether using a USB cable to a smartphone?  If your wifi doesn't work after installing, start a new thread in networking & wireless, see the sticky thread [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by dbee on 2020-02-22
Yeah, I couldn't connect to my mobile network either.

I pressed the WPS button on the broadband router and i was able to connect.

Then i installed the proprietary nvidia drivers and everything seems to fine now. I had to install the legacy nvidia drivers, the new ones didn't install. Fingers crossed. Everything works from here

The only problem is that i can't seem to connect to the 5g broadband network :-(

---

