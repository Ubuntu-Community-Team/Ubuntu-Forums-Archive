---
title: "broadcom wireless issues"
date: 2006-03-11
forum: Hardware &amp; Laptops
---

### Post by omni814 on 2006-03-11
I have a Dell Laptop where I have installed Breezy Badger and am having issues getting the wireless lan to install.  I have the Dell 1370 internal wireless with a Broadcomm 4318 chipset.  I have installed the windows driver using ndiswrapper and have had no luck getting Ubuntu to reconise the card in the network config pane.  Any help would be appreciated, my lspci follows:
[COLOR="SeaGreen"]
lspci

...
0000:02:03.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

lspci -n

...
0000:02:03.0 0280: 14e4:4318 (rev 02)

ndiswrapper -l

Installed ndis drivers:
bcmwl5  driver present, hardware present'[/COLOR]

I'm a linux noob, so please be explicit if you ask me to do commands, thanks.

---

### Post by DavidFourer on 2006-05-12
omni814--
I have the same dell and exactly the same wireless lan broadcom 4318 chipset and I getting exactly the same results.  
ndiswrapper -l : bcmwl5 driver present, hardware present
sudo modprobe -v ndiswrapper gives no fault
can't seem to find or turn on hardware
No wlan0 in system>admin>networking, no light on, nothing in the bios that helps.

---

