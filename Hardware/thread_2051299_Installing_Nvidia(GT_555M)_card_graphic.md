---
title: "Installing Nvidia(GT 555M) card graphic"
date: 2012-09-01
forum: Hardware
---

### Post by cyletech on 2012-09-01
Hello everyone,

I installed Ubuntu 12.04 for three times. i searched so much about installing bumblebee, installing Nvidia card graphics, and etc but i could not solve that problem till now. please help me solve this.

I have Lenovo Y570(with Nvidia GT 555M).


Thank you,
Alireza

---

### Post by davidbilla on 2012-09-06
Hi, 

I have a Lenovo Y570 too. I was able to install bumblebee and get specific programs to use the nvidia driver. 

What are the things that you tried? Did you try installing bumblebee? Did it give you an error?

---

### Post by Epodx64 on 2012-09-07
Try this add the x-swat x-updates PPA here's the link [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

add the PPA and then run sudo apt-get update

Then try jockey and see if it see's the 304.x Driver if not open a terminal and run
sudo apt-get update
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
or
sudo apt-get install nvidia-settings-updates

also if you can't get X to run at all you can do all the above from a TTY console (ctrl+alt+f1)
the 304.x Driver use to work great for me on my old Nvidia build.

---

### Post by m_duck on 2012-09-07
The Ubuntu wiki page for Bumblebee is pretty good.

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Works fine here (admittedly not on a 555, but a 525).

---

### Post by Dy1anW on 2012-09-08
Installing Nvidia drivers isn't going to help at all, since the GT 555M uses Optimus technology. Unfortunately, Nvidia have no plans [as yet] to build native linux drivers for Optimus, but older cards won't be affected by these driver issues; it also seems that only Windows 7 has support for Optimus.

@cyletech, did you uninstall all Nvidia drivers before installing Bumblebee? There seems to be an issue with that. Bumblebee uses nouveau drivers by default, and switches to nvidia under optirun, but for some reason, it may not do so. You should edit your bumblebee.conf and add "nvidia" under Driver (this is blank by default). you'll also see "nvidia-current" under the Nvidia drivers; this should just be "nvidia".

---

### Post by herczigem on 2012-10-28
Hello Friends!

I have small problem. I have laptop with Nvidia GT-555 graphics driver. My system ubuntu 12.10. I install the bumblebee.
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
After go the test in terminal type "glxspheres". This work good.
And then i try in terminal type "optirun glxspheres". Give me this answer:
[  573.894270] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[  573.894408] [ERROR]Aborting because fallback start is disabled.

Please help whats wrong? Why don't work the second graphics card.

This is laptop, alienware m14x.

Thank You!

---

### Post by m_duck on 2012-11-04
Can you post the output of:```
lsmod | grep bbswitch
```The issue I had in 12.10 is that since the kernel headers are not installed, the bbswitch module cannot be built and ergo cannot be loaded. So if the above command gives no output, this is likely the issue, otherwise I'm not sure.

Solution [here](http://askubuntu.com/questions/202644/how-to-install-nvidia-optimus-driver-on-ubuntu-12-10) (worked for me).

---

### Post by herczigem on 2012-11-09
> **m_duck said:**
> Can you post the output of:```
lsmod | grep bbswitch
```The issue I had in 12.10 is that since the kernel headers are not installed, the bbswitch module cannot be built and ergo cannot be loaded. So if the above command gives no output, this is likely the issue, otherwise I'm not sure.

Solution [here](http://askubuntu.com/questions/202644/how-to-install-nvidia-optimus-driver-on-ubuntu-12-10) (worked for me).

I chek the link and made it but don`t ready the video card.
what is the "lsmod | grep bbswitch"?

---

### Post by m_duck on 2012-11-11
> **herczigem said:**
> I chek the link and made it but don`t ready the video card.
what is the "lsmod | grep bbswitch"?

Sorry, I probably could have explained it better. If you open terminal and run it (search terminal in the dash) it will let us know of the **bbswitch** module has been loaded.

Basically, Bumblebee needs this module to be able to switch between the graphics cards. In 12.10, because the kernel headers aren't installed for whatever reason, the building of this module fails and it (obviously) can't load. The issue is that the install seems to progress fine, with a small message saying that the build failed.

The idea of the output of that command was to check if this was your problem, or if you had a different issue. If it is this issue that you have (i.e. the output from lsmod | ... is empty) then it is simply a case of removing Bumblebee, installing the kernel headers and then reinstalling Bumblebee.

---

### Post by soka80 on 2013-02-19
I know I'm doing something wrong, I have a Alienware m14, and the gt555m. I installed bumblebee just as the wiki explains. When I rebooted I got a black screen. I'm running 12.04 64-bit. Am I supposed to be installing the drivers first? Could someone shed some light on this for me?

---

