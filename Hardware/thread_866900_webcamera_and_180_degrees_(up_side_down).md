---
title: "webcamera and 180 degrees (up side down)"
date: 2008-07-22
forum: Hardware
---

### Post by iosifidis on 2008-07-22
Hello,

I just installed ubuntu 8.04 to a friend's ASUS F7SR-7S056C. The problem I face is that the web camera is up side down. I searched the net and couldn't find something. A friend on the list had the same problem, I wrote him but I think everyone is on vacation. That's why I write here.

Is there any ideas?

Take care

---

### Post by iosifidis on 2008-07-29
I found something on the net but since I'm new, I don't know how to do it.

On the driver that it loads, it needs an invert option. It means 

 modprobe xxxx_driver_name_xxx invert=1

that I type it as it is or I put it in an option file in

/etc/modprobe.d/

I found the driver and chech the documentation. The I upload with modprobe -r driver_name and then I give modprobe driver_name with the option for invert, and check if it works. If yes, then put it in the option file.

Well, few questions:

1. How do I find what driver it loads?
2. How do I create an option file?

---

### Post by evets25 on 2008-07-29
Those of us who have been using the Lenovo Y510 have been having the same problem, you can read about it [here]("http://ubuntuforums.org/showthread.php?t=870681"). This is more progress than we made on it, so if anyone has some more specific instructions on how to set this up that would be great. Also, note that some people who tried the Lenovo Y510 with the 64-bit version of ubuntu reported no problems with the webcam. 

EDIT: Also, I ran a lspci, and this was the only thing that looked like it could be the webcam: 

```
07:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

I'm thinking that the webcam must be the same in both types of laptops, or perhaps the same kernel module for both, or something like that. Thoughts anyone?

---

### Post by winnibob on 2008-07-29
evets25 : the result you show from lspci is for the xD-card reader. I think the webcam is usb-wired, so you should try lsusb instead of lspci. Without any external usb peripheral plugged in, it gave me the following, which seems to be more related to the webcam :```
Bus 004 Device 004: ID 046d:09b6 Logitech, Inc.
```

---

