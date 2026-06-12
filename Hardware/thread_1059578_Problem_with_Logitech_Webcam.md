---
title: "Problem with Logitech Webcam"
date: 2009-02-03
forum: Hardware
---

### Post by Djalmahal on 2009-02-03
Hi,

today I bought a Logitech QUickcam connect, which the wiki.ubuntu website says works (I checked that before I bought it). Fact it, it isn't recongized by my Ibex.

Now the output of lsub is
andreas@andreas-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 011: ID 046d:089d Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So it finds it on Bus 002, but the id should be 0x08d9 not the 089d that it gives, that is the id for the Logitech Quickcam e2500 which doesn't work under Ubuntu

Another output of a commandline is 

andreas@andreas-laptop:~$ lsmod | grep gspca
andreas@andreas-laptop:~$ sudo modprobe gspca
[sudo] password for andreas: 
FATAL: Module gspca not found.

I don't know too much about command line, can someone advice me?
I also found websites which tell you you have to modify the spca driver for the quickcam e2500, but I don't know if I should go ahead.

I installed the logitech program in a virtual windows machine and the logitech software and webcam works, skype crashes.

THanks a lot for advice
Andreas

---

### Post by Crafty Kisses on 2009-02-03
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2) To test your webcam you can do this: There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by Djalmahal on 2009-02-03
Ekiga has the bouncing logo, also cheese and webstream and skype don't find anything, ekiga doesn't give me any other option than "no device found" in preferences with v4l1 and v4l2

---

