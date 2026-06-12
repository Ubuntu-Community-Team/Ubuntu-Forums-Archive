---
title: "Help running driver on startup"
date: 2008-09-26
forum: General Help
---

### Post by quic on 2008-09-26
I have just installed the driver that allows the Xbox 360 controller to be used within Ubuntu (for XBMC).  However I do not wish to have to open a terminal window and manually change directory to the driver location and then execute the driver with arguments everytime I boot up. I would like the driver to autorun everytime I boot up, without interaction (if possible).

This is what I have to put in at the moment
```
albert@albert-laptop:-$ cd /home/tmp/xboxdrv-linux-0.2

albert@albert-laptop:~/tmp/xboxdrv-linux-0.2$ sudo ./xboxdrv --wid 0 -s -l 2 --dpad-as-button --deadzone 12000
```

How can I get this to run automatically on startup with root privilages, with the password being filled automatically?

---

### Post by Sycron on 2008-09-26
I think tmp directory is automatically removed at every startup. I'm wrong ?

---

### Post by quic on 2008-09-26
The tmp folder is just a normal folder that I have created, nothing special about it.

---

### Post by Sycron on 2008-09-26
Go to System-->preferenceres-->Sessions and add those commands at startup.

---

