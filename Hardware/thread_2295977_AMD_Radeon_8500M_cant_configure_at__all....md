---
title: "AMD Radeon 8500M cant configure at  all..."
date: 2015-09-22
forum: Hardware
---

### Post by stefanoskikristijan on 2015-09-22
Hello, today i switched to Ubuntu and i find it really better than Windows. But the only problem i have is to make my AMD 8500M work. In Additional Drivers the current driver is X.ORG when i try to install the fglrx drivers and restart the PC just boots to black screen and asks me to run in Low Graphich mode, troubleshot, exit the console login or reconfigure the graphics. Than ofc i run SUDO APT-GET REMOVE FGLRX* and when i reboot everything is fine. So does anyone of you guys know how can i make the switchable graphiics work ? I have Intel HD 4000 btw, and 64bit version of Ubuntu 14. Thanks,

---

### Post by mastablasta on 2015-09-23
you need to initialise after install. read more here: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

it is not necessary that it will work. sometimes it all works sometimes it doesn't. it also depends on firmware from other components and how well the their manufacturer decided to support Linux.

---

### Post by stefanoskikristijan on 2015-09-23
> **mastablasta said:**
> you need to initialise after install. read more here: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

it is not necessary that it will work. sometimes it all works sometimes it doesn't. it also depends on firmware from other components and how well the their manufacturer decided to support Linux.

I did everything from scratch and when i try to initialise it says "Graphic adapter not found" or something like that. I tried SUDO AMDCONFIG AND SUDO ATICONFIG both of them dont work for initialisation. Does anyone of you know what could be the problem ?

---

### Post by Bucky Ball on 2015-09-23
*Thread moved to **Hardware**.*

---

### Post by mastablasta on 2015-09-24
next after running:

```
sudo amdconfig --adapter=all --initial
```

you might also be interested into what cards the OS sees. you can also boot into text mode (CLI) so you can see dmesg messages and such if there are any errors and if cards get initialised well. 

if nothing works then it could be the PC is not compatible with Linux, so there is no point in using any more time. load the supported OS and be done with it :)

had a similar thing and couldn't load new GPU card that is supposedly fully supported. it seems my motherboard just didn't act well with it (opensource worked but slow, closed source driver did not). in the end I returned the card after loosing 4 or 5 days troubleshooting and re-inserted the very old GPU card.

---

### Post by Yellow Pasque on 2015-09-24
> **mastablasta said:**
> if nothing works then it could be the PC is not compatible with Linux, so there is no point in using any more time. load the supported OS and be done with it :)

You should realize that this is probably a hybrid/switchable graphics laptop (AMD calls such a configuration 'Enduro'), and that a normal, straightforward install of fglrx/Catalyst isn't going to work. I don't know what the support is like nowadays, but you used to have to kill the X server, run a script to switch from the IGP chip to the discrete Radeon, etc. In other words, you were best off not using the discrete GPU or using the open radeon source driver.

---

### Post by stefanoskikristijan on 2015-09-25
Im curently using the XORG driver with no problem but i cannot swtich using VGA Switcheroo here is the link of the thread i started for switcheroo:
[http://ubuntuforums.org/showthread.php?t=2296145](http://ubuntuforums.org/showthread.php?t=2296145)

---

