---
title: "Drivers for webcam?"
date: 2008-05-22
forum: Hardware
---

### Post by ubockto on 2008-05-22
In particular, the logitech quickcam pro 5000, are there any?

---

### Post by linuxwizard on 2008-05-22
Have you tried using your webcam ? Alot of Logitech webcams will works out of the box. Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If the webcam does not work post the results of the command > lsusb

---

### Post by ubockto on 2008-05-22
I am in the preferences window, and on the video device, it says that no devices have been found, I have clicked the "Detect Devices" button, but that doesnt detect anything

How do I find the equivalent of Window's Device manager??

---

### Post by benevolent on 2008-05-22
I have a logitech webcam, and it's working fine..

I followed this guide: [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) .


It's working with Amsn and cheeze :-)



edit: Actually I only installed **easycam**

> You need to add the following repository to your source list
**deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main**

Then you need to update the packages
**sudo apt-get update**

and install the easycam package
**sudo apt-get install easycam2**

---

### Post by ubockto on 2008-05-22
This is what it says when I put lsusb into the terminal command line

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:00b0 Microsoft Corp. 
Bus 001 Device 002: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 001 Device 001: ID 0000:0000  

there is nothing for the webcam I have, unless it is faulty

---

### Post by linuxwizard on 2008-05-22
Do you have the cam plugged into a hub ? Use a port on your computer or try using a different port on your computer. Than try > lsusb

---

### Post by ubockto on 2008-05-22
> **linuxwizard said:**
> Do you have the cam plugged into a hub ? Use a port on your computer or try using a different port on your computer. Than try > lsusb

yup, its plugged in the usb and thats what it came up with

---

### Post by linuxwizard on 2008-05-22
Have you used that webcam before ? Do you have another computer you can test it on to see if it does work ? Using a hub can cause issues with a webcam. If you tried different ports directly on your computer and your system does not detect it, you need to figure out if their is something wrong with the webcam.

---

### Post by ubockto on 2008-05-22
> **linuxwizard said:**
> Have you used that webcam before ? Do you have another computer you can test it on to see if it does work ? Using a hub can cause issues with a webcam. If you tried different ports directly on your computer and your system does not detect it, you need to figure out if their is something wrong with the webcam.

the only other computer I have got that it is known to work with, currently is a XP pc, it worked then, but the xp pc is not working anymore until I find my installation disc, which I will try find over the weekend, lol

---

### Post by troupa on 2008-05-23
plug in the webcam, wait say, 20 sec, and in a terminal do:

dmesg

is there any output at the end of that about new USB device found, etc?

---

### Post by ubockto on 2008-05-23
Nothing at all, it only says something about my keyboard and mouse

---

