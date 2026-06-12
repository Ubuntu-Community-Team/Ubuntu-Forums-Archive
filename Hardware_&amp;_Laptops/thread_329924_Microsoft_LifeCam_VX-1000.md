---
title: "Microsoft LifeCam VX-1000"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by InFoMaLuCo on 2007-01-02
I'd like to make my Microsoft LifeCam VX-1000 works  on Ubuntu 6.10.
How can I do it? I've searched on the internet but I didn't find it.

Thanks.

---

### Post by vanstrien on 2007-02-09
You'll want a driver for the spca5xx chipset.  Althought Edgy comes with a driver spca5xx, I didn't have any success with it.  

Instead I downloaded and compiled the generic spca driver from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html).  It doesn't work great, but it works fine enough.

To test it you could also download and compile the spcagui application on the website, but camorama is in the repositories so its a lot faster to use that.

By the way, if your camera doesn't work, try launching camorama as root.

I'm going to check out some of the other drivers and configuration settings for the spca chipset to see if they work better.  gspca is good but not quite good enough.

---

### Post by rklauco on 2007-03-04
Does the camera actualy works with self-compiled spca module?

---

### Post by stuarttaylor on 2007-04-29
How about the microphone? I've got the camera working.

---

### Post by mravenca on 2008-06-17
I tried to compile the spca5xx driver, but I got this error message:

root@ubuntu1:~/inst/webcam/spca5xx# make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/root/inst/webcam/spca5xx CC=cc modules
make[1]: Entering directory `/lib/modules/2.6.15-26-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-26-386/build'
make: *** [default] Error 2

Can you help me?

Thank you

---

### Post by rklauco on 2008-06-17
You better try
```
make modules
```

---

### Post by mravenca on 2008-06-17
This is what I got:

root@ubuntu1:~/inst/webcam/spca5xx# make modules
make: *** No rule to make target `modules'.  Stop.

---

### Post by rklauco on 2008-06-17
First of all - do you have the kernel source downloaded, or at least kernel headers?
What is the result of
```
sudo apt-get install linux-headers-`uname -r`
```
?

---

### Post by mravenca on 2008-06-18
First of all, thank you for help.

I have installed linux headers, but the result is still the same:

root@ubuntu1:~# apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-26
The following NEW packages will be installed:
  linux-headers-2.6.15-26 linux-headers-2.6.15-26-386
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 7762kB of archives.
After unpacking 79.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-26 2.6.15-26.47 [6905kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-26-386 2.6.15-26.47 [857kB]
Fetched 7762kB in 29s (261kB/s)
Selecting previously deselected package linux-headers-2.6.15-26.
(Reading database ... 68577 files and directories currently installed.)
Unpacking linux-headers-2.6.15-26 (from .../linux-headers-2.6.15-26_2.6.15-26.47_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-26-386.
Unpacking linux-headers-2.6.15-26-386 (from .../linux-headers-2.6.15-26-386_2.6.15-26.47_i386.deb) ...
Setting up linux-headers-2.6.15-26 (2.6.15-26.47) ...

Setting up linux-headers-2.6.15-26-386 (2.6.15-26.47) ...
root@ubuntu1:~# cd /root//inst/webcam/spca5xx
root@ubuntu1:~/inst/webcam/spca5xx# make modules
make: *** No rule to make target `modules'.  Stop.

---

### Post by mravenca on 2008-06-19
lsusb says:

root@ubuntu1:~/inst/webcam/gspca# lsusb
Bus 001 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 003: ID 045e:00f7 Microsoft Corp.
Bus 001 Device 001: ID 0000:0000

---

### Post by mravenca on 2008-06-20
I got an idea, but I am not sure, if it will work. Could someone send me a compiled kernel module gspca.o?

My address is [email]mravenca@gmail.com[/email]

---

