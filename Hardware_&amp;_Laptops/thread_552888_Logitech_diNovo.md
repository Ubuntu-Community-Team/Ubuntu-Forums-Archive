---
title: "Logitech diNovo"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by Riis on 2007-09-17
I have a problem with my Logitech diNovo Media Desktop Laser and Ubuntu 7.04.

When the computer boots, the keyboard and mouse stops working.
It wont start to work again before I unplug it for a number of seconds and the plug it in again.

How can I solve this?
It sounds like an bluetooth problem, but the advices i've found on the net did not help.

Thanks in advance.

---

### Post by Riis on 2007-09-17
I guess I need to learn to use the search-function before asking :)

I will try this one: [http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057)

---

### Post by chris_c28 on 2007-09-17
If you are using the bluetooth dongle from Logitech and have a bluetooth-enabled laptop, you may need to uninstall bluez-utils.

---

### Post by Riis on 2007-09-17
> **chris_c28 said:**
> If you are using the bluetooth dongle from Logitech and have a bluetooth-enabled laptop, you may need to uninstall bluez-utils.It's the complete diNovo-kit I have, so I am using the logitech bluetooth dongle. But it's for my workstation - not my laptop.

I tried to follow the guide (mentioned in the link in post #1), but the first codeline gives an unexpected result:
```
hcitool scan
Device is not available: No such device
```
How can that be?

---

### Post by Randulf on 2007-10-18
Hi!
I have exactly the same problem with my dinovo.
Have to unplug and plug it back in before I can log in, but I can enter setup etc with it.
Also get the same message:
user@computer:~$ hcitool scan
Device is not available: No such device

Installed:
bluetooth
bluez-btsco
bluez-cups
bluez-gnome
bluez-pin
bluez-utils
gnome-bluetooth

but still the same message

---

### Post by FunkWarrior on 2008-05-09
Same problem for me on a fresh hardy installation...

My Logitech wirelesshub bluetooth is not recognized as a bluetooth device??

---

### Post by laluz on 2008-05-11
Just my vote here, same problem with hcitool not showing any devices. Also I do have the problem with the reconnection, but only since I have upgraded to Hardy. With Gutsy, the was no problem with the KDE login screen. Now I have to turn off/on the keyboard itself to be able to log in.
My ultimate goal is to be able to use the logitech dongle to work with the a2dp headphones.

---

