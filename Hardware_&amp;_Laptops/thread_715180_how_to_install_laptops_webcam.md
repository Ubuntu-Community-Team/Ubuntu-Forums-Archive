---
title: "how to install laptops webcam"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by karq on 2008-03-04
Maybe someone can tell me how to get my laptops webcam working under ubuntu?

---

### Post by linuxwizard on 2008-03-04
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. If that does not work post results of the command > lsusb

---

### Post by Steve Angelidis on 2008-03-04
Hi. Sorry to butt in but I have the same question as Karq. I played with settings in Ekiga as suggested -- to no avail.

The webcam did seem to be detected though.

Ran lsusb as suggested and received the following output:

steve@steve-laptop:~$ lsusb
Bus 005 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

Greatly appreciate any help.

Steve A.

---

### Post by linuxwizard on 2008-03-04
Hello Steve Angelidis
If you can't get your cam to work with Ekiga than I would suggest installing the driver from here > [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) >> your webcam is listed an supported > Bus 005 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd

---

### Post by Steve Angelidis on 2008-03-04
Thanks Mr. Wizard! I'll give it a try. 

Don't know if my Linux "skills" are up to it though.
 
Steve A.

---

