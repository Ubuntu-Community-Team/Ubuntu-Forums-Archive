---
title: "Toshiba Laptop Network Woes"
date: 2008-08-17
forum: Hardware
---

### Post by fightforlife on 2008-08-17
:(I have a Toshiba Satelite A105-S2712. I cannot get Ubuntu to connect to a wired or wireless network. I have installed every versions I could find. I am pretty sure it is not the programs, It is something in the laptop. Here's why. It will connect with Windows XP which it came with. I installed Virtual Box in windows and then Ubuntu on the VB. The network works perfectly both wired and wireless. But, when I install Ubuntu and have it dual boot, it will not get the network. I have downloaded what some said were drivers for the network, but I don't know how to install then, besides that I don't think that would help. Any ideas? The network thing is Intel PRO/Wireless 2200BG. I have another laptop, and it connects to Ubuntu right out of the box. Any suggestions is appreciated. Oh, and by the way there are no settings in the BIOS to set for that.

HELP Please....

---

### Post by oceallaighm on 2008-08-18
I have a Toshiba L300D-10Q. To the best of my knowledge both wired and wireless cards work in Vista. 

Note it is possible for Ubuntu running in VirtualBox to be able to access the network via the host, as it does not use a card specific driver in the guest.

In my case when I boot from a Ubuntu 8.04 Live CD, I must disable the internal network card in the bios as Ubuntu will crash if I don't do this. Note in my case both of the network cards are Realtek.

I have not tried the more recent Ubuntu 8.04.1 iso image, perhaps it supports my card, I don't know if this is the version that you used. I used an external usb ethernet connection which Ubuntu 8.04 recognised to get around my problem.

---

### Post by purefan on 2008-09-16
Does anyone know how to fix this? im having the same problem and as accurate as oceallaighm's reply is I cant see the fix here :(

---

### Post by fightforlife on 2010-02-23
My problem went away after I installed an upgrade 9.04 the wireless and wired drivers are working perfectly on that older Toshiba Laptop. I am happy now, and also with the newer 9.10 that works nicely. I haven't found much of anything that it can't do now. Thanks to everyone who replied. You all are the greatest support team ever!

---

