---
title: "ran madriva ok but can't run ubuntu"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by mpflacco on 2009-01-11
i have a dell dimension 2400 (integrated graphics) 500 MB RAM, 100g hard drive. Previously installed and ran mandriva without problem. during installation repartioned drive-ubuntu only.

From installation cd:
"Try Ubuntu without any change to your computer" runs ubuntu without problem
Test memory is ok
Check CD for defects is ok
installation proceeds without error messages
boot seems ok, but hangs with a beige screen and mouse cursor (which still moves with mouse) but num lock and caps lock frozen.

advice please!

---

### Post by kranny on 2009-01-12
This might help you
[https://answers.launchpad.net/ubuntu/+question/51790](https://answers.launchpad.net/ubuntu/+question/51790)

---

### Post by mpflacco on 2009-01-13
I tried to follow these instructions. sure enough i got the error

"if it gives you an error that it can not cone:ct and suggests you run sudo apt-get update than fix your network to use DHCP"


When i ran:    sudo nano /etc/network/interfaces  My file didn't look like the one below

# The primary network interface - use DHCP to find our address
auto eth0
#iface eth0 inet dhcp

instead I had:

auto lo
iface lo inet loopback

I tried changing to the one above (with eth0) and took out the "#" but it didn't make any difference. i still couldn't connect for updates. of note, when i successfully ran ubuntu from the CD, internet connectivity was fine!

any suggestions?

---

### Post by abn91c on 2009-01-13
if you have a wired broadband at the prompt do ```
dhclient eth0
``` to activate the connection. the dimension 2400 has the intel 845 video card, compiz is not compatible with it, do ctr+alt+f1 then at the prompt ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

---

### Post by mpflacco on 2009-01-14
That was the key!

it wasn't entirely clear when to press ctrl-alt-F1 but after a few tries I got the prompt and typed


dhclient eth0 (needed sudo first to make it work)

sudo apt-get remove compiz
sudo apt-get remove compiz-core

then i reverted to the previous instructions and typed:

sudo apt-get upgrade
sudo dpkg-reconfigure xserver-xorg

rebooted and ubuntu seems to work fine!

**Thank you both very much for your help!** If you have time could you explain what exactly this was all about??

---

