---
title: "how do i install bluetooth drivers"
date: 2015-04-13
forum: Hardware
---

### Post by Olivia_Zane on 2015-04-13
i just did a fresh install of ubuntu 14, been using windows 7
before my bluetooth was working, but as soon as i installed ubuntu my blue-tooth is not working
i am new to ubuntu /linux
i tried using the ubuntu software center but there is nothing

---

### Post by dino99 on 2015-04-13
similar question: [http://askubuntu.com/questions/490346/bluetooth-not-working-in-ubuntu-14-04-lts](http://askubuntu.com/questions/490346/bluetooth-not-working-in-ubuntu-14-04-lts)
a bit old now, but may help: [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

by default the ubuntu installation might have detected your hardware, then installed the required packages;  but check them anyway
( 'synaptic' is a friendly app to deal with packages, install it : sudo apt-get install synaptic (from a terminal)

---

### Post by Pilot6 on 2015-04-13
Please give output of

lsusb

Drivers are in linux kernel. But if you have a new device it may not be supported yet.

---

