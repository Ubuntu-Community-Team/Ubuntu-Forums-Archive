---
title: "Graphical Glitches!"
date: 2012-10-24
forum: Hardware
---

### Post by t5tu4ergj5ug9 on 2012-10-24
I installed Lubuntu 12.10 (32-bit) and everything went fine. However, there are some weird graphical glitches. It mainly affects icons not showing until  I hover my cursor over them (for example, the icons in the Software Center categories. It also affects check-boxes.
Edit: Found a fix: In the Font options, I had to change Sub-pixel Geometry from RGB to None.

---

### Post by t5tu4ergj5ug9 on 2012-10-24
/Deleted

---

### Post by wojox on 2012-10-24
It's right in Software Sources.

---

### Post by t5tu4ergj5ug9 on 2012-10-25
/Deleted

---

### Post by myromance123 on 2012-10-25
Installing Nvidia drivers manually is a bit difficult.

**_TAKE NOTE: Nvidia OPTIMUS has NO LINUX DRIVERS. Hybrid Nvidia/Intel setups don't have drivers either. If you are on a laptop and this is your case, the open source driver is currently the only way to go._**

To put it basically, you'd have to:
1. Download driver, and remember where you downloaded it.
2. Right click it -> Properties -> Permissions -> Tick "Allow Execute"
4. Ctrl+Alt+F1 (to bring up a fullscreen terminal)
5. Stop the GUI (sudo service lightdm stop)
3. Purge/Uninstall Nouveau (the Open Source driver)
6. CD to the driver (.run)
7. Install driver (sudo ./DRIVER_NAME_HERE)
8. Restart (sudo reboot)

I guided a friend on installing an Nvidia driver for his 9300M GS but it wasn't easy. There were problems with the dkms for his driver VS Lubuntu. It kept winding up giving us an error titled "broken pipe". The only way we made it work was by saying no to dkms for the driver. This means he has to manually reinstall the driver if Lubuntu updates the kernel-headers.

NOTE: The last Lubuntu I tried was Lubuntu 12.04, and this problem of icons only appearing after hovering over them existed for me as well. Installing the driver did not fix the problem for me.

P.S: I also believe there is a PPA with Nvidia-Updates or something in the title that makes it a whole lot easier to install Nvidia proprietary drivers. I can't remember where I found it however.

---

### Post by t5tu4ergj5ug9 on 2012-10-25
/Deleted

---

### Post by myromance123 on 2012-10-25
I am not entirely sure, but is your Lubuntu up to date?
When I installed Lubuntu 12.04 on my HP DV3500, no drivers were shown in the Additional Drivers.

I had to update Lubuntu through the update manager and restart Lubuntu, after that my drivers appeared in the Additional Drivers. Not sure if it would be the same case with yours.

I also remember trying this command, which I think is the same as installing the Nvidia driver from Additiona Drivers.
```
sudo apt-get install nvidia-current
```

You can give it a go if you're willing.

---

