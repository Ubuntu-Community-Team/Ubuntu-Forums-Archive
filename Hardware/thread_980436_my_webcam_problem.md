---
title: "my webcam problem"
date: 2008-11-12
forum: Hardware
---

### Post by netloglinux on 2008-11-12
as i am new to ubuntu-linux, i dont know how i can configure my webcam, i.e i dont know how to search for the hardware and to install the driver... my laptop model is acer 4520,

.......................

and i have one more problem with firefox, the browser is not loading flash contents properly (with ganish) so i installed adobe flash player but still it uses the old player, how to change firefox for the new player?...


thanks and regards...

---

### Post by tvtech on 2008-11-12
it should have been automatic 

install ```
sudo apt-get install gnome-device-manager
```  it should show up under your usb devices as something like... USB2.0 1.3M UVC WebCam

then install cheese or something and see if it works, mine only works with cheese and it shows up at /dev/video0  quickcam see's it but can't use it.... 
if you want to test it install 

```
sudo apt-get install gnome-volume-properties
``` 

and it gives you a gui config tool for it and you can check and see if it works there.

OPPS SORRY ABOUT THAT gnome-volume-properties is a useful tool install it anyways.  the program you want to test your video input is this 

```
sudo apt-get install gstreamer-properties
```

you can test your webcam there.

all these programs will show up under System>Preferences

---

### Post by tvtech on 2008-11-12
hope that helps or at least gets you pointed in the right direction!

---

