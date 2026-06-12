---
title: "Ambient Light Sensor on 9.10"
date: 2009-10-30
forum: Hardware
---

### Post by Fender89 on 2009-10-30
Like everyone else, I downloaded 9.10 today. I'm just having one problem that I'm sure someone who understands the 9.10 folder structure better than I could solve in a few seconds. 

My laptop has an ambient light sensor that must be turned off for me to be able to adjust screen brightness, I usually use the following tutorial when I install ubuntu, but I'm guessing things have been moved around in the new release. Can someone please amend these few terminal commands so I can once again blindly paste them in and have it work magically when I reboot. Needless to say; I'm a microsoft noob. Thanks guys.

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

### Post by Fender89 on 2009-11-01
Shameless bump. Need a reply.

---

### Post by Fender89 on 2009-11-01
After the last step I get:

update-rc.d: warning: /etc/init.d/brightness missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/brightness already exist.

No idea what LSB information is.

---

### Post by Louigi Verona on 2009-11-03
Hey!
I have had the same problem and solved it. Do everything that the instruction says but change this:

echo 0 > /sys/devices/platform/**asus-laptop**/ls_switch 
to
echo 0 > /sys/devices/platform/**asus_laptop**/ls_switch

Do not mind the LSB thing, I read it simply says the file lack info on the order of loading during the boot or whatever, it's just a warning, not an error.

Anyway, reboot - and brightness will be restored.

---

