---
title: "ZTE AC8710 and Ubuntu 8.10 any chance to get it work together?"
date: 2009-05-03
forum: Hardware
---

### Post by khurtsiya on 2009-05-03
Hello,

I already read many articles about installing this modem on Ubuntu, but fail doing it.

I know that this is possible, but GNOME-PPP simply do not Detect it.

Any tips will be appreciated.

---

### Post by khurtsiya on 2009-05-05
Anyone?

---

### Post by GeorgeVita on 2009-05-05
> **khurtsiya said:**
> ...
Any tips will be appreciated.

Hi **khurtsiya**, I have not worked with this modem but we could try some "tips".

This is a USB 3G/CDMA modem. Please boot without the modem, wait for the system to stabilize, attach the modem, wait 10-15 seconds open a terminal window and run the command: **dmesg**

This command will list all system activity. From all these lines we need the last 10-15 concerning **ttyUSBx** or **modem** or **option driver**.

After this run: **lsusb**
and then: **ls /dev/ttyU* /dev/ttyA***

Post here the 10-15 lines of **dmesg** and all output from **lsusb** and **ls /dev...**

Regards,
George 
T

---

### Post by khurtsiya on 2009-05-05
**dmesg**

> [   72.101073] wlan0: no IPv6 routers present
[  122.884091] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  123.043752] usb 4-1: configuration #1 chosen from 1 choice
[  123.125479] usbcore: registered new interface driver usbserial
[  123.126712] usbserial: USB Serial support registered for generic
[  123.127983] usbserial_generic 4-1:1.0: generic converter detected
[  123.129408] usb 4-1: generic converter now attached to **ttyUSB0**
[  123.130587] usbcore: registered new interface driver usbserial_generic
[  123.130597] usbserial: USB Serial Driver core
[  123.217183] usbcore: registered new interface driver libusual
[  134.990791] type=1503 audit(1241513426.088:7): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB0" pid=6478 profile="/usr/sbin/cupsd"
[  135.169131] ppdev0: registered pardevice
[  135.217561] ppdev0: unregistered pardevice
[  137.534071] ppdev0: registered pardevice
[  137.581276] ppdev0: unregistered pardevice
[  138.004081] ppdev0: registered pardevice
[  138.052152] ppdev0: unregistered pardevice

> michael@michael-laptop:~$ **lsusb**
Bus 007 Device 003: ID 064e:a103 Suyin Corp. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 07ca:a309 AVerMedia Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0458:0036 KYE Systems Corp. (Mouse Systems) Pocket Mouse LE
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID **19d2:fff5**  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 138a:0001  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by GeorgeVita on 2009-05-05
Hi, I think that **19d2:fff5** in conjuction with only one serial port (/dev/ttyUSB0) is not good. It seems like this is not the "modem" mode.

Have you tried to change **19d2:fff5** to something else?

Using usb-modeswitch see: [http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630))

or with AT commands see: my post#8 of [http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934)
 
In my ZTE MF636 I had to "change" the mode of the USB stick to the modem mode (19d2:0031) and then create the usbserial ports.

G

---

### Post by zampes on 2009-05-05
Hello!
I had a similar issue with the ZTE MF622. The thing is this: You need the 'rules' file for the modem, which you have to copy to /etc/udev/rules.d/, then go to the file /etc/udev/rules.d/ and add the following line at the end before "end of file": ipcp-max-failure 30.
After you've done this, you need to restart your pc with the modem PLUGGED IN -this is necessary.Then, when you restart, ubuntu will see it and allow you to configure it. However, it happened to me that no pendrives could be read, so I had to remove the 'rules' file from '/rules.d' -don't worry, your modem will still work. You may restart your computer again and everything will work just fine.

Here's another post with a solution:
[http://www.tuxhat.com/linux/reliance-netconnect-broadband-on-linux/](http://www.tuxhat.com/linux/reliance-netconnect-broadband-on-linux/)

Except that instead of using wvdial I simply use the NetworkManager Applet 0.7.0 in the taskbar...

---

### Post by zampes on 2009-05-05
Also... take a look at this. 
[http://www.ztemt.com.cn/ennewzte/service/ziliao.action](http://www.ztemt.com.cn/ennewzte/service/ziliao.action)

---

### Post by khurtsiya on 2009-05-16
So who is interested.

Modem works fine thanks to admin of this site [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=727](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=727) who is creator of USB_ModeSwitch I guess. Very helpful guy.

No I am trying to tune this all to somehow disconnect modem because I should restart computer to get it work again if line is disconnected...

---

