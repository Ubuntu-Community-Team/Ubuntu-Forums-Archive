---
title: "UBUNTU 11.04 with Intel Hub US15W graphics card support"
date: 2011-10-31
forum: Hardware
---

### Post by suvendu4urs on 2011-10-31
Hi...

I have one System which has an Atom processor Z510/Z530 Series and Intel System Controller Hub US15W chipset. 

I have installed UBUNTU 11.04.After installation it is saying that Hardware is not found for running UNITY.So please switch to UBUNTU classic.

I request you to please provide the information for how to enable Graphics card support for this hardware.

Please come back soon with some reply

---

### Post by suvendu4urs on 2011-10-31
Hello All,

I have followed the steps mentioned in this forum:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

After doing this i am able to get the Unity for 11.04.It means my graphics card is enabled.

But due to this i am unable to play my video in VLC.Videois getting played but there is no image.I guess some decoder is missed out.


Let me know if you guys have some solution or ideas.

Thanks....

---

### Post by suvendu4urs on 2011-10-31
steps followed are:


Emgd drivers (currently supported)

Drivers are available in the gma500 PPA repository for Natty, Maverick and Lucid

Repository page: [https://launchpad.net/~gma500/+archive/emgd](https://launchpad.net/~gma500/+archive/emgd)


Instructions for Natty only. Open a terminal and type:

sudo add-apt-repository ppa:gma500/emgd 
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms emgd-xorg-conf
sudo emgd-xorg-conf
reboot for the changes to take effect.

---

