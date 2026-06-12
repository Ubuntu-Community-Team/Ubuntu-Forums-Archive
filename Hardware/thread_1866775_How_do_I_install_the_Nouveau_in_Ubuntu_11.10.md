---
title: "How do I install the Nouveau in Ubuntu 11.10"
date: 2011-10-21
forum: Hardware
---

### Post by cjschris on 2011-10-21
All of the documentation is outdated, at least for me.

How can I remove the Nvidia drivers and put in the Nouveau ones?
I don't mind if you just like to a working thread, but I can't find one.

---

### Post by coffeecat on 2011-10-22
The nouveau driver is the default open source driver. If you've installed the proprietary nvidia driver through Additional Drivers, all you need to do is open Additional Drivers again, disable the nvidia driver and reboot. I'm not sure how far the nouveau driver has come in 11.10, so you may lose the ability to run Ubuntu 3d if you use the nouveau driver, but Unity 2d will still be available.

If you installed the nvidia driver from a package downloaded from the nvidia website, there will be an uninstall script to run. I don't know the details as I've never done this. If this is the case with your driver, post back and someone will be able to help.

---

### Post by Cordess on 2012-03-12
> **coffeecat said:**
> The nouveau driver is the default open source driver. 

That's not the case for Geforce 4 4800 SE Ti cards.

I use one, and Ubuntu is using the VESA driver.
The samy applies to after switching from Ubuntu 11.10 to Ubuntu 12.04 beta.


> 
If you've installed the proprietary nvidia driver through Additional Drivers, all you need to do is open Additional Drivers again, disable the nvidia driver and reboot. 

On 12.04 additional drivers doesn't even detect my videocard as a card from NVidia.

So it is even not possible to install the nvidia-96 drivers and
the Xorg.conf file is empty on 12.04.


So i am really interestest how to install nouveau manually.

---

### Post by grahammechanical on 2012-03-13
There is this:

[http://nouveau.freedesktop.org/wiki/InstallNouveau]("http://nouveau.freedesktop.org/wiki/InstallNouveau")

And this:

[http://www.omgubuntu.co.uk/2011/03/nouveau-open-source-3d-graphics-drivers-for-nvidia-in-ubuntu/]("http://www.omgubuntu.co.uk/2011/03/nouveau-open-source-3d-graphics-drivers-for-nvidia-in-ubuntu/")

Regards.

---

