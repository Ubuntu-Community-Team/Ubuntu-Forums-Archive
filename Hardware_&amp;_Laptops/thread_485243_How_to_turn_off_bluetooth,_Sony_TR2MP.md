---
title: "How to turn off bluetooth, Sony TR2MP"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by chrisgeller on 2007-06-26
Hi

My Sony TR2MP has a switch that turns on BOTH wifi and bluetooth. In Windows if I turn it on, it asks me what I want to use.

However, in Ubuntu, they both appear to be on as standard, and the Bluetooth light is on. Is there a way I can turn it off? My wifi seems particularly flakey at the moment and I wonder if the Bluetooth is interfering.

---

### Post by olejorgen on 2007-06-27
Not sure if it'll work, but you might try disableing the bluetooth service. System->Administration->Services

---

### Post by wieman01 on 2007-06-27
You need to install a tool called "spictrl". 
> sudo apt-get install spicctrl
> sudo modprobe sonypi
> gksudo gedit /etc/modules
Now add this at the bottom of the file:
> [COLOR="Red"]sonypi[/COLOR]
Now turn off the Bluetooth device:
> sudo spicctrl -l 0
If you need a startup script for turning it off at boot, let me know. I set on up for you.

---

### Post by gwilliam on 2007-06-27
Thanks! Worked perfectly.

I added two menu items to the Applications menu, but when I call

> gksudo spicctrl -l 0

(even from the terminal) it doesn't have any effect. Any reason for this?

---

### Post by wieman01 on 2007-06-27
Try this script if you want to turn it off while your machine boots:
> gksudo gedit /etc/init.d/local_settings
Now add this (and save):
> spicctrl -l 0
Make it executable:
> sudo chmod +x /etc/init.d/local_settings
Create symbolic link:
> cd /etc/rc2.d
ln -s ../init.d/local_settings S99local_settings
'gksudo' is meant for graphical applications (Gnome) and not for command line. That's why it does not work.

---

### Post by gwilliam on 2007-07-06
I didn't realize it, but there's no need to run spicctrl as root... So the menu entries work as simply 'spicctrl -l 0' and 'spicctrl -l 1'

---

