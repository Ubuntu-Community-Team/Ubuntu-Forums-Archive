---
title: "Lenovo G430 WLAN problem."
date: 2010-11-19
forum: Hardware
---

### Post by soumyadityac on 2010-11-19
Hi.I installed today Ubuntu ,after hearing a lot about it, in my laptop.
My laptop is Lenovo 3000 G430 4I52.
I installed it inside windows 7.But my problem is ,everything works just fine except the WLAN.When I turm my switch on, nor the LED glows, neither anything comes up on the screen.
I am new to LINUX, so a detailed help will be appreciated.

---

### Post by cooltoad on 2010-11-20
Wifi is working on my lenovo 3000 G430 4152. You will have to install Broadcom's proprietary drivers.

They are available at :
 System - > Administration -> Additional drivers 
This will open a desktop application that will give you the option to install the drivers.
  
Before installing ensure that your wifi hardware's model no is : BCM4312 or in BCM43 series
 run this on terminal to get the model no and match it with model's for which broadcom driver is available
  sudo lshw -C network

I am sure your wifi will start working :)

---

