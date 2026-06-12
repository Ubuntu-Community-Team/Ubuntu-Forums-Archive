---
title: "How to install Nvidia Geforce 820M drivers?"
date: 2015-07-30
forum: Hardware
---

### Post by %(gej%) on 2015-07-30
I've installed Ubuntu 15.04 (64-bit) in Asus X555LD notebook. I followed [this]("https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers") post & tried to install Nvidia drivers using the PPA.
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```
But 'Intel® HD Graphics 5500 (Broadwell GT2)' is the one that's still in use. So how can I install Nvidia drivers in my notebook?

---

### Post by grahammechanical on 2015-07-31
Do you mean that you have hybrid graphics? And Intel Graphic adapter and a Nvidia graphic adapter? If so, then once you have the Nvidia driver installed you will need to use the Nvidia settings manager to switch between the two adapters.

So, far all you have done is added the PPA as a software source/repository and updated the list of software sources. Try using Additonal Drivers to see if it will now offer a greater range of Nvidia drivers than before.

Regards.

---

### Post by NathanRodriguez on 2015-07-31
Here on my system the Nvidia drivers appeared normally in the Additional Drivers (System -> Preferences) tab, WITHOUT need for adding a PPA.

---

### Post by Vladlenin5000 on 2015-08-01
> **NathanRodriguez said:**
> Here on my system the Nvidia drivers appeared normally in the Additional Drivers (System -> Preferences) tab, WITHOUT need for adding a PPA.


Like they always do... The point here is whether or not the offered versions already support the hardware. 
A Nvidia 820M requires 346.47 as the first nvidia driver to support it, 352.xx is the current recommendation.
Ubuntu 15.04 offers some 346; Ubuntu 14.04 offers up to 331.xx only. As such, adding a PPA and installing a newer version is in order for this card/chip. You already done that and it's usually enough to apt-get update/upgrade _provided you already have some nvidia driver installed_ (you don't). Otherwise just install it (after the usual update/upgrade):
```
sudo apt-get install nvidia-352
```

---

### Post by Keith_Helms on 2015-08-01
Why do you think that the 346 driver is needed to support an 820m card?  According to Nvidia's doc, support for the 820m is present in the 331.113 driver, which is the latest in the repository for 14.04.

See here:
[http://www.nvidia.com/Download/driverResults.aspx/80533/en-us](http://www.nvidia.com/Download/driverResults.aspx/80533/en-us)

I would avoid messing with PPAs that contain newer versions of video drivers that are in the repository where possible.

---

### Post by %(gej%) on 2015-08-02
> Here on my system the Nvidia drivers appeared normally in the  Additional  Drivers (System -> Preferences) tab, WITHOUT need for  adding a PPA.
I checked Additional Drivers in Software & Updates, but there weren't any drivers for Nvidia.

```
sudo apt-get install nvidia-352
```
I tried this after adding the PPA, but I got a black screen after restarting Ubuntu.

EDIT: I installed 346 driver from the repository & it's working fine. Thank you all for the help. :D

---

