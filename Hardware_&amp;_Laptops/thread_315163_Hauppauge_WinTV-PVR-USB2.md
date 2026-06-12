---
title: "Hauppauge WinTV-PVR-USB2"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by tgkspike on 2006-12-08
Does anyone know how to get the Hauppauge WinTV-PVR-USB2 working yet? It is in the 2.6.18.1 kernel. I am using this kernel with Ubuntu 6.10. What else do I have to do to get it to work?

---

### Post by FryerFox on 2006-12-08
I used this quide:

[pvrusb2 driver information]("http://www.isely.net/pvrusb2/pvrusb2.html")

I use it in my MythTV setup.

---

### Post by tgkspike on 2006-12-08
Thanks

I assume you got this working with mythtv. 
Right now I am working on extracting the firmware

---

### Post by FryerFox on 2006-12-08
> **tgkspike said:**
> I assume you got this working with mythtv.

I did. If you have never used MythTV before, I suggest you find a nice guide for that too. I found [this one]("https://help.ubuntu.com/community/MythTV") and [this one]("http://parker1.co.uk/mythtv_ubuntu.php") useful.

---

### Post by tgkspike on 2006-12-08
I extracted the firmware (and moved it to where I think it should go) , and have the driver installed, 

TVtime says no singal and 
pvrusb2: invalid argument 
cannot open capture device on /dev/video0

When I start Xawtv the red light on the pvrusb2 turns on, 
but I am only getting static images

tgkspike@equared:~$ xawtv
This is xawtv-3.95, running on Linux/i686 (2.6.18.1-custom)
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
libGL warning: 3D driver claims to not support visual 0x5b
_______________________________________________________

Any help would be great

---

### Post by FryerFox on 2006-12-09
In TVTime, I also get:

No signal
pvrusb2: invalid argument
cannot open capture device on /dev/video0
No Video Source

I must have it configured incorrectly, but I don't use TVTime myself, so I never spent any time trying to get it working. The WinTV-PVR-USB2 is working fine for me in Myth, though.

---

### Post by carella on 2006-12-29
Hello I have the same pb with the same hardware and procedure

But in my case /dev/video directory does not even exist !

What have I to do ?

Thanks

---

