---
title: "My webcam doesn't work"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by ostvarivanje on 2007-07-15
I have a webcam with microdia chipset.
In lsusb command I have this result for the webcam:

Bus 002 Device 003: ID 0c45:627b Microdia

What can I do to work it? In Kopete I have a black screen in section devices

---

### Post by w4ett on 2007-07-15
Try Camstream in Synaptic ...if it does not work, it will probably need a driver or patch .

---

### Post by ostvarivanje on 2007-07-15
I installed camstream but doesn't work my cam. Any other solution?

---

### Post by w4ett on 2007-07-15
I searched the string

0c45:627b Microdia ubuntu

In google...most returns are not in English, but do mention Kernel patches.  You might want to search it too.

---

### Post by IntuitiveNipple on 2007-07-15
A quick Google search for "0c45:627b" seems to show that there is currently no linux driver for this device.

---

### Post by Wiebelhaus on 2007-07-15
Totally unrelated but I read a feed about a doctor in the Netherlands that took the time to write like 3000 different drivers for webcams...


lol , he owns.

---

### Post by w4ett on 2007-07-15
> **sx66gns said:**
> Totally unrelated but I read a feed about a doctor in the Netherlands that took the time to write like 3000 different drivers for webcams...


lol , he owns.

He must have a lot of time on his hands  LOL   :)

---

### Post by srv104 on 2008-07-01
I have the 627b on a lenovo z61t. [SIZE="5"]Heres how to make it work![/SIZE]

Webcam 
The laptop has a Microdia based integrated webcam (lsusb tells 0c45:627b). 


Microdia webcam kernel driver project
 
There is a Microdia project working on an Open Source driver by reverse engeneering (usb sniffing mainly) and some little documentation.
The project has a google group*:
[2]. You can follow the development via git-web*: 
[3] If you want to test the driver (still in development, use at your own risks): You need to install git first: 

**sudo apt-get install git-core gitk git-gui git-doc curl**

Then clone the "microdia" repository: 

**git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git) **

Then build the driver:
 
[B]cd microdia

make
[/B]
Now load some necessary modules before the microdia driver: 

**sudo modprobe videodev**

Finally, load the microdia driver (`rmmod` to unload it): 

**sudo insmod microdia.ko**

You can test the webcam with Ekiga, or with VLC: 

vlc v4l://*:v4l-vdev="/dev/video0"
or mplayer: 
[B]
mplayer -tv device=/dev/video0:driver=v4l:input=1:width=640:height=480 tv://1 -zoom[/B]

Worgk great for me! another fun program to use is "Cheese" which is like photobooth for mac. You could also write a small script and autoload the drivers on startup. Good Luck!

---

