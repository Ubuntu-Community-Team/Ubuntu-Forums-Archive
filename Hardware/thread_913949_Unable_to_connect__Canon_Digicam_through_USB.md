---
title: "Unable to connect  Canon Digicam through USB"
date: 2008-09-08
forum: Hardware
---

### Post by yajuvendra on 2008-09-08
Hi,
I wanna upload my pics in to HDD but Whenever i connect the cam to the usb port i cannot see any response from the system.

no change in the 'Pictures' folder

How to connect?

Thanks.

---

### Post by timcredible on 2008-09-08
it doesn't change anything in the pictures folder.  what you should do is install digikam and kipi-plugins from synaptic, then run digikam after plugging your camera in, go to Cameras->Add Camera and auto-detect your camera.

---

### Post by yajuvendra on 2008-09-12
I have installed digikam but i am uable to to find my camera there.
Its Canon Powershot A590IS.

I tried auto detect too.
It says no camera found.
Help.
Thanks.

---

### Post by phidia on 2008-09-12
With the camera plugged in and turned on (switched to filesharing too) open a terminal from Applications > Acessories > Terminal and enter "dmesg" do you see the camera in that output? you can also try "lsusb".
Digital cameras are suppose to be [plug and play]("https://help.ubuntu.com/community/DigitalCameraHowTo") really so if your's isn't then it may not be recognized. Unfortunately there were no hits for your camera at the multimedia forum.

---

### Post by IntuitiveNipple on 2008-09-12
This is the camera? [Canon Powershot A590 IS](http://www.usa.canon.com/consumer/controller?act=ModelInfoAct&fcategoryid=183&modelid=16336#ModelDetailAct)

When the camera is connected to the PC what is the output of:
```

lsusb

```
This should give us the device's USB/PCI ID.

---

### Post by timcredible on 2008-09-12
you might have to change the usb mode on the camera, if it supports 2 different modes.  i had to do that on my fuji s100fs, but not on my fuji z1.

---

### Post by yajuvendra on 2008-09-12
Yes its the camera(the above link).
But there is no support SW for Linux in that site.
There is no problem with the Connection. Bcos i am able to do the same in XP and able to transfer the photos.
But when i try in Ubuntu its not working.

Still working on it.

---

### Post by dolphinsonar on 2008-09-27
subscribing, same camera

---

### Post by wolle212 on 2009-01-30
I was able to import my pictures from my Canon Powershot A590IS via Picasa 3.

[http://picasa.google.de/linux/download.html#picasa30]("http://picasa.google.de/linux/download.html#picasa30")

Nothing else -- as mentioned -- worked. Why Picasa does the trick is beyond me ...

---

### Post by yajuvendra on 2009-02-02
> **wolle212 said:**
> I was able to import my pictures from my Canon Powershot A590IS via Picasa 3.

[http://picasa.google.de/linux/download.html#picasa30]("http://picasa.google.de/linux/download.html#picasa30")

Nothing else -- as mentioned -- worked. Why Picasa does the trick is beyond me ...

Thats good. I will check it out.
Thanks.

---

### Post by chisiyuan on 2009-03-30
I use gphoto2 in terminal to download  photos from my camera. And gtkam, an applicantion with GUI may work too.

---

### Post by wolle212 on 2009-05-17
Hooray,

with Ubtuntu 9.04x64 it works out of the box! Just click click and the pics are in my home-folder :)

---

