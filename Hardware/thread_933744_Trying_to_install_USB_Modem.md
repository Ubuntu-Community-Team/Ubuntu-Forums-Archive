---
title: "Trying to install USB Modem"
date: 2008-09-29
forum: Hardware
---

### Post by ehsensiraj on 2008-09-29
I am trying to install Huwei ETS 2051 on my computer. I am totally clueless where to start since I am using ubuntu for the first time. 

I give this command in terminal "lsusb" and got following:
 
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```  

would you please guide me to install this modem.

---

### Post by phidia on 2008-09-29
There is a Ubuntu wiki on that make modem [here]("https://help.ubuntu.com/community/DialupModemHowto/Huawei") but that isn't for your specific model.
You can try to use the guide [here]("http://www.openpages.info/huawei.html") but that isn't specifically for ubuntu so some of the steps may have to be adjusted.

---

### Post by JC Cheloven on 2008-09-29
Most likely you have to use the program "wvdial", which is included by default in Ubuntu. I don't know about your particular model, but you may find this useful (I think that the general scheme should be very similar):

[http://ubuntuforums.org/showthread.php?t=843973&highlight=e220](http://ubuntuforums.org/showthread.php?t=843973&highlight=e220)

Also some good news: next version of Network Manager (NM7, which is supposed to be included in Ubuntu Intrepid), will handle usb gprs modems itself. You could try installing NM7 on Ubuntu Hardy (you'll find guidelines also in the avobe link) but I did'n have any succes with it.

---

### Post by ehsensiraj on 2008-09-30
Well I try to install it I 'll let you know my progress. As far NM7 concern I think I have to package it myself. I have no idea how I can do that?.

---

### Post by ehsensiraj on 2008-09-30
with "sudo wvdialconf" I got this:

> ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   

but when I checked this syslog it showed this:
> Sep 30 11:33:23 ehsen-desktop NetworkManager: <debug> [1222788803.249956] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3410_TUSB3410'). 
Sep 30 11:33:23 ehsen-desktop NetworkManager: <debug> [1222788803.479437] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3410_TUSB3410_if0'). 

So It look like ubuntu detect something but I have no idea how to make it work.

---

