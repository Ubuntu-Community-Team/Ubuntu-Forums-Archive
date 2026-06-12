---
title: "logitech Wireless Number Pad keys =() is not working!"
date: 2012-01-22
forum: Hardware
---

### Post by paalfe on 2012-01-22
I have both the old and the new logitech Wireless Number Pads and every key except =() is working on both! Can somebody help me to get them working?

the new one, logitech Wireless Number Pad N305:
[http://www.logitech.com/en-au/434/6355](http://www.logitech.com/en-au/434/6355)

the old one, Logitech Cordless Number Pad for Notebooks:
[http://reviews.logitech.com/7061/3075/logitech-cordless-number-pad-for-notebooks-reviews/reviews.htm](http://reviews.logitech.com/7061/3075/logitech-cordless-number-pad-for-notebooks-reviews/reviews.htm)

I am running ubuntu 11.10 x64

---

### Post by paalfe on 2012-01-31
I tried hidpoint, but it did not help.

overview: [http://www.hidpoint.com/hidpoint/overview/overview.html](http://www.hidpoint.com/hidpoint/overview/overview.html)
HIDPoint can be considered as a Linux version of Logitech&#8217;s or Microsoft&#8217;s Keyboard and Mouse configuration software.

download: [http://www.hidpoint.com/hidpoint/download.html](http://www.hidpoint.com/hidpoint/download.html)
[IMG]http://s16.postimage.org/s9ust5udx/hidpoint_img.png[/IMG]



installing hidpoint: [http://www.hidpoint.com/hidpoint/support/installing-hidpoint.html](http://www.hidpoint.com/hidpoint/support/installing-hidpoint.html)


```

sudo apt-get install libpng3 libtiff4 ia32-libs 
sudo ln -s /lib32/libpng12.so.0 /lib/libpng.so.3
chmod +x hidpoint1-0.bin
sudo ./hidpoint1-0.bin

```

Reboot the machine after installation for HIDPoint to detect devices.

---

### Post by No137946 on 2012-06-13
I had the same problem on Ubuntu 10.10 I tried hidpoint but didn't solve the issue. I'm using Ubuntu 12.04 now and it still has the same problem. The device works out of the box in Windows 7 but the =() still don't work. It looks like it still is an unresolved issue. Please somebody help.

---

### Post by luc765 on 2012-10-16
Hello,

Follow the tuto given by this URL to have your logitech N305 working 100%.
Its in french but easy to understand

[http://users.skynet.be/linux-rixensart/3_peripheriques.html#keypad](http://users.skynet.be/linux-rixensart/3_peripheriques.html#keypad)

Lucien

---

