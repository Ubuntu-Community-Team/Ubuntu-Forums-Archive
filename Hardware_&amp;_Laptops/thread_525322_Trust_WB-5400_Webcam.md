---
title: "Trust WB-5400 Webcam"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by lgambett on 2007-08-14
Hi all,
Anyone succeeded in making this webcam work under (K)Ubuntu ?
Lsusb gives;

Bus 005 Device 013: ID 0c45:624e Microdia
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000

I have installed recent gspca driver, but nothing happens.

This is the output from /var/log/messages (BTW; why NetworkManager is working here ?)

Aug 14 13:35:23 hp kernel: [185585.492000] usb 5-2: new high speed USB device using ehci_hcd and address 14
Aug 14 13:35:23 hp NetworkManager: <debug info>^I[1187091323.588001] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_624e_noserial').
Aug 14 13:35:23 hp kernel: [185585.624000] usb 5-2: configuration #1 chosen from 1 choice
Aug 14 13:35:23 hp NetworkManager: <debug info>^I[1187091323.641190] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_624e_noserial_if0').
Aug 14 13:35:23 hp NetworkManager: <debug info>^I[1187091323.658191] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_624e_noserial_usbraw').

Thanks to everybody,
Luca

---

### Post by sitepamarco on 2008-06-07
Hi Igambett,
Mine's just working fine on Kubuntu 8.04 2.6.24-18-rt #1 SMP PREEMPT RT Wed May 28 21:53:07 UTC 2008 x86_64 GNU/Linux :)
(AMD Athlon 4800+ 64x2 - Gigabyte MA69VM-S2 - 2 Go RAM - nvidia Geforce 8600GT 512 Mo - Webcam Trust WB-5400 - All-in-one Brother DCP-330C - Screens Yuraku YV22WB1 LCD 22" + Targa CRT 15" - Kbd and mouse LABTEC Power Wireless desktop plus)

Hope this will help you.
Start here :
[https://groups.google.com/group/microdia/web/using-git-with-microdia]("https://groups.google.com/group/microdia/web/using-git-with-microdia")

And then :
[https://groups.google.com/group/microdia/web/testing-microdia-driver-draft]("https://groups.google.com/group/microdia/web/testing-microdia-driver-draft")

Enjoy

---

### Post by Lomendil on 2008-06-16
Hi,

I have the same webcam and it seems I won't make it work !

I tried your 2 links sitepamarco but with no luck.

I used Synaptic to install Git and I tried to install driver :

```
silk@silk-ubuntu:~$ git clone http://repo.or.cz/w/microdia.git
Initialized empty Git repository in /home/silk/microdia/.git/
/usr/bin/git-clone: 374: curl: not found
```


Can't find what's not working.

EDIT : Problem wasn't hard to fix : curl needed to be installed.
Now I'm stuck with the git repository being offline ... bad luck :D

---

### Post by sitepamarco on 2008-06-16
> **Lomendil said:**
> Hi,

I have the same webcam and it seems I won't make it work !

I tried your 2 links sitepamarco but with no luck.

I used Synaptic to install Git and I tried to install driver :

```
silk@silk-ubuntu:~$ git clone http://repo.or.cz/_w_/microdia.git
Initialized empty Git repository in /home/silk/microdia/.git/
/usr/bin/git-clone: 374: curl: not found
```


Can't find what's not working.

EDIT : Problem wasn't hard to fix : curl needed to be installed.
Now I'm stuck with the git repository being offline ... bad luck :D

Maybe you should simply try :

 ```
git clone [http://repo.or.cz/](http://repo.or.cz/)**_r_**/microdia.git
``` 

Instead of : git clone [http://repo.or.cz/](http://repo.or.cz/)**_w_**/microdia.git

See something quite a bit different somewhere? ;-)

---

