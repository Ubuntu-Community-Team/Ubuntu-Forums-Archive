---
title: "HowTo: Get your HP laserjet 1000 working."
date: 2009-02-24
forum: Hardware
---

### Post by Iesos on 2009-02-24
I had a problem with a hp lj 1000 after installing (x)ubuntu on a machine. The confusing things where that everything got connected and detected in the proper way, and the driver, foo2zjs, which is the recommended driver for hp lj 1000 seemed to be installed. But nothing worked; that is, the printer didn't print anything. This is what you need to do:

1. Download the driver source from [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)
For example:
```
$ wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
```

2. open it and extract it.
For example:
```
$ tar zxf foo2zjs.tar.gz
$ cd foo2zjs

```

3. Get the driver image for hp lj 1000
```
$ ./getweb 1000
```

Comment: If it complains about "getweb: no such file" or something, you'll need to do a
```
$ sudo apt-get install build-essential
$ make
```
But I think that this step is unnecessary.

4. Make a new device 'node' that is your printer. That is, you probably already have one, at least I had; /dev/lp0. But you should make a new one, somehow the assumed path by some programs seems to be /dev/usb/lp0. (This was the essential step for me, which no other howto seemed to mention)
Do for example do this:
```
$ sudo mkdir /dev/usb
$ sudo cp sihp1000.img /dev/usb/lp0

```

5. We need cups to find your printer, that is find the new node. So change the DeviceURI in /etc/cups/printers.conf to file:///dev/usb/lp0.
For example:
```
$ sudo nano -w /etc/cups/printers.conf
[Comment out the existing DeviceURI line (by adding a # infront of it) and add]
DeviceURI file:///dev/usb/lp0
```

6. Restart cups so that it gets updated. For example
```
$ sudo /etc/init.d/cupsys restart
```

That should do it. If not, restart from 3, do the comment, and also do the
```
$ sudo make install
$ sudo make install-hotplug
$ sudo make cups
```
and then continue from 4.

Good luck.

---

### Post by jon eric pipes on 2009-02-25
im running ubuntu hardy heron and have an hp p1005 printer with the symptoms you described, but your fix didnt work for me
are there fixes for dummies?
jon

---

### Post by crauscher on 2009-02-25
I went through the process to get my hp lj 1000 working, but when I get to the last step to restart the code states:

sudo: /etc/init.d/cupsys: command not found

I attempted to repeat the process multiple times with no effect....

Any suggestions?

Thanks!

---

### Post by crauscher on 2009-02-25
Update....  

I believe if you are using Ubuntu 8.10, you should have HPLIP under your possible programs to "add/remove" 

Click on the box to add this program and continue...

From there, just follow the directions for adding a new device and the program will help you find the missing plug in 

I did have to unplug my printer and restart my computer before the plug in would work properly. 

good luck

---

### Post by stchman on 2009-02-25
In the Administration section there is an HPLIP section.  There you can download the firmware for the 1000 printers.  Or you can use the foo2zjs drivers.

---

