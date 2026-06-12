---
title: "Quartus USB-Blaster setting help!"
date: 2010-03-29
forum: Hardware
---

### Post by Thrivine on 2010-03-29
Hi,all!

I'm a newbie in using **Ubuntu** **Linux**, and just encountered a troublesome question, which I can hardly resolve by myself.

I want to do my circuit designing work in the Linux environment and download the design into Altera's DE2 board by the USB cable. The question is, no matter what efforts I make, frustratingly, the programmer of Quartus still can't detect the USB Blaster.

I plug in the USB Blaster and tap in the terminal this:
lsusb

And I get this:
Bus 003 Device 003: ID 09fb:6001 Altera

I tap in this:
[Altera_Home]/quartus/bin/jtaconfig

And this is what I get:
No JTAG hardware available

I guess the system has recognized the USB device, but the Quartus hasn't. I don't know how to fix it.

Is there somebody who came across the same question as I do? Is there someone experienced with Quartus software could provide some advice? I need your help sincerely!

---

### Post by andy16666 on 2010-06-09
I also had similar problems with the DE2 board on Ubuntu 10.04, using Quartus II version 9.1. 

I found this thread on the topic which solved it for me: 

[http://www.alteraforum.com/forum/showthread.php?t=22481](http://www.alteraforum.com/forum/showthread.php?t=22481)

This is what I did: 
```

$ sudo mount --bind /dev/bus /proc/bus
$ sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices
$ sudo <quartus_directory>/bin/jtagd
$ sudo <quartus_directory>/bin/jtagconfig
$ <quartus_directory>/bin/quartus 

```

---

### Post by player999 on 2011-05-15
I'm getting frustrated. It doesn't work for me! Running Natty 11. Yes, something like that(above) has been worked in Maverick.

---

### Post by dizel3d on 2011-05-16
Try this.
```

$ sudo killall jtagd
$ sudo chmod 755 /sys/kernel/debug/usb/devices
$ sudo chmod 755 /sys/kernel/debug/usb
$ sudo chmod 755 /sys/kernel/debug
$ sudo mount --bind /dev/bus /proc/bus
$ sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices
$ sudo <quartus_directory>/bin/jtagd
$ sudo <quartus_directory>/bin/jtagconfig

```Have a problem with "jtagconfig" yet? Make sure, that "jtagd" is working? Run command "ps -A | grep jtagd".

---

### Post by player999 on 2011-05-16
> **dizel3d said:**
> Try this.
```

$ sudo killall jtagd
$ sudo chmod 755 /sys/kernel/debug/usb/devices
$ sudo chmod 755 /sys/kernel/debug/usb
$ sudo chmod 755 /sys/kernel/debug
$ sudo mount --bind /dev/bus /proc/bus
$ sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices
$ sudo <quartus_directory>/bin/jtagd
$ sudo <quartus_directory>/bin/jtagconfig

```Have a problem with "jtagconfig" yet? Make sure, that "jtagd" is working? Run command "ps -A | grep jtagd".

Maybe I've solved the problem.
ByteBlaster was already binded in my startup script

Those commands helped me:
```
$killall jtagd
$jtagd --user-start
```
I've read about it at Altera Forums too
I don't even know what "--user-start" means, nevertheless it works fine.
But problem with Quartus, when i deattach DUT device and attach again is still unsolved. Every time i need to reinitialize ByteBlaster device and even restart Quartus. Very awkward.
Thanks for prompt reply.

---

