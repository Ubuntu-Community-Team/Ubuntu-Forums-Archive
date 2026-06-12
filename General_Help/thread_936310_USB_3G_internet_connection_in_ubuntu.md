---
title: "USB 3G internet connection in ubuntu?"
date: 2008-10-02
forum: General Help
---

### Post by Dalstal on 2008-10-02
Hello!
I was wondering if there is anyone out there who could help me solve this problem:
I have a USB 3G internet connection (one of those Mobile broadband's) and to use it you need to run a program wich is included on the USB unit, but the software is made for windows (I think it is a .exe file). Is there any way I could make it work in ubuntu?
At the moment I'm using XP (and hating every minute of it) since I can't access the internet using ubuntu if I can't get this modem working (it is a HUAWEI HSDPA USB Modem [http://www.huawei.com/mobileweb/en/products/view.do?id=282](http://www.huawei.com/mobileweb/en/products/view.do?id=282))

---

### Post by Redptc on 2008-10-02
If you search for 'Huawei' in this forum you will get a lot of answers to your question. 

Generally, what country are you in and what PC are you using?

---

### Post by Dalstal on 2008-10-02
Im from sweden (my connection operator is "3") and i'm using an acer extensa 5420G

---

### Post by cpetercarter on 2008-10-02
If your modem is a Huawei E220, have a look at [this how-to]("http://ubuntuforums.org/showthread.php?t=843973").

---

### Post by Redptc on 2008-10-02
Download GnomePPP from Synaptics

Start it up and let it detect the device, it will be something like /dev/tty/USB0, use USB modem as type, 460800 as speed.

For username and password I used   '', ( I think you can use what you like)

for phone number use *99#

click connect!

---

