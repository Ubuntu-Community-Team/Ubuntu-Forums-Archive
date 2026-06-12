---
title: "very strange problem 7.04"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by gotha on 2007-06-24
Hallo everybody,
I have Asus a9rp notebook, but when I installed Ubuntu 7.04 very strange problem appears - the notebook just freezes after half an hour working(not exactly half an hour of course). Everything freezes and can`t move the mouse or type anything. Under M$ Window$ I dont have such a problems, so I think my hardware is OK but Ubuntu can`t cope with this hardware. So here it is:
> 
ASUSTeK Computer Inc. A9Rp 1.0
Board: ASUSTeK Computer Inc. A9Rp 1.0
    Bus Clock: 133 megahertz
896 Megabytes Installed Memory
    Slot 'DIMM0' has 512 MB (serial number SerNum0)
    Slot 'DIMM1' has 512 MB
1,87 gigahertz Intel Celeron M 440
    64 kilobyte primary memory cache
    1024 kilobyte secondary memory cache
ATI RADEON XPRESS 200M Series
Realtek RTL8139/810x Family Fast Ethernet NIC
Linksys Wireless-G Notebook Adapter WPC54G Ver.3

Some people told me to install fglrx drivers for the video card but nothing changes, it`s all the same.
Could you tell me where is the problem ?
I don`t want to use Window$ till the end of my life !!! ;)

P.S. I am sorry for my english, I suppose I have many mistakes but this is not my mature language and I am still learning. I hope you understand me.

---

### Post by Talon2 on 2007-06-24
Your English is good.

My first guess would be a RAM problem.  The Ubuntu installation CD boots up to a menu.  On this menu there is a memory checker utility option.  Recommend you run the memory checker.

---

### Post by xenoph0be on 2007-06-24
Another thing to check is if your processor is overheating.

You can download and install the following app:
[http://computertemp.berlios.de/]("http://computertemp.berlios.de/")

There is a link for a feisty package.  You can configure the applet to log to a file so that if your pc is locking up due to overheating you can check to see what the CPU temp was shortly before the computer locks up.

---

### Post by gotha on 2007-06-25
Memtest show absolutely no errors. 
When I installed computertemp and started it in the gnome-terminal appears this message:
> 
(computertemp:5751): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

and nothing happens.

Any other ideas ?

---

### Post by xenoph0be on 2007-06-25
> **gotha said:**
> Memtest show absolutely no errors. 
When I installed computertemp and started it in the gnome-terminal appears this message:

and nothing happens.

Any other ideas ?

Its a gnome panel applet.  
right click any gnome panel click 'add to panel...' 
scroll down to' system & hardware' 
click and drag 'computer temperature monitor' to a gnome panel.
right click new icon and go to preferences and you can set how you want it to work there.

Jacob

---

### Post by gotha on 2007-06-28
oh, thanks, now it works but the temperature is 58 degrees C. When I am playing warcraft 3 with wine it rises to 65 degrees and no more. I think this is normal temperature of the CPU.

---

