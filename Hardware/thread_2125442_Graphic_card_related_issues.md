---
title: "Graphic card related issues"
date: 2013-03-14
forum: Hardware
---

### Post by chaitanya2106 on 2013-03-14
My laptop is of 2008. It has an inbuilt nvidia graphic card. I am running Ubuntu 12.04 LTS. I have not installed additional drivers. How is it running then? Is it using the VGA adapter? Is that adapter installed in the motherboard? 
Laptop has some graphic issues, in the previous edition of ubuntu i installed those drivers and then display used to freeze after sometime. Nothing of the sort happens when not installing those drivers.

Laptop configuration:
Dell Vostro 1400
1.8 GHz Intel Core 2 Duo,
Nvidia Geforce 8400M GS 128 MB dedicated memory,

---

### Post by Mr. Shannon on 2013-03-14
By default Ubuntu will use the nouveau open source drivers for NVIDIA cards.

---

### Post by chaitanya2106 on 2013-03-14
> **Mr. Shannon said:**
> By default Ubuntu will use the nouveau open source drivers for NVIDIA cards.

then is it okay that i dont download those additional drivers?

---

### Post by VeeDubb on 2013-03-14
> **chaitanya2106 said:**
> then is it okay that i dont download those additional drivers?

It is, but you won't have 3d accelleration.  If all you want to do is web browsing, editing documents, (no graphics intensive tasks) then the built in drivers are actually your best choice.

If you want to be able to have your video card assist with decoding high def video, play video games, etc, you will need the additional drivers.  Just don't research how to install the nvidia drivers online.  What you'll find is a bunch of outdated non-sense, much of which keeps getting reposted by people who just refuse to get with the times.  Just use the additional drivers menu and let it do the thinking.

---

### Post by grahammechanical on 2013-03-14
The Nouveau open source driver is much improved since about a year ago. I am able to run 12.04 with 3D effects such as wobbly windows using the Nouveau driver. In comparison I have found Nvidia drivers to be broken at times. I do test installs of Ubuntu and I have had too many installs not load to a desktop due to the Nvidia driver. So, I never tick to install third party software as that will bring the Nvidia driver.

Many of the Compiz 3D affects are no longer being developed and they are not available from 12.10 onwards. So, there is not a noticible difference in look between Nvidia and Nouveau drivers. Under Nouveau I can resize the Launcher icons. Which we could not do before.

My advice is, if you want to try the Nvidia driver then try it but be prepared to use Recovery Mode>Resume to get to a desktop and then experiment with different drivers.

Regards.

---

### Post by Cheesemill on 2013-03-14
> **grahammechanical said:**
> So, I never tick to install third party software as that will bring the Nvidia driver.

AFAIK choosing to install 3rd party software during installation will not install proprietary graphics drivers, just the [ubuntu-restricted-addons]("http://packages.ubuntu.com/quantal/ubuntu-restricted-addons") package.
I did some research a while ago but it's hard for me to get a definitive answer as I only have Intel hardware.

For more info see my thread here...
[http://ubuntuforums.org/showthread.php?t=2098817](http://ubuntuforums.org/showthread.php?t=2098817)

If you have anything to add on the matter I would be very grateful.

---

