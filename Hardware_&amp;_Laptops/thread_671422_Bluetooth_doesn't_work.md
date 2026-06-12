---
title: "Bluetooth doesn't work"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by audunmb on 2008-01-18
I got an Asus a6km laptop with built-in Bluetooth, but I can't get it too work in Ubuntu (works in Windows). I've installed all the bluetooth packages (bluez-util, bluez-gnome, etc), both for KDE and Gnome.

running hcitool dev just gives me 
Devices:

and nothing more. I really don't where to start troubleshooting this. The help files (at help.ubuntu.com) gives no clue how to solve this and since I don't really know what's wrong I don't know what to search for. Any help will be appreciated.

---

### Post by DrMega on 2008-01-18
I had to install Gnome Bluetooth server to make it work on mine (sorry, I can't recall the exact package name but if you search for 'bluetooth' in synaptic, you'll see it.

---

### Post by linuxwizard on 2008-01-18
Look over these
[https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6Km](https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6Km)

[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/148712](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/148712)

---

### Post by intense.ego on 2008-01-18
I have something called "Bluetooth File Sharing" and it does the job for me

---

### Post by audunmb on 2008-01-20
Linuxwizard, thanks, but I couldn't really figure out anything more from the links you gave me. The bug in bluez-utils is one step beyond where I got to, since it describes a problem where the laptop does connect to other units but quits after a short while. I got no connection at all, no pairing, no response at all.

It seems to me that Ubuntu doesn't recognize that I have BT on my computer at all. 

(DrMega and Intense-ego: I have all the packages installed, they just don't work).

---

### Post by linuxwizard on 2008-01-20
The biggest thing I was looking at is from here > [https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6Km](https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6Km) > it show Bluetooth working only 20% > meaning not very well supported their are issues with it. You may not get it working.

---

### Post by huck416 on 2008-01-25
Hi, 

Disregard all this.... See bottom of post...

Just got a Logitech V470 BT mouse and cannot get it to work with Gutsy 7.10 on a Dell Inspiron 1521. Output from hcitool scan is: ```
~$ hcitool scan
Device is not available: No such device

```
In the GUI for system settings, services, bluetooth is shown as start at boot but is not running. However, ```
$ sudo /etc/init.d/bluetooth restart
``` shows OK. I tried sticking the MAC addr in /etc/default/bluetooth. My bluetooth file reads as follows:

# Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
#HIDD_OPTIONS="--master --server"
HIDD_OPTIONS="-i 00:07:61:9A:DC:57 --master"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.

There's a bunch more after but I don't think it's relevent. Then I would restart bluetooth but still nothing. BTW, bluetooth is enabled in the bios. Any help would be appreciated.

UPDATE:

OK, it might help if there's actually a bluetooth card in the machine!!:roll: The advertising led me to believe there was a card when I bought it but guess not. My bad. More to follow when I get a card. :lolflag:

---

### Post by audunmb on 2008-01-29
hmm.. seems like the BT hardware on my laptop isn't supported on Linux, like so much else on this model. I wish that I've checked that a bit more closely before buying it.

---

### Post by huck416 on 2008-02-08
Received the Dell 355 2.0 bluetooth internal card yesterday, took 5 mins to install, booted up and with one push of the 'connect' button on the mouse, it was working. That easy. I haven't got the side-to-side function of the scroll wheel working yet so if anyone has ideas on how to configure mouse buttons, it would be appreciated. :KS

The mouse is a Logitech V470 on a Dell Inspiron 1521.

---

### Post by linuxwizard on 2008-02-08
huck416
Look over this, see if this will help you.

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

