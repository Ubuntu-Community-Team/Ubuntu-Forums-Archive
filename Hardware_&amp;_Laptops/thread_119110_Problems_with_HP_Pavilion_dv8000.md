---
title: "Problems with HP Pavilion dv8000"
date: 2006-01-18
forum: Hardware &amp; Laptops
---

### Post by manu007 on 2006-01-18
Hi all,

I try to install ubuntu 5.10 on an HP Pavilion dv8000 (dv8050EA), but i have some problems in 64bit.

starting normaly, the computer hangs.
starting with noacpi option, i am able to install the basic soft, but a cannot reach the network. The net card is initialized correctly, but a can't ping any computer on the net.
With another distribution, i have the same problem, but installing a new stock kernel (2.6.15), everything is running.

I can't do that with ubuntu, the basic system does not contains the development system...

The HP uses the ATI-XP chipset.

any idea ?

---

### Post by rockratid on 2006-01-23
I had the same problem, but the Ubuntu i386 distribution installed great.  Unfortunately my xorg configuration is not working.  I have tried a few things and have yet to find anything useful.  If anyone has a working xorg configuration would love to know what worked.

---

### Post by rockratid on 2006-01-24
I noticed while trying to solve my problem all sorts of threads discussing the same problem for 64 bit processors on other hp models.  A couple threads had good step by step solutions to the problems.  I personally would rather run 32 bit at this point.

So I managed to get my X-windows working by simply doing the following:

sudo dpkg-reconfigure xserver-xorg

I chose the medium installation options.  Did not probe the video card and set it to vesa.  I then set my resolution to the max supported by windows at 100Hz refresh and so forth and so on.

Ndiswrapper for the broadcom wlan was easy as well I simply probed my windows side of the system in the system32/drivers folder the bcmwl5.sys is the system driver.  I then searched the drive for bcmwl5.inf copied them to my linux side of the house and followed the standard ndiswrapper steps and I am up and running.

---

### Post by bryhawks on 2006-04-29
I had the same issue but was able to pass the argument of 
linux nopic nolapic at the time of booting. I was able to then continue. I am useing the 64bit 5.10.

---

