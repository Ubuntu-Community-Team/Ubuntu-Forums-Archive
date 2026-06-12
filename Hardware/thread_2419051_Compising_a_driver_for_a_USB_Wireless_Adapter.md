---
title: "Compising a driver for a USB Wireless Adapter"
date: 2019-05-15
forum: Hardware
---

### Post by wjbmd48 on 2019-05-15
Hi All:

So, I purchased a Cudy wu600 ac wireless adapter, and failed to notice that it didn't support Linux. My bad: I can't in good conscience ask for a refund.

lsusb identifies it as 

Bus 002 Device 003: ID 0bda:1a2b Realtek Semiconductor Corp.

Is it possible, given this ID, to compile a driver for it myself. For example, I also have and EDUP adapter, and after browsing the forum came up with the below terminal command sequence that installed it. Might there be a similar procedure for the above device?

sudo apt install git dkms
git clone [https://github.com/gnab/rtl8812au.git](https://github.com/gnab/rtl8812au.git)
sudo cp -r rtl8812au  /usr/src/rtl8812au-4.2.2
sudo dkms add -m rtl8812au -v 4.2.2
sudo dkms build -m rtl8812au -v 4.2.2
sudo dkms install -m rtl8812au -v 4.2.2

Thanks!

Bill

---

