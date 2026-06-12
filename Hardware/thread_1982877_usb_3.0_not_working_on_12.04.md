---
title: "usb 3.0 not working on 12.04"
date: 2012-05-19
forum: Hardware
---

### Post by timcredible on 2012-05-19
i added usb_storage to /etc/modules, which seemed to get usb 3.0 to work for a while, but it's not working most of the time.  the drive works fine if i plug into a usb 2.0 port.  anybody know what's going on with usb 3.0?

thanks

---

### Post by vandorjw on 2012-05-24
usb 3.0 is backward compatible with usb2.0.
Support should be build into the kernel. I also have USB 3.0.

```
lspci | grep USB 
```
> 
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
03:00.0 USB Controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller


I am not sure why you had to add it to modules, since mine is loaded by default.
Use the following command to check if it is loaded when it is not working.

```

lsmod | grep usb

```

> 
usb_storage            56275  1 


If it is not loaded, load using
```

sudo insmod usb_storage

```

Even if it was loaded, remove using
```

sudo rmmod usb_storage

```
 and then reload

What distrobution and version are you using?

uname -a

---

### Post by timcredible on 2012-05-27
device is seen:
```

tim1204@HP-Desktop:~$ lsusb
Bus 008 Device 004: ID 1058:0740 Western Digital Technologies, Inc. My Passport 1TB

```

usb_storage is loaded, even after removing it and rebooting:
```

tim1204@HP-Desktop:~$ lspci | grep USB
usb_storage            49198  0 

```

i even ran gparted and did a check on all partitions (it has 7, with swap, fat32, many ext4), no change.  it mounts every time on usb2, i boot off of it with usb2 just fine, but it only rarely mounts on usb3.  if nobody else is having the problem, maybe my usb3 card is bad

---

### Post by SuperFreak on 2012-05-28
Same problem. My USB 3 drive is sometimes recognized and mounted for a few seconds and then disappears

---

### Post by SuperFreak on 2012-06-03
Appears that Asmedia controllers may not work with Linux [https://bbs.archlinux.org/viewtopic.php?id=139421](https://bbs.archlinux.org/viewtopic.php?id=139421)
we both seem to use that USB 3 controller. My back USB 3 connections work, just not my front ones

---

### Post by timcredible on 2012-06-04
Thanks, that's what i was afraid of, guess I'll get a different card

---

### Post by trucken on 2012-08-02
I found a reference to adding the line 

blacklist uas

to file /etc/modprobe.d/blacklist.conf

I did a restart and my usb is working.  I would love to know what this did and why it works?
:)

I found only one reference to this and it was pretty obscure, I almost missed it.

---

### Post by timcredible on 2012-08-03
thanks for the info.  it didn't work for me, but hopefully it works for others.  i think mine is a conflict with an existing usb2 hub...

---

### Post by michalt on 2012-09-14
> **trucken said:**
> I found a reference to adding the line 

blacklist uas

to file /etc/modprobe.d/blacklist.conf

I did a restart and my usb is working.  I would love to know what this did and why it works?
:)

I found only one reference to this and it was pretty obscure, I almost missed it.

Did work for me! Thanks! (Dell Vostro 3360)

Added later: Not perfect, works after restart though after connecting USB for second time, again USB 2.0

---

### Post by malakar.subhendu on 2013-04-14
it worked for me only. After doing a restart, it started again.
doing a usb-devices showed that the driver was uas and not usb-storage

---

### Post by pepsifx357 on 2013-07-05
THANK YOU!!!!!!  

<--Sabertooth 990FX Rev 2.0

The network card doesn't work in it either, so there was no way to get any data to it without hooking up a dvd-rom.  Now I have a WAY!!!!

Now onto the network card problem...

---

