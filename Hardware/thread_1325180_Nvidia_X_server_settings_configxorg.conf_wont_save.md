---
title: "Nvidia X server settings config/xorg.conf wont save"
date: 2009-11-13
forum: Hardware
---

### Post by redfoxkt on 2009-11-13
when i go to save the configuration of my Nvidia X server settings it gives me this error:
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.
when i first press the "save to X configuration file" it pops a window and says in the search box: /etc/X11/xorg.conf then it gives me the option to browse or press save/cancel so i press save then it gives me that error i stated before i been trying to fix this for the past week or 2 and i cant figure out the problem!

thanks for the help

---

### Post by Vadi on 2009-11-13
use 

alt+f2, "gksudo nvidia-settings" to start

---

### Post by redfoxkt on 2009-11-14
> **Vadi said:**
> use 

alt+f2, "gksudo nvidia-settings" to start
i can open it through the admin link im not in ubuntu I dont remember the menu but when i set up a twin view and i go to save the config it gives me that error. then when i reboot my screen setting go back to normal

---

### Post by HappyFeet on 2009-11-14
Do:
```
sudo rm /etc/X11/xorg.conf
```
then restart nvidia-settings with:
```
gksudo nvidia-settings
```
then make all the changes you need, apply, then save configuration, and it will see you don't have a xorg.conf file. A new window will open. Hit the button lableled **show output**, and copy the file. Leave nvidia-settings open, and open a new terminal. Do:
```
sudo touch /etc/X11/xorg.conf && sudo gedit /etc/X11/xorg.conf
```
then paste what you copied from nvidia-settings. Save and reboot.

---

### Post by redfoxkt on 2009-11-15
> **HappyFeet said:**
> Do:
```
sudo rm /etc/X11/xorg.conf
```then restart nvidia-settings with:
```
gksudo nvidia-settings
```then make all the changes you need, apply, then save configuration, and it will see you don't have a xorg.conf file. A new window will open. Hit the button lableled **show output**, and copy the file. Leave nvidia-settings open, and open a new terminal. Do:
```
sudo touch /etc/X11/xorg.conf && sudo gedit /etc/X11/xorg.conf
```then paste what you copied from nvidia-settings. Save and reboot.

ok thanks it worked only problem is im using a wide screen TV and a samsung 19" monitor so it messes up a little cause of the widescreen but it worked thanks

---

