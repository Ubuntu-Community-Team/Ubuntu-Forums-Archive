---
title: "Can I have a Jaunty app. in Dapper?"
date: 2009-10-01
forum: Hardware
---

### Post by darkworld on 2009-10-01
Old laptop ran Dapper fine but I could not get online with my usb modem dongle. Then jaunty came along and it does all the network connection for you......so I loaded xubuntu jaunty onto my old laptop and hey presto I was online. 

However my laptop is a pentium 3 and it struggles a bit with xubuntu jaunty. Is it possible to run dapper but get the app from jaunty that loads up the usb modem dongle????

---

### Post by markbuntu on 2009-10-02
You would most likely run into huge dependency problems. If you could scare up some more ram for that machine you would get far better performance.

---

### Post by tgalati4 on 2009-10-02
Try running hardy.  It's a long-term support release and it may work as well.  You need at least 512 MB of ram to get smooth performance, otherwise it's a chore to use.

Dapper is too old to support any of the frameworks used in Jaunty, so backporting applications will be a chore.

If you are dual-booting with dapper, figure out what module is loaded recognize the usb modem and load it manually:

sudo modprobe usbmodemmodulethatyoufoundusinglsmodandlsusb

---

