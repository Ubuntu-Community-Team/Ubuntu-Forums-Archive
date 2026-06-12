---
title: "Ubuntu + Wireless Internet + Belkin USB Connector"
date: 2008-08-30
forum: General Help
---

### Post by Jinkzt3r on 2008-08-30
I was curious, is there any way to get my Belkin Wireless USB Connector to work via Ubuntu? If not I have no way to connect to the Internet T_T, seems I don't have a working network card so an Ethernet cable won't work, and the only thing that will enable me to get to the internet is my Belkin USB Connector.

I can't install the software, and when I do try to access the Internet by putting in my Router name/wep key, it won't connect.

Any one help? T_T Sorry, Ubuntu noob here :P.

---

### Post by jonian_g on 2008-08-30
Of course.
Put the ubuntu cd in your drive and open a terminal and type:

```
sudo apt-get install ndisgtk
```

Alternatively you can find the ndisgtk package in Synaptic Package Manager and install it.

Remove the ubuntu cd and put in the cd with the windows drivers that came with your wireless card.

Then go to System>Admin>Windows wireless drivers and click on Install new drivers. Navigate to the folder in the cdrom that contain the drivers and select the .inf file and then click install and you are done.

To connect to your network left click on the network icon (top-right of the screen) and you will see a list of the available wireless networks, select the one you want and you will be prompted to enter the wep/wpa key.

EDIT: If you use 64bit Ubuntu then the windows drivers for your wireless usb must be for 64bit.

---

### Post by Jinkzt3r on 2008-08-30
> **jonian_g said:**
> Of course.
Put the ubuntu cd in your drive and open a terminal and type:

```
sudo apt-get install ndisgtk
```

Alternatively you can find the ndisgtk package in Synaptic Package Manager and install it.

Remove the ubuntu cd and put in the cd with the windows drivers that came with your wireless card.

Then go to System>Admin>Windows wireless drivers and click on Install new drivers. Navigate to the folder in the cdrom that contain the drivers and select the .inf file and then click install and you are done.

To connect to your network left click on the network icon (top-right of the screen) and you will see a list of the available wireless networks, select the one you want and you will be prompted to enter the wep/wpa key.

EDIT: If you use 64bit Ubuntu then the windows drivers for your wireless usb must be for 64bit.

Is it supposed to say 

> E: Couldn't find package ndisgtk

in the terminal? I also didn't see the file name inside the Synaptic Package Manager either.

---

### Post by Jinkzt3r on 2008-08-30
Solved, man. I suck!

---

