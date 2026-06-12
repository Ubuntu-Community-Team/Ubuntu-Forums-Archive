---
title: "Hardy - Intel 855gm and screen resolution"
date: 2008-05-26
forum: Hardware
---

### Post by bandeeri on 2008-05-26
Hi, i've installed Hardy on a DELL latitude D505 with an Intel 855gm graphics card. All went fine but i can't set the screen resolution higher than 1024x768. I tried 915resolution but nothing more.

Any idea?

---

### Post by housam on 2008-05-26
Try this 

```
sudo nano /etc/usplash.conf
```
 you will got something like that 


> # Usplash configuration file
# These parameters will only apply after running update-initramfs.
  

add the required resolution 

> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=[COLOR="Red"]1280[/COLOR]
yres=[COLOR="Red"]1024[/COLOR] 
 
OR put the settings you want for [COLOR="Red"] x & y [/COLOR]then reboot and type :

```
sudo dpkg-reconfigure usplash
```
then check for the new settings -- System > Preferences > Screen Resolution and select the new one.

---

### Post by prshah on 2008-05-26
> **bandeeri said:**
> an Intel 855gm graphics card. All went fine but i can't set the screen resolution higher than 1024x768. 

You may either be using the vesa driver or an outdated intel driver. To confirm, press Alt+F2, then give the command ```
gksudo displayconfig-gtk
```, press enter, then give your password.

In the new window that open up, choose the "Graphics Card" tab. It should show "Intel experimental modesetting driver"; if it shows "i810" or "vesa" or anything else, post back here for instructions on how to update to the latest driver.

---

### Post by bandeeri on 2008-05-26
> **housam said:**
> Try this 

```
sudo nano /etc/usplash.conf
```
 you will got something like that 



  

add the required resolution 


 
OR put the settings you want for [COLOR="Red"] x & y [/COLOR]then reboot and type :

```
sudo dpkg-reconfigure usplash
```
then check for the new settings -- System > Preferences > Screen Resolution and select the new one.

I tried this but nothing change.

---

### Post by bandeeri on 2008-05-26
> **prshah said:**
> You may either be using the vesa driver or an outdated intel driver. To confirm, press Alt+F2, then give the command ```
gksudo displayconfig-gtk
```, press enter, then give your password.

In the new window that open up, choose the "Graphics Card" tab. It should show "Intel experimental modesetting driver"; if it shows "i810" or "vesa" or anything else, post back here for instructions on how to update to the latest driver.

The driver was i810 so i changed it to Intel experimental. I died this changement 3 times to valid it but nothing more, i'm still in 1024x768.

---

### Post by prshah on 2008-05-27
> **bandeeri said:**
> The driver was i810 so i changed it to Intel experimental. I died this changement 3 times to valid it but nothing more, i'm still in 1024x768.

If it didn't change, maybe you need to install the latest driver; use```
sudo apt-get install xserver-xorg-video-intel
```, then make the change, save, logout and press Ctrl_Alt_BkSpace to restart the Xserver.

Also make sure that "Video memory" is set to automatic.

---

### Post by bandeeri on 2008-05-27
> **prshah said:**
> If it didn't change, maybe you need to install the latest driver; use```
sudo apt-get install xserver-xorg-video-intel
```, then make the change, save, logout and press Ctrl_Alt_BkSpace to restart the Xserver.

Also make sure that "Video memory" is set to automatic.

I've already installed the latest driver.

---

### Post by mars17tv on 2008-11-06
Up,up,up
I have the same problem here. I tried all these but nothing change.
Any suggestion please :(

---

