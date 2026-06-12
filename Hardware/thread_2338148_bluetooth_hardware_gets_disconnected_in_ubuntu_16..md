---
title: "bluetooth hardware gets disconnected in ubuntu 16.04"
date: 2016-09-25
forum: Hardware
---

### Post by basel-sayeh on 2016-09-25
Hello
I've been trying to get bluetooth hardware to work in ubuntu 16.04
My wifi & bluetooth chip is Atheros qca9565
the bt chip gets disconnected during boot
here is my dmesg log
[http://pastebin.com/jVzSuXt7](http://pastebin.com/jVzSuXt7)
and it doesn't show in lsusb list 

idvendor:0489
idproduct:e095

in windows its working
and also in root shell in ubuntu recovery options it does show

edit:acer_wmi kernel module was the problem. after blacklisting it bluetooth worked perfectly

---

