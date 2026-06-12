---
title: "USB wifi adapter"
date: 2008-10-22
forum: Hardware
---

### Post by abahler on 2008-10-22
Hi I have a usb wifi adapter that I would like to use with ubuntu.
in the device manager it shows the connection speed is 480.0 Mbit/s so it is connected. How do I make ubuntu recognize it as a wifi connection?

---

### Post by icanfly0307 on 2008-10-22
okay, first things first. Could you post the model number of the usb adapter? Also, plug in the network adapter and post the output of lsusb.

What do you mean by "device manager"? Device Manager is from windows and unless you mean that, i don't think there is a device manager in ubuntu.

---

### Post by abahler on 2008-10-22
The adapter is ZyXel AG-225H. What is the lsusb?
There is a device manager in ubuntu if you go to: system menu/preferences/hardware information.

---

### Post by abahler on 2008-10-22
Is there a way to some how use the windows driver for the adapter?

---

### Post by icanfly0307 on 2008-10-22
google around on ndiswrapper. it's a way to make windows drivers work for linux.

ill be back in a couple of hours. until then, good luck! :)

PS: lsusb just lists the usb devices plugged into your system. Run it from the terminal like:

sudo lsusb

---

### Post by icanfly0307 on 2008-10-22
ok my bad. it seems that your network card is supported out of the box in ubuntu!!! :KS

so, my question is, what version of ubuntu are you using and are you using the Gnome desktop environment?

the info you provide to the questions above will take us a step forward and give us a clear insight on what to do next. :)

---

### Post by abahler on 2008-10-23
i'm using ubuntu fiesty 7.04. And yes i'm using gnome desktop.

---

### Post by icanfly0307 on 2008-10-23
ok, that makes everything easier. :)

since you're using gnome, look at the top right corner of the top menubar. It should have something like two screens and an X over them. that is the network manager applet. 

when you plug in your adapter, does it have any type of indication to show that it is working? maybe an led light or something? 

anyways, right click on the icon and you should see a list of networks within your range. click on your network and if you have a network key, enter it. that's it! you should be connected to your network within 20 secs or so.

let me know what happens...

PS. if you cant connect to your network, you may have to reboot and try again. thats what happened to my wg111t adapter.

---

### Post by abahler on 2008-10-23
I loaded ndiswrapper and it works!!!
Thanks for your time.

---

### Post by icanfly0307 on 2008-10-23
Great! Glad to know that it worked for you!:guitar:

---

