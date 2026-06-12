---
title: "to install nvidia driver"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by garrynigel on 2009-01-03
hi i have a nvidia geforce 7200 gs grafix card installed on my computer.. along .its a 256 mb grafix card with onboard support of 512 mb with pci express .. so i wanted to install d drivers andi went to the nvidia website [http://www.suse.de/~sndirsch/nvidia-installer-HOWTO.html](http://www.suse.de/~sndirsch/nvidia-installer-HOWTO.html) and dey gave me dis html to read.. now im wondering.. do i have to install the drivers or the drivers available by linux in the system>administartion>hardware drivers version 177 is enuf or not..
in dis document dey r tellin me to install using YaST.. i checked in d repository its not der...so i dunno wat to do please help

---

### Post by oldos2er on 2009-01-03
Use System, Administration, Hardware Drivers to enable the Nvidia drivers.

---

### Post by garrynigel on 2009-01-03
he dude dat thing was already in use.. before i put the grafix card....and .. its detected even in dat nvidia server settings..d grafix card is detected and i have already activated nvidia accelerated grafix drivers 177 .. latest ones dat der.. sow at do i do.. i mean is the grafix card already used or do i need to install more drivers

---

### Post by 2hot6ft2 on 2009-01-03
It's already installed and in use then there's nothing else to do except maybe set your screen resolution.
System>Preferences>Screen Resolution

---

### Post by DeMus on 2009-01-03
> **garrynigel said:**
> hi i have a nvidia geforce 7200 gs grafix card installed on my computer.. along .its a 256 mb grafix card with onboard support of 512 mb with pci express .. so i wanted to install d drivers andi went to the nvidia website [http://www.suse.de/~sndirsch/nvidia-installer-HOWTO.html](http://www.suse.de/~sndirsch/nvidia-installer-HOWTO.html) and dey gave me dis html to read.. now im wondering.. do i have to install the drivers or the drivers available by linux in the system>administartion>hardware drivers version 177 is enuf or not..
in dis document dey r tellin me to install using YaST.. i checked in d repository its not der...so i dunno wat to do please help

Why on earth do you go to a Suse.de site to install nVidia drivers in Ubuntu?
Open Synaptic Package Manager and search for EnvyNG. Install that program and run it. ( it shows up in your main menu Applications | System Tools.
It will download the latest nVidia driver and install it automatically.
All you have to do is reboot. It worked great for me and it's so simple.
Good luck with it.

DeMus

---

