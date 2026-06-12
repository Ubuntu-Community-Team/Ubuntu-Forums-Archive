---
title: "Canon A610 not recognised!!!"
date: 2005-11-19
forum: General Help
---

### Post by galactus51 on 2005-11-19
Hello folks!! 

I have a brain new Canon A610 and When I try to import photos in Ubuntu 5.10 the folowing errors occurs:

An error occurred in the io-library ('Error not especified'): Could not query kernel driver of device.


OR


PTP protocol error  

Any Ideas guys?

---

### Post by mykey on 2005-11-19
It simply means that your camera is too hip for your kernel and it does not know which driver to use for it.

Try to set a different canon driver in the options of the viewer software.

good luck

---

### Post by galactus51 on 2005-11-19
:(

Bad luck!!!

There's no support for my Camera in Linux. Well, that's it. Bye, bye Linux. :(

---

### Post by metoo on 2005-11-19
You can use a card reader.

Funny, I just tried with my older Canon:
lsusb sees the camera, but no driver for it was loaded/feels to be responsible. I never noticed that, as I always use an USB card reader.

---

### Post by glib on 2005-11-19
I picked up a usb 2.0 cardreader a few weeks back for $20CAD. I just put in the card and it automounts and I can copy my pictures off from there.

---

### Post by galactus51 on 2005-11-21
Ok Guys. I just did that. But Ubuntu doesn't recognise the Card Reader. :(

I'm using Kurumin Linux to see my photos.

---

### Post by metoo on 2005-11-24
I hate to correct myself ;-) but read in the forum about gtkam today.
Plugged in the Canon S50 via USB cable and selected camera - add... it was immediately recognized (normal mode).
Same in digiKam (KDE program).
Both probably based on gphoto2.

The A610 is not in the list, but may be an older model is compatible...

Try importing pictures with gtkam or digikam.

For the usb card reader:
sudo lsusb gives you the overview of detected usb devices. External card readers are usually OK (in opposite to build in once).

---

### Post by marcool on 2005-11-27
I have the same camera, and ubuntu Breezy with Kde 3.4, gphoto2, and digikam.
And the camera works very well, I can download all my photos and video without any problem.

When I plug the camera, appear an icon on the desktop (Kde)




Bye.

---

### Post by Joey French on 2005-11-27
Same here. I am using a new Canon as well. It is shocking how well this ubuntu handles this camera. Simple- plug in usb, import images, done.

---

