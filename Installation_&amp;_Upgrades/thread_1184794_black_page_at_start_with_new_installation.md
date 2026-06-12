---
title: "black page at start with new installation"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by lilmale1 on 2009-06-11
i intalled server on my server 10x12 mobo
im sure its a server, it has pci x slots for scsi 

i only have an ide hard drive for this computer

does that matter if im installing ubuntu 9 server on the computer
with an ide type

i aslo get the black page thats why im thinking its that ide drive think since desktop works but not quiet for my drivers
modules.

so im using server ubuntu 9 and im on the boot black page

i already tried startx with user name and password

but says to install xinit and i did so now im sitting here wondering why it wont start the ubuntu 9 server

can someone help with it since i tried installing it 3 times and still the same thing

---

### Post by dstew on 2009-06-11
The server installation is a command-line only interface. It looks like you want to install a desktop (startx makes no sense if you have a server only installation). If so, and if your computer is connected to the internet, do```
sudo apt-get install ubuntu-desktop
```

---

