---
title: "Nvidia drivers - Restricted Manager does not work."
date: 2009-01-18
forum: Hardware
---

### Post by Kossilar on 2009-01-18
Hey folks.

I'm trying to install drivers for the Geforce 8600 mobile in my laptop. Unfortunately the restricted driver manager fails to work and manually installing the 180 driver from the NVIDIA website breaks X. According to synaptic I should already have the 177 drivers installed(I have no idea how that happened since I didn't install them manually) however the system is not using them. 

Does anybody know how I can fix this problem?

---

### Post by jskandhari on 2009-01-18
STEP 1:

System>Administration>Synaptic Package Manager

search for nvidia-177 driver and mark it for installation ; also check its associated drivers are also installed ; incase it is already installed proceed to step 2.

STEP 2:
System>Administration>Hardware Drivers

Select the 177 and click on enable.

>>Note : Make sure you have the Administrator Password else you won't be able to do any changes<<

---

### Post by Kossilar on 2009-01-18
> I'm trying to install drivers for the Geforce 8600 mobile in my laptop. Unfortunately the restricted driver manager fails to work and manually installing the 180 driver from the NVIDIA website breaks X. According to synaptic I should already have the 177 drivers installed(I have no idea how that happened since I didn't install them manually) however the system is not using them.

Hello, thank you for taking the time to reply to my post. As stated in the thread name, the restricted driver manager is not functioning correctly and, while the 177 drivers appear to be installed correctly in synaptic they are not actually working.

---

### Post by RJARRRPCGP on 2009-01-18
You can install 180x with Synaptic.

---

### Post by Kossilar on 2009-01-19
Hmmm. Okay well I managed to get the drivers installed and enabled using the Hardware Manager, even though it fumbled through it madly. 

However, although it now tells me that the drivers are enabled, it didn't bother to configure xorg.conf for me. Which means I'm going to have to do it the hard way right?

Wait no... apparently running nvidia-xconfig sets up the xorg.conf for me, only the NVIDIA drivers still fail to load properly on reboot.

---

### Post by geezerone on 2009-01-19
Which version of Ubuntu are you using as only driver 169.12 is available in nvidia-glx?

---

### Post by Kossilar on 2009-01-22
I'm using version 8.10. I've managed to get the driver to work now. By carefully killing the other drivers that the restricted driver manager refused to enable and then installing and enabling(somehow) the 180 drivers.

What a mess.

---

### Post by holotropik on 2009-01-22
I am going through this issue myself...no end of frustration! I just need to know what I can edit, other than xorg.conf, so i can get rid of ghost entries for drivers that I dont even have installed!
I wish there was a simple way to reset the drivers so I could start from scratch..?

---

