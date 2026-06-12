---
title: "TV card &amp; webcam"
date: 2008-12-28
forum: Hardware
---

### Post by aL3xandar on 2008-12-28
Hi there,

for a while I'm using SAA 7134 chipset-based TV card... It works perfectly, but now I have problems in installing webcam... every time I start some webcam app, as an output, I get my recent TV station...

my tv card is located in /dev/video0

is there any chance that I can put my webcam to /dev/video1 or smthng..
Help, anyone?!

---

### Post by fireman300 on 2009-01-25
Generally your webcam should automatically assign itself to /dev/video1 since your capture card is at /dev/video0. But nearly all of the webcam programs out there that I have tried default to video0. Read the man page and look to see if there is a flag to set so that it reads from video1 instead. ex: ```
camorama -d /dev/video1
```
Hope this helps.

---

### Post by sdennie on 2009-01-26
You can create udev rules to explicitly name the devices.  Your configuration may be different but, here is an example of what mine looks like:

```

$ cat /etc/udev/rules.d/81-video.rules 
SUBSYSTEMS=="usb", ATTRS{product}=="Laptop Integrated Webcam", KERNEL=="video*", NAME="webcam"
SUBSYSTEMS=="usb", ATTRS{manufacturer}=="Pinnacle Systems GmbH", KERNEL=="video*", NAME="tvtuner"

```

That gives me /dev/webcam and /dev/tvtuner instead of /dev/video*.  More information on writing udev rules can be found here: [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

