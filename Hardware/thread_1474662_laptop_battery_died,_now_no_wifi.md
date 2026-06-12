---
title: "laptop battery died, now no wifi"
date: 2010-05-06
forum: Hardware
---

### Post by nal13 on 2010-05-06
I have an Hp mini 1000 and have been running ubuntu on there for a year now, I have always had problems getting the wireless to work. I have been running 10.04 since the day it was released, everything installed nicely and has been running good until this morning. So in an attempt to "recondition my battery" last night, I drained my battery all the way. This morning I went to turn on the netbook and the wireless wasn't working. I tried reinstalling the drivers, but it wouldn't. So now I'm reinstalling ubuntu 10.04 and I guess I can't let my battery die. Can someone maybe shed some light on this or else explain what's going on? Also, could I just buy another wireless card and replace it with one works better with ubuntu? If so, may I get some suggestions on brand or model.


edit: I should add I have a broadcom wireless card

---

### Post by ugutugut on 2010-05-06
Check if network device and driver enable
    sudo lshw -c network

Check if wireless device exist
   iwconfig

if wireless device exist, then try to scan
   sudo iwlist wlan0 scan

---

### Post by nal13 on 2010-05-06
> **ugutugut said:**
> Check if network device and driver enable
    sudo lshw -c network

Check if wireless device exist
   iwconfig

if wireless device exist, then try to scan
   sudo iwlist wlan0 scan

I will next time. I already installed 10.04 again. Thanks though.

---

### Post by nal13 on 2010-05-06
No recommendations for a more compatible linux wireless card for my hp mini?

---

