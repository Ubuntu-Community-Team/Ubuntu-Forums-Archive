---
title: "usb mouse stalls irregular"
date: 2004-12-13
forum: Hardware &amp; Laptops
---

### Post by wimva on 2004-12-13
Hi all, 

After an otherwise nice installation of ubuntu on my laptop (Fujitsu-Siemens C1020) I experienced a rather anoying feature : my usb mouse (MS Optical Wheel Mouse) stalls after some time - however the touchpad keeps on going fine. 

I have been able to narrow it down to the following :

1) it is possible to reproduce on purpose by opening for example a terminal window and moving the terminal window around the desktop very fast (shaking) with the mouse, then after some time the usb mouse refuses to work - using the touchpad is no problem

2) after some research  I managed to temporarily "resolve" the problem by the following commands : 

   sudo modprobe -r usbhid ; sudo modprobe usbhid

after which the usb mouse respons happily again. 

Of course I would like to have a more permanent solution because it always stalls at the wrong moment. Anyone with more technical knowledge any ideas?

Thanks for the effort.

---

### Post by wulf on 2004-12-13
[QUOTE=wimva]Hi all, 

After an otherwise nice installation of ubuntu on my laptop (Fujitsu-Siemens C1020) I experienced a rather anoying feature : my usb mouse (MS Optical Wheel Mouse) stalls after some time - however the touchpad keeps on going fine. 

I have been able to narrow it down to the following :

1) it is possible to reproduce on purpose by opening for example a terminal window and moving the terminal window around the desktop very fast (shaking) with the mouse, then after some time the usb mouse refuses to work - using the touchpad is no problem

2) after some research  I managed to temporarily "resolve" the problem by the following commands : 

   sudo modprobe -r usbhid ; sudo modprobe usbhid

after which the usb mouse respons happily again. 

Of course I would like to have a more permanent solution because it always stalls at the wrong moment. Anyone with more technical knowledge any ideas?

Thanks for the effort.[/QUOTE]
 I've got the same mouse but a different laptop (Packard Bell EasyNote M5262). So far I haven't seen the same problem.

How long does the mouse usually work until it stalls? I've had the machine on for up to 7-8 hours at a time (AC power) and no problems. It might just be that the USB subsystem is happier on my laptop but I wonder if the time might be significant?

Wulf

---

### Post by wimva on 2004-12-14
Thanks for your info. 

At the moment it is going better - althought it has already stopped responding one time this evening. Can't give an estimate on the time interval before the mouse stops working - it has been 10 minutes as wel as an hour. 

I found out how to restore the mouse without rebooting - so I will live with it for the moment. 

Regards, 
Wim

---

### Post by wulf on 2004-12-15
What's the trick you discovered? It would be worth posting here in case anyone else hits the same issue, does a search and discovers this thread.

Wulf

---

### Post by wimva on 2004-12-18
Aha ... I suppose I wasn't very clear in my first mail because it is there already. 

The trick is to unload en reload the usbhid module as the following commands illustrate : 

  sudo modprobe -r usbhid ; sudo modprobe usbhid

after that, the mouse works again.  

Bye

---

### Post by Dam on 2005-04-20
Same computer and same problem!

See [http://www.ubuntuforums.org/showthread.php?p=140511](http://www.ubuntuforums.org/showthread.php?p=140511)!

---

### Post by wimva on 2005-11-16
Just to inform you that Breezy has no problem with my mouse and laptop. 
Someone has hit the right button !! Great.

---

