---
title: "Wi-fi driver on HP netbook"
date: 2012-06-06
forum: Hardware
---

### Post by misterconrad on 2012-06-06
I bought an HP netbook (model number M215-IAA16180G01).
I installed Ubuntu 12.04 and it works except for the lack of Wi-Fi drivers. The internet card is Broadcom BCM4312. How can I get the necessary driver? Might I add that on top of not having internet with this machine, it also does not have a disc drive. Is there a way I can download the driver on another computer and put it on a flash drive or something? Thank you.

---

### Post by rolltide101x on 2012-06-06
Plug an ethernet cord into it.


[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

On Ubuntu, you will need headers and tools.  Try these commands: 

apt-get install build-essential linux-headers-generic 

apt-get build-dep linux

---

### Post by misterconrad on 2012-06-06
I also forgot to mention that it does not have an Ethernet port. My only option I believe is somehow getting the driver onto a USB drive and installing it as such.

---

### Post by ahallubuntu on 2012-06-06
Did you try installing Additional Drivers, with the USB drive that you originally used(?) to install plugged in?  Sometimes Additional Drivers (proprietary drivers) for wireless cards can simply be installed from the original CD (or USB drive version of the CD) without any internet connection.  That has worked for me with a Broadcom wireless card at least once.

If you plug in your original bootable Ubuntu USB flash drive, you may be able to re-add its repositories back in so a Broadcom driver may be found:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

(Scroll down to CD/DVD )

---

