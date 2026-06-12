---
title: "Detecting IMU using i2cdetect"
date: 2014-04-14
forum: Hardware
---

### Post by avu2 on 2014-04-14
Hi,
First of all, sorry for my English and limited ubuntu knowledge as I'm quite new to this OS.

I'm having a 9DOF([https://www.sparkfun.com/products/10724](https://www.sparkfun.com/products/10724)) IMU connectting to my fit-pc(ubuntu 12.04) directly through the usb-iss([http://www.tinyosshop.com/index.php?route=product/product&product_id=645](http://www.tinyosshop.com/index.php?route=product/product&product_id=645))  and NOT THROUGH THE ARDUINO. The problem I have is that when I use i2cdetect, it only can detect the address of the Gyroscope(working) chip but for the Accelerometer and Magnetometer it can't detect. Especially for the Accelerometer, when I used i2cdetect only for the first time after booting, it could detect it's address and I could not access to the Accelerometer using i2cdetect -y -0 0x53.

First time:
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: -- -- -- 53 -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- 68 -- -- -- -- -- -- -- 
70: -- -- -- -- -- -- -- --                         




This is the second time:

 0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- 68 -- -- -- -- -- -- -- 
70: -- -- -- -- -- -- -- --                         


I have done instantiating the devices using " echo ADXL345 0x53 > ...." but still not response from the accelerometer. For the Magnetometer, totally not response from it.

So I'm wondering is there any solution to get my ubuntu detect or the 3 addresses? Or is there any sample code(C,C++) for this?
 
Thank you and have a nice day

---

### Post by avu2 on 2014-04-15
Up...uppppppppp

---

