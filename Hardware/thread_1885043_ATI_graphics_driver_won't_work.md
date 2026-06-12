---
title: "ATI graphics driver won't work"
date: 2011-11-22
forum: Hardware
---

### Post by shredmaster on 2011-11-22
ubuntu 11.04
my laptop is a Pavilion dv7-4183cl HP model. It comes with these graphic drivers:
VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] (5470 to be precise)

when i check if there are additional drivers for my computer it displays the following:

ATI/AMD proprietary FGLRX graphics driver

naturally, i click on the option to download and install such driver. once done, ubuntu prompts me to restart my computer. once i reboot, ubuntu tells me that i don't have the hardware to use unity and prompts me to use the classic view. things is, i can't run any programs that require 3d graphics! what can i do to fix this?

---

### Post by collisionystm on 2011-11-22
> **shredmaster said:**
> ubuntu 11.04
my laptop is a Pavilion dv7-4183cl HP model. It comes with these graphic drivers:
VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] (5470 to be precise)

when i check if there are additional drivers for my computer it displays the following:

ATI/AMD proprietary FGLRX graphics driver

naturally, i click on the option to download and install such driver. once done, ubuntu prompts me to restart my computer. once i reboot, ubuntu tells me that i don't have the hardware to use unity and prompts me to use the classic view. things is, i can't run any programs that require 3d graphics! what can i do to fix this?


Download this

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

When finished, 

Right click on the file, go to permissions, check the box to mark the file as executable.

Double click it and hit run.

Choose express setup, let it run.

When finished, open a terminal
```

sudo aticonfig --initial -f
```

reboot

---

### Post by shredmaster on 2011-11-22
I followed your instructions. While doing so everything seemed to be going fine. However, once i tried to reboot, i got stuck on a black screen displaying some commands the computer was running. The computer did NOT freeze, but it just did nothing. I recalled that, while on Windows 7, if i disconnected the AC cable the graphics card would respond differently... so i tried both plugged in and D/C. It would display different results for each case, but it would still stay put and do nothing. I'm wondering if i have to install the proprietary driver that ubuntu tells me to install at the begging? I figured that there was no need, specifically since there would be conflict between the two, but i dont know. I ended up reinstalling ubuntu. Should i try an alternative solution or keep trying with yours? Thanks in advanced.

---

### Post by collisionystm on 2011-11-22
> **shredmaster said:**
> I followed your instructions. While doing so everything seemed to be going fine. However, once i tried to reboot, i got stuck on a black screen displaying some commands the computer was running. The computer did NOT freeze, but it just did nothing. I recalled that, while on Windows 7, if i disconnected the AC cable the graphics card would respond differently... so i tried both plugged in and D/C. It would display different results for each case, but it would still stay put and do nothing. I'm wondering if i have to install the proprietary driver that ubuntu tells me to install at the begging? I figured that there was no need, specifically since there would be conflict between the two, but i dont know. I ended up reinstalling ubuntu. Should i try an alternative solution or keep trying with yours? Thanks in advanced.


okay you may have missed a step.

When Ubuntu boot's and you are at the black screen with the text
hit CTRL + ALT + F2
Login to the computer
```

sudo aticonfig --initial -f
``````

sudo lightdm --full-restart
```

---

### Post by Mark Phelps on 2011-11-23
This is another of the Dv7's with switchable graphics -- which present real problems to Ubuntu.  

It's going to default to try to use the onboard Intel chip unless you disable that.  

While you may be able to do that in the BIOS, THEN, you no longer have the switchable graphics option back in Windows.

---

### Post by shredmaster on 2011-12-01
I tried the 
sudo aticonfig --initial -f
sudo lightdm --full-restart
but it told me that lightdm did not exist. so i reinstalled ubuntu 11.10 and looked up what it was, and apparently it's installed by default on ubuntu 11.04 and 11.10, but when i looked for it, i had to install it manually!

anyway, starting your instructions once again, i "installed" the driver once again, but when i put the first command on the terminal i get this:

Uninitialised file found, configuring.
PowerXpress error: Cannot stat '/usr/lib64/fglrx': No such file or directory
Failed to initialize libglx for discrete GPU
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-0

so i figured that the installation did not finish as intended. im scared that if i reboot ill get stuck again.

---

### Post by collisionystm on 2011-12-01
> **shredmaster said:**
> I tried the 
sudo aticonfig --initial -f
sudo lightdm --full-restart
but it told me that lightdm did not exist. so i reinstalled ubuntu 11.10 and looked up what it was, and apparently it's installed by default on ubuntu 11.04 and 11.10, but when i looked for it, i had to install it manually!

anyway, starting your instructions once again, i "installed" the driver once again, but when i put the first command on the terminal i get this:

Uninitialised file found, configuring.
PowerXpress error: Cannot stat '/usr/lib64/fglrx': No such file or directory
Failed to initialize libglx for discrete GPU
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-0

so i figured that the installation did not finish as intended. im scared that if i reboot ill get stuck again.


Are you even using a 64 bit ubuntu install???

---

### Post by collisionystm on 2011-12-01
nevermind, I read a post online. 

you will be okay with the message you received

[http://www.linuxquestions.org/questions/linux-hardware-18/radeon-hd-6670-problems-no-kms-black-screen-883047/](http://www.linuxquestions.org/questions/linux-hardware-18/radeon-hd-6670-problems-no-kms-black-screen-883047/)

reboot

---

### Post by MoreOrLess on 2011-12-01
Sighhh.. I can't believe they haven't fixed that bug where jockey offers proprietary drivers and screws up hybrid GPU systems.

The fglrx driver isn't going to work (unless you can disable the integrated intel graphics in your BIOS, which you probably can't). I suggest removing fglrx (and delete /etc/X11/xorg.conf too): [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

The best solution is to turn off the ATI card to save battery (either in BIOS if possible or using vgaswitcheroo).

Also, now would be a good time to learn what recovery mode is and how to boot in safe graphics mode to fix your system (unless you miss the thrill of reinstalling from being a Windows user).

---

### Post by MoreOrLess on 2011-12-01
I'm not sure where you came up with this:
> lightdm --full-restart
I think you mean:
```
sudo service lightdm restart
```

---

### Post by collisionystm on 2011-12-01
> **MoreOrLess said:**
> I'm not sure where you came up with this:

I think you mean:
```
sudo service lightdm restart
```

Easy. 

Lightdm --help

Check it out, I'm not crazy ;)

---

### Post by MoreOrLess on 2011-12-01
I don't see that option...

---

### Post by collisionystm on 2011-12-01
try typing just 'lightdm'

it was on my system

I am not on ubuntu at the moment

---

### Post by shredmaster on 2011-12-01
as a matter of fact i am :)

---

### Post by collisionystm on 2011-12-02
> **shredmaster said:**
> as a matter of fact i am :)


lol. 

I actually replaced my ubuntu with opensuse....shhhhhh... dont tell anyone! 

I installed lightdm on there and, yeah, I dont see the option.

I swear it was in there on my ubuntu. It was when I was trying to get my radeon graphics to work and I was living out of tty messing with settings. 

lightdm --full-reset or --full-restart was in there.

---

