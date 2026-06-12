---
title: "Ralink rt2870 driver / wireless usb adapter"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by brandon82 on 2009-01-16
i just bought a Belkin wireless USB adapter, which uses rt2870 driver. I'm fairly new to Ubuntu, and need some detailed help/instructions as to how to make this work. Any help would be greatly appreciated. 

Thanks
-brandon-

---

### Post by ssorc on 2009-01-16
Brandon,

Some models of the MSI Wind U100 also use the Ralink RT2860 driver, so have a read of the instructions in the "Ralink RT2860 wifi" section of the following page and see if that works (I can not be 100% sure as there may be a subtle difference with the Belkin USB adapter).

[https://help.ubuntu.com/community/MsiWind](https://help.ubuntu.com/community/MsiWind)

- ssorc

---

### Post by brandon82 on 2009-01-19
I found the correct driver from the ralink site (rt2870) and have it saved just on the desktop of the machine in question. I guess I just need instruction on where to go from here. Ubuntu is still somewhat foreign to me still at this point. I am using 8.04

-brandon-

---

### Post by ssorc on 2009-01-19
Brandon, 
I don't have a 8.04 system in front of me, so take this with a grain of salt, but the following should work:

1. Make sure you have the build-essential package and the linux headers for your kernel installed

sudo apt-get install build-essential linux-headers-$(uname -r)

2. Follow the instructions listed at this previous forum posting:

[http://ubuntuforums.org/showthread.php?t=960642]("http://ubuntuforums.org/showthread.php?t=960642")

- ssorc

---

### Post by brandon82 on 2009-01-19
Ok. recieving an error stating that build essentials / linux headers not installed.. and cannot get online to reslove this.....aargghhh

-brandon-

---

### Post by brandon82 on 2009-01-19
I managed to get the wireless usb working by using the windows drivers provided on the install cd using ndiswrapper / ndisgtk. I've read both good and bad about going about it this way, but it seems to be working ok. Thanks for all your help.

-brandon-

---

