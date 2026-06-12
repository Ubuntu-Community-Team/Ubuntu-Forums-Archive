---
title: "WinTV USB"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by johnybot on 2006-01-28
Could not find any conclusive help on this...

how do i get the WINTV USB device to work using usbvision(how do i install it) or otherwise...

---

### Post by alpianon on 2006-03-17
Ubuntu 5.10 - driver usbvision 0.9.8.2 for Hauppage WinTV USB

1- Go to [http://usbvision.sourceforge.net/](http://usbvision.sourceforge.net/) and dowload the sources
(version 0.9.8.3 can't be compiled under Ubuntu 5.10, you have to download v0.9.8.2)

Here's the direct link for lazy people
[http://prdownloads.sourceforge.net/usbvision/usbvision-0.9.8.2.tar.gz?download](http://prdownloads.sourceforge.net/usbvision/usbvision-0.9.8.2.tar.gz?download)


2- Save it in your home directory


3- In Synaptic, enable the Universe repository


4- You need to install make, gcc-3.4, linux-headers; you need also "zapping" to watch tv.
You have to complile and install the module, then you may add a script to load it during startup

Open a console window, then type:
(please note that the character ` is not ' and it can be obtained with AltGr+' - anyway, you may just copy and paste the following lines)

sudo apt-get install make gcc-3.4 linux-headers-`uname -r` zapping
tar -xf usbvision-0.9.8.2.tar.gz
cd usbvision-0.9.8.2/src
sudo make
sudo make install
sudo modprobe usbvision
echo -e "modprobe usbvision\n" >usbvision
sudo cp usbvision /etc/init.d
cd /etc/init.d
sudo chmod 755 usbvision
sudo update-rc.d usbvision start 51 S .

( . at the end of the line is needed!)

4- Connect the WinTV USB card, and run zapping (it should be in the Audio&Video menu)

Cheers!
Alberto Pianon (Italy)

---

### Post by johnybot on 2006-03-17
Holy shat that is comprehensive. i shall try it now

---

### Post by johnybot on 2006-03-17
THANK YOU THANK YOU THANK YOU
works great exept Zapper and TVtime freeze the whole system :O
XawTV works awesomely

---

