---
title: "ATI Radeon HD 3800 Drivers"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by Zireth ZH on 2009-04-07
How do I get catalyst 9.2 or 9.3 installed??? Ive downloaded the linux drivers but cant get it to install cuz Im completely lost in some steps..

Right now I have an ATI driver installed but those are not the latest one ... and appareantly it seems that they are for HD 2900 etc. I got those I think from synaptics... 

Please, Im new using linux and I cant understand 100% the guides ive found by googling it....

If someone can take his time to explain me step by step for easy understanding having in mind that im a newbie I will really appreciate it.  Please....

Thanks ):P

---

### Post by TwistedTripper on 2009-04-07
I've always followed Method 2 on this guide [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) . Assuming you're running Hardy.

You may have to remove the driver you have installed at the moment. Possibly try the following, replacing 8.5x with the version you installed.

> sudo dkms remove -m fglrx -v 8.522 --all

Sorry if that isn't much help but I don't know the ins and outs all that well.

---

### Post by Mark Phelps on 2009-04-07
An alternative, if you don't want to mess with manually installing the drivers, is to use EnvyNG.  It's an application that will handle the installation and uninstallation of ATI and Nvidia video drivers.

See the following link for details:
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

