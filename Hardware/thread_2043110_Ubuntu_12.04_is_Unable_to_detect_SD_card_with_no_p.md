---
title: "Ubuntu 12.04 is Unable to detect SD card with no partition"
date: 2012-08-15
forum: Hardware
---

### Post by jiapei100 on 2012-08-15
Hi, all:

Ubuntu 12.04 is not able to detect my plugged in SD Card via a SD Card reader. **dmesg** gives

> [  569.396121] usb 5-4: new full-speed USB device number 15 using ohci_hcd
[  569.536130] usb 5-4: device descriptor read/64, error -62
[  569.780131] usb 5-4: device descriptor read/64, error -62
[  570.020119] usb 5-4: new full-speed USB device number 16 using ohci_hcd
[  570.160133] usb 5-4: device descriptor read/64, error -62
[  570.404130] usb 5-4: device descriptor read/64, error -62
[  570.644119] usb 5-4: new full-speed USB device number 17 using ohci_hcd
[  571.052109] usb 5-4: device not accepting address 17, error -62
[  571.188132] usb 5-4: new full-speed USB device number 18 using ohci_hcd
[  571.596110] usb 5-4: device not accepting address 18, error -62
[  571.596135] hub 5-0:1.0: unable to enumerate USB device on port 4



I'm sure the SD card reader is working fine since I tried my other 32giga SD Card. However, it's quite possible that I happened to have removed the partition info of this 16giga Patriot SD Card. How can I get this SD card back to life anyway?


Cheers
Pei

---

### Post by ahallubuntu on 2012-08-15
You have to have at least ONE partition on any device, SD card, hard drive, or otherwise.

You can use Gparted to re-partition the card (add at least one partition to it):

```
sudo gparted
```

If Gparted isn't installed, install it:

```
sudo apt-get install gparted
```

---

### Post by jiapei100 on 2012-08-15
Hi, ahallubuntu:

Thanks for your reply... 

I did have **gparted** installed. Please refer to my other posted message here [http://ubuntuforums.org/showthread.php?t=2042712](http://ubuntuforums.org/showthread.php?t=2042712) .
It's just because even gparted fails to display anything related to my SD card, and after I met this "dmesg" error, did I decide to post in a new topic.


Now, I even tested
```
pei@pei-GA-870A-UD3:/dev$ sudo parted /dev/sdc
```
still, I got the following error message when I tried to **rescue**
```
(parted) rescue                                                           
Error: /dev/sdc: unrecognised disk label 
```


Sigh.... Why can't a SD Card be as robust as a USB pen drive?


Cheers
Pei

---

### Post by holmez on 2012-09-11
Same problem. This was working happily before I upgraded from 10.04.1 to 12.04.1

---

### Post by jiapei100 on 2012-09-11
It seems you proposed a solution to this problem.

Try to find an old Ubuntu 10.04, and solve this problem ! right? :D


> **holmez said:**
> Same problem. This was working happily before I upgraded from 10.04.1 to 12.04.1

---

