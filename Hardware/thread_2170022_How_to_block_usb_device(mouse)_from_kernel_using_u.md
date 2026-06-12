---
title: "How to block usb device(mouse) from kernel using udev rules"
date: 2013-08-24
forum: Hardware
---

### Post by rounaksingh17 on 2013-08-24
hi, 
I am writing a program which will interface with usb external mouse ( uses it and perform something) directly. But, as we know, kernel keeps it away from user space and uses *usbhid* module for it to interface. So I needed to dettach it from kernel. I searched the web and found a way, by blacklisting the *usbhid* module from kernel in modprobe at boot time.
[http://www.howopensource.com/2011/08/how-to-disable-and-enable-usb-device-in-linux/](http://www.howopensource.com/2011/08/how-to-disable-and-enable-usb-device-in-linux/) 
This method actually blocks all usbhid. Therefore, all my external mouses and keyboards stopped working. This is not what i want.   
I need to disable just a specific mouse :!: . 
So,
Searching the Internet again I found another way using udev. They had disabled a IR device by writing a rule in /etc/udev/rules.d/.  
[http://ubuntuforums.org/showthread.php?t=1175001](http://ubuntuforums.org/showthread.php?t=1175001) 
```
ATTRS{idVendor}=="15c2", ATTRS{idProduct}=="0043", OPTIONS+="ignore_device"
```
I copied rule in /etc/udev/rules.d/34-custom-rules.rules and changed the VID, PID, but it didnot work. :( 

  Then, I tried to find some documentation of udev and found it. 
1>[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)[INDENT]This is a previous version documentation,,, it mentioned about the "ignore_devices" and I understand about what it does.  
[/INDENT]
2>[http://0pointer.de/public/systemd-man/udev.html](http://0pointer.de/public/systemd-man/udev.html) and "man udev" in terminal.[INDENT]This seemed new version documentation,moreover there is nothing written about "ignore_device".Also, new OPTIONS values have introduced.  
[/INDENT]
 
Now I am confused that **how I am going to dettach just a specific mouse**. :?  
Because both are stating different.
**If somebody has knowledge of udev, please share it.**
Please help.  

Also, I started learning about udev applying simple rules and then, tried to run a script when some usb device plugged-in using RUN, but I was unable to get a response.```
ACTION=="add",SUBSYSTEM=="usb",RUN+="/usr/local/bin/open_home.sh"
```
**Please also verify this rules.**   
_Thanks._

---

