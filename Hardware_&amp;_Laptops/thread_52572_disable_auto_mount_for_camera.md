---
title: "disable auto mount for camera?"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by ccolon on 2005-07-28
I'm currently having problems with my webcam ( Creative PC CAM 300 )

I installed the spca5xx module from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

However when I run an application (e.g. spcagui, spcaview or gqcam)  that accesses the webcam, one of two things happen:-

a) The webcam is detected, everything runs fine and works  :-)

b) The application starts and then my computer freezes completely, the only thing I can do is reboot the machine by switching the power off.   :-(

The only difference between scenarios (a) and (b) is how quickly I start the webcam application after plugging in the usb cable of the pc cam.

I think what is happening in (b) is that the usb connection to the pccam internal memory card is mounted. Then trying to access the webcam through /dev/video0
crashes the system. However if the webcam application gets there first everything is fine as in (a).

I would like to be able to temporary disable auto mount for the pc cam usb file transfer facility, so I can use the webcam without fear of a system crash. Is this possible?? I don't fully understand the ubuntu automount system.

Cheers if anyone can give me a simple solution to this,

David

ps I'm actually running kubuntu if that makes any odds

ps2 If I don't try to start any webcam applications at all. I can access the pc cam internal memory automatically using konqueror and transfer stored images, but I don't really want to do this. I just want to use the webcam facility.

---

### Post by ccolon on 2005-07-28
I've recently discovered that in Kubuntu you can stop automounting by typing:-

sudo /etc/init.d/dbus-1 stop

However I think this is a KDE only solution. (i.e only relevent to Kubuntu).

It's also quite a nasty hack as:-

sudo /etc/init.d/dbus-1 start

doesn't get the auto mounting working again.

But at least after disabling the dbus daemon the pccam 300 streams images, without causing a system crash  :-)

If anyone has a better solution for temporarily disabling automount in Kbuntu, I would still be interested ( I realise I'm in the wrong forum now, but I didn't realise automount of drives was KDE/Gnome specific in my original post )

David

---

