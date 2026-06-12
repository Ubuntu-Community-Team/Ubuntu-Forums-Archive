---
title: "[SOLVED] Need help with my acpi4asus update to get my screen brightness fixed"
date: 2008-05-19
forum: Hardware
---

### Post by hotweiss on 2008-05-19
I have just installed Ubuntu Hardy and everything is working minus my screen and webcam. I've found a solution for the webcam. My screen on the other hand is very dim, the problem lies with the ambient light sensor. On the acpi4asus web site it states that the latest version has the fix. Can someone give me detailed instruction on how to perform this update? Thanks.

[http://acpi4asus.sourceforge.net/](http://acpi4asus.sourceforge.net/)

---

### Post by hotweiss on 2008-05-20
> **hotweiss said:**
> I have just installed Ubuntu Hardy and everything is working minus my screen and webcam. I've found a solution for the webcam. My screen on the other hand is very dim, the problem lies with the ambient light sensor. On the acpi4asus web site it states that the latest version has the fix. Can someone give me detailed instruction on how to perform this update? Thanks.

[http://acpi4asus.sourceforge.net/](http://acpi4asus.sourceforge.net/)

OK I read the date incorrectly. O.41 is from 2007. None the less I found the fix:

A) Open Terminal, and type the following:
sudo nano brightness

B) Now paste the following in the Terminal window:
#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typin the following in Terminal:
sudo mv brightness /etc/init.d
and then
sudo chmod 755 /etc/init.d/brightness
and then
sudo update-rc.d brightness defaults 90

E) Reboot, and you will have regained control of your brightness level.

---

### Post by hookysun on 2008-08-30
> **hotweiss said:**
> OK I read the date incorrectly. O.41 is from 2007. None the less I found the fix:

A) Open Terminal, and type the following:
sudo nano brightness

B) Now paste the following in the Terminal window:
#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typin the following in Terminal:
sudo mv brightness /etc/init.d
and then
sudo chmod 755 /etc/init.d/brightness
and then
sudo update-rc.d brightness defaults 90

E) Reboot, and you will have regained control of your brightness level.

it worked! i was having to stick a usb gooseneck light directly onto the sensor to get the screen bright enough, and now... i love you, hotweiss.

---

