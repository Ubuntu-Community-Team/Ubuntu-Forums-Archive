---
title: "trying to set up raw printer"
date: 2010-02-21
forum: Hardware
---

### Post by kmrs75 on 2010-02-21
ok i have 2 vinyl cutters one i was able to set up as a raw printer. as soon as i plugged it in it found it and i was able to add it as a generic raw. 

i tried my other cutter when i plugged it in i didnt get a pop up to add printer. i tried it manually so far no luck 

lsusb 

ken@ken-desktop:~$ lsusb
Bus 001 Device 004: ID 0644:0200 TEAC Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 041e:4034 Creative Technology, Ltd WebCam Instant
Bus 003 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Green"]Bus 006 Device 006: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC[/COLOR]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

the green is the cutter 

i tried different things when i set it up manually 

im little stumped on device URI i found it under dev/serial/by-id/usb-FTDI_FT232R_USB_UART_A9006Med-if00-port0

so i tried usb://dev/serial/by-id/usb-FTDI_FT232R_USB_UART_A9006Med-if00-port0

that didnt do it all i get is an error printer not connected 

i also tried serial://........

it just sits in printer que processing nothing more 

i read some place where the FT232 needs drivers to make it work any luck with any of this 

thanks in advance you all are the best

---

### Post by givrix on 2012-12-21
This is an old post but the bug is still there.
To use my cutter as a serial printer i had to :

assign my user to the dialout group :
```
sudo usermod -a -G dialout #user#
```

then change the permission on a cups file :
```
chmod 700 /usr/lib/cups/backend/serial
```

No idea why it solves the issue but then serial ports appear when scanning for printer !
Found how to solve here : [https://bugs.archlinux.org/task/20396](https://bugs.archlinux.org/task/20396)

---

### Post by overdrank on 2012-12-21
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

