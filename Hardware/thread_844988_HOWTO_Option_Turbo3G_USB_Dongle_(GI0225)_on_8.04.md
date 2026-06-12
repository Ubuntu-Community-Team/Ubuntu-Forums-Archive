---
title: "HOWTO: Option Turbo3G USB Dongle (GI0225) on 8.04"
date: 2008-06-30
forum: Hardware
---

### Post by Dacobi on 2008-06-30
The Option GI0225 Turbo3G USB dongle will when first inserted show up as an usb-storage device.
Using the program [_usb_modeswitch_]("http://www.draisberghof.de/usb_modeswitch/") you can change the state of the device to usb modem.
The following driver setup installs usb_modeswitch and updates udev rules.d
so that all configuration is done automatically when the dongle is inserted.

[_Option_GI0225_3G_driverSetup.run_]("http://juvul.com/Option_GI0225_3G_driverSetup.run")

The installation is simple. Download the file, unplug your dongle and run the installer (sh <filename>).
The dongle can now be inserted and should be present as /dev/ttyUSB2
You can now configure your connection using gnome-ppp, wvdial or simply in network settings.
The following [_wvdial.conf_]("http://juvul.com/wvdial.conf") works with the phone number *99# and "internet" as APN

Enjoy :)[COLOR="black"][/COLOR]

---

### Post by jpeddicord on 2008-07-01
Moved from Tutorials and Tips: Not comprehensive; a shell script installer does not constitute a tutorial.

---

### Post by th00ht on 2009-01-05
Cannot find the thread there. can someone post a link the right thread?

---

### Post by Dacobi on 2009-01-05
> **th00ht said:**
> Cannot find the thread there. can someone post a link the right thread?

This is all the thread there is :)

BTW: 
In 8.10 my Option USB Dongle is detected automatically and a config window pops up where I can enter internet settings.

This didn't work however but that may be because I already installed the driver setup sh file...

/Dacobi

---

### Post by th00ht on 2009-01-12
> **Dacobi said:**
> In 8.10 my Option USB Dongle is detected automatically and a config window pops up where I can enter internet settings.

Thanks Dacobi

I did a reinstall of 8.04 (after trying easypeasy1 which is just not ready) and inserted the Option card in my 901. I cannot see an tty entry in /dev and in dmesg I can see that it is recognized as usb-storage device, which incidently is correct as it is also a flash memory card. And an entry 

hso: /home/adamm/git/ubuntu-hard-lum/debian/build/build-eeepc/wireless/hso.c : 1.3 Option Wireles

suggests that it is modem as well. It did not assign a modem port though.

---

### Post by Philip390 on 2009-07-18
Huge bump on this one, I just installed Jaunty Jackalope on my laptop with Wubi and I tried my GI0225 confident that it would work but it didn't. So I checked around some forums and found this, and since it seems to work for you I decided to try it, but the link is broken :( I wonder if anyone has the file and is willing to rapidshare it or something like that? I would be eternally grateful! 
/Philip

---

### Post by Philip390 on 2009-07-28
Trying again, i cant seem to find any other way to do this..

---

