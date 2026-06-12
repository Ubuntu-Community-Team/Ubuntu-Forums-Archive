---
title: "How do I stop a kernel module loading at boot?"
date: 2013-09-14
forum: Hardware
---

### Post by Merrattic on 2013-09-14
I believe I have a problem with the order/timing of kernel modules loading, I think my r8169 module is blocking my dvb_usb_af9015 (and possibly gspca_main). If I disable my onboard LAN in the bios, my dvb stick comes alive, if I enable the onboard LAN, dvb stick module fails. (oddly if I boot to Windows7 then reboot back to Xubuntu it works)

Unloading and reloading after boot up does not work, it is too late by then....

So, how do I stop a kernel module loading at boot?

---

### Post by tgalati4 on 2013-09-14
You generally blacklist them.  There are a few ways to do it.  Check out /etc/modprobe.d/blacklist.conf and [https://help.ubuntu.com/community/Loadable_Modules#Blacklisting_Modules](https://help.ubuntu.com/community/Loadable_Modules#Blacklisting_Modules).

---

### Post by varunendra on 2013-09-15
Like tgalati4 suggested, you blacklist a module to stop loading it at boot time. To blacklist r8169 -
```
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

If it solves your problem, you can add the following line to your /etc/rc.local file (above "exit 0" line) to automatically load it again after a certain amount of time (you must open the file with 'gksu' to have root access to be able to edit it) -
```
sleep 30 && modprobe r8169
```
*(It is VERY IMPORTANT that you insert this line ABOVE the last line that says - "**exit 0**". That file must end with this "exit 0" line)*
The number 30 is time in seconds to wait before loading the module. Change it to whatever works for you.

---

### Post by Merrattic on 2013-09-28
Thanks will give this a go and report back

---

### Post by Merrattic on 2013-09-30
Well the blacklisting worked fine, but didn't fix my problem :(

---

### Post by Merrattic on 2013-10-15
Resolved!
 Not a software bug as such, turned out to be the Intel xHCI mode  setting in the bios for USB for my Asus Z87M-PLUS motherboard. Default  setting was Smart Mode. This made all usb ports usb 3.0 and/or "better"  than 2.0, meaning my webcmas wouldn't play nicely. Changing the bios  setting to Disabled saw the camera fire up instantly, along with routine  connection of my DVB USB stick.
 Other option to try is Auto, and EHCI Hand Off to Enabled

---

