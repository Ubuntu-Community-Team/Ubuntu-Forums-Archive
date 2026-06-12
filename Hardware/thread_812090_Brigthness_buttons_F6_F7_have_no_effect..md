---
title: "Brigthness buttons F6 F7 have no effect."
date: 2008-05-29
forum: Hardware
---

### Post by roy.nico on 2008-05-29
Hej 

I have a laptop Fujitsu T4220, with Ubuntu Hardy. The brightness buttons (Fn+F6 and Fn+F7) seem to have no effect. I have to mention that on the other hand the sound volume buttons (Fn+F8 and Fn+F9) work well. 
Any idea, how i could solve this ? 

Thanks in advance, 

Nicolas

---

### Post by stephen53 on 2008-05-29
I have a Asus laptop model # M7V series. I have notice the same thing in my note book. I have a light sensor that controls the LCD backlight. After I upgraded from dapper to hardy it started to work. The keys to control the brightness are not working. I found the package smartdimmer on my machine and think that is controlling  the LCD brightness. I am searching for some way that I can tweak smartdimmer  as in low light it is too dim for my old eyes. The documentation on my machine is sparse .

---

### Post by hotweiss on 2008-05-29
> **stephen53 said:**
> I have a Asus laptop model # M7V series. I have notice the same thing in my note book. I have a light sensor that controls the LCD backlight. After I upgraded from dapper to hardy it started to work. The keys to control the brightness are not working. I found the package smartdimmer on my machine and think that is controlling  the LCD brightness. I am searching for some way that I can tweak smartdimmer  as in low light it is too dim for my old eyes. The documentation on my machine is sparse .

To get your brightness keys working just follow these instructions:

A) Open Terminal (Menu->Accessories), and type the following:
sudo nano brightness

B) Now paste the following in the Terminal window:
#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
sudo mv brightness /etc/init.d
and then
sudo chmod 755 /etc/init.d/brightness
and then
sudo update-rc.d brightness defaults 90

E) Reboot, and you will have regained control of your brightness level.

---

### Post by stephen53 on 2008-05-29
Thank you hotweiss. That got my brightness applet working. Only the brightness key is working. The key to lower brightness did not change the brightness.  I understood what was done until sudo update-rc.d brightness defaults 90 . Could you explain what that command did? Thanks again.

Stephen

---

### Post by roy.nico on 2008-05-30
> **hotweiss said:**
> 
B) Now paste the following in the Terminal window:
#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch



I tried to follow and adapt this solution for my Fujitsu T4220. Something must be changed for sure, but i don't know what. My /sys directory :
```
 ls /sys/devices/platform/
bay.0      dock.0  fsc_btns  iTCO_wdt        pcspkr  serial8250
bluetooth  eisa.0  i8042     parport_pc.888  power   uevent

```


nicolas

---

### Post by hardyn on 2008-06-09
if you key:

man update-rc.d

it gives a description of the command.  It inserts the script into the startup script.  Defaults specifies the command style, and 90 is a run priority.

---

