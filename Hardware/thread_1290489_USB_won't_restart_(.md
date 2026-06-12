---
title: "USB won't restart :("
date: 2009-10-13
forum: Hardware
---

### Post by cthlhu1987 on 2009-10-13
My USB-subsystem ist not really that stable I wanted it to be: Sometimes it just stops working (mostly after I locked the screen under GNOME). Now I found recommendations how to restart the USB-subsystem without restarting the whole system:
```
sudo /etc/init.d/udev restart
```
it made the following output
```
baruch@baruch-laptop:~$ sudo /etc/init.d/udev restart
 * Stopping kernel event manager...                                                                                                             [ OK ] 
 * Starting kernel event manager...                                                                                                             [ OK ] 
baruch@baruch-laptop:~$ 

```
without solving the problem. The USB-subsystem still accepted no UBS-devices without restart. Can somebody help me, plz :( :confused:

---

