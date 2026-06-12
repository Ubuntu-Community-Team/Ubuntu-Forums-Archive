---
title: "Ralink USB Wifi and Master Mode"
date: 2010-11-05
forum: Hardware
---

### Post by Ragade on 2010-11-05
So I purchased this to be able to have my NDS go online.
[http://www.amazon.com/gp/product/B00333AWTA/ref=oss_product](http://www.amazon.com/gp/product/B00333AWTA/ref=oss_product)

It came with a disk with multiple drivers; I tired 2070, with no luck in ubuntu or Windows in creating an infrastructure access point.

Does anyone have any work arounds (I've been told to try ndis wrapper) or know the chipset for this little dongle?
tried sudo iwconfig
results in 
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on


```
Which does not really help.
Assistance is much appreciated.

---

### Post by P4man on 2010-11-05
I dont know how to create an access point, but you can find out the chipset by opening a terminal and typing in

```
lsusb
```

---

### Post by Ragade on 2010-11-05
That brings me 
```
 
Bus 001 Device 006: ID 148f:3070 Ralink Technology, Corp.

```

Which I assume means it's a 3070 chipset? I guess I'll try ralink's linux drivers before I resort to ndis wrapper.

---

