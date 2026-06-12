---
title: "dial up"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by iroquois on 2009-10-23
could anyone tell me how i could find the name of the port i'm using for my usr robotics USB modem?this is where i get hung up trying to get my modem connection set up.I have ubuntu 9.04

---

### Post by dstew on 2009-10-23
Here is a nice [How-To with screenshots]("http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html") to set up a dial-up connection using the graphical user interface tools. It is from an earlier version of Ubuntu, but something like this should work for 9.04

The serial ports have device names like /dev/ttyS0, /dev/ttyS1 etc. If you want to set up serial communications using the command line, I think the [wvdial]("http://linux.die.net/man/1/wvdial") program is what you want. You need to specify the serial port and modem set-up parameters in the [/etc/wvdial.conf file]("http://linux.die.net/man/5/wvdial.conf"). The [wvdialconf program]("http://ubuntuforums.org/showthread.php?t=1298850") can help you create your /etc/wvdial.conf file by automatically detecting your modem. Try that.

---

### Post by iroquois on 2009-10-23
ty dstew,my external modem isn't connected to a serial port.It's a USB connection.I'd just need a way to find out how to identify which USB connection it is.The modem set up method i'm using is ppp config

---

### Post by dstew on 2009-10-23
The command **lsusb** will show a list of USB devices.

---

### Post by Bartender on 2009-10-23
ttyACMO.  Pretty sure that's an "oh", not a zero. (?)

---

### Post by iroquois on 2009-10-23
thanks

---

