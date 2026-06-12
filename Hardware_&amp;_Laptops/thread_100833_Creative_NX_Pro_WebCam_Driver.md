---
title: "Creative NX Pro WebCam Driver"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by oly on 2005-12-08
download the latest version of the spca5xx driver
[http://mxhaard.free.fr](http://mxhaard.free.fr)

extract the file with the archiver tool or on command line.

Then cd into the director in a terminal and type.

export CC=gcc-3.4
make
sudo make install 
sudo modprobe spca5xx

then fire up gnomemeeting and you should be able to get video through by configuring your camera in gnomemeetings preferences.

type dmesg in a terminal, to see if the driver is loaded and your camera detected.

---

### Post by wolfiedk on 2006-02-14
Hi !

Im a newbie when it´s all about Linux/Ubuntu.....

Im trying to install the Creative NX Pro driver like you discribed.

I think im all done with the installing, but when i try to start a program up to view the webcam, my machine freeses...

When Im using dmesg command it displayes that my webcam is installed.

Is it possible to get a deeper discribtion ?

Thanks...


Morten Madsen
Denmark

---

