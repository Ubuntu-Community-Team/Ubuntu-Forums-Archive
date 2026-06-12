---
title: "Got a webcam driver, got a webcam...how do i get the two to work?"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by letmein on 2007-06-30
ZC0301 Z-Star Microelectronics Corp. = Webcam

Got the driver for my webcam, all downloaded and set to go....how do i get it to work?

---

### Post by speaker219 on 2007-06-30
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
might help you.

---

### Post by letmein on 2007-06-30
I've used this page already, installed easywcam, followed the instructions etc...easyweb works, apparently, however the camera does not, i've also installed camorama

Camorama error: Counld not connect to video device (dev/video0). Please check connection

EasyCam output: This software, EasyCam, is still in test status.  If your webcam is not detected, it may be not compatible with autodetection yet.  Thank you to read the file easycam generated on your desktop.

Easycam does indeed show my webcam, i just assume it doesn't have the drivers that are needed..i've done a search and found those drivers..which brings me back to my original question, now that i know my camera type and i have the drivers (linux) drivers to run it, how do i install them?

---

### Post by tarasbulba on 2007-07-02
Did you installed gspca driver? If it's installed, then try this command:

> sudo modprobe gspca usbgrabber=1
If your webcam shows up, then go to your /etc/modprobe.d directory and add this command at the end of your "options" file:
> options gspca usbgrabber=1
It should loaded at boot time and you can use your webcam.
If those commands don't work try :
> force_rgb=1
instead of usbgrabber=1 command.Hope thats help

---

### Post by letmein on 2007-07-02
gspca driver is indeed installed, tried the commands, they did not work...i tried the camera on a windows system thinking that perhaps there was an hardware problem with the camera, camera works fine.  Any other ideas?

---

### Post by chele on 2007-07-02
> **letmein said:**
> gspca driver is indeed installed, tried the commands, they did not work...i tried the camera on a windows system thinking that perhaps there was an hardware problem with the camera, camera works fine.  Any other ideas?Sounds like you picked up an unsupported webcam. You have the drivers already installed and it still does not work. Can you return it?

---

### Post by letmein on 2007-07-05
Not likely able to return it, considering I bought it in another country :-(

---

### Post by yorkie on 2007-07-05
Hi I had the same problem  Camorama error: Counld not connect to video device (dev/video0). Please check connection is there abutton on your webcam if so press it and webcam may work
it worked for me.

---

