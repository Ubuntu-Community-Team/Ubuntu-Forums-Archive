---
title: "R1E tablet support?"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by Gentist on 2007-12-28
I'm trying to install Ubuntu on my Asus R1E notebook. So far, I think I've gotten everything to work (had to set SKIP_CHECKS=yes in ~/.config/compiz/compiz-manager since the driver is a bit buggy when using compiz and trying to play media files).

However, I haven't gotten the most important feature to work, namely the tablet function. As far as I know, the tablet module is a wacom module, so I thought it'd work out of the box. However, there is no /dev/input/wacom, and I've found nothing relevant in dmesg.

I'm running out of ideas. I might try to install the latest drivers manually, but other than that, I can't come up with much else. Ideas or hints would be appreciated.

Edit: output of lsusb shows my tablet module:
```

$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 003: ID 08ff:1600 AuthenTec, Inc. 
Bus 005 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 056a:0090 Wacom Co., Ltd 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

```

---

### Post by axsys on 2008-01-02
the r1e and r1f both use a usb interface to connect the tablet part of the screen. most other tablets use a serial interface, and unfortunately, the linux wacom drivers dont support the usb interface. it would be so nice to use the tablet features in ubuntu on our r1's......

---

### Post by Skuff on 2008-01-03
i've got the same problem. I hate running XP or Vista to do my tablet-stuff. that's getting me down. :sad:

---

### Post by Gentist on 2008-01-04
Yeah, and according to [this]("http://www.nabble.com/usb-tablet-pc%3A-how-to-start-development--td10457863.html"), it doesn't appear to be quite as easy to add support for it as it would be with a regular USB tablet. I tried poking around the source code, but with the little understanding I have of the Linux Kernel, I haven't been able to produce any results.

---

### Post by lvanderree on 2008-05-17
According to this: [https://sourceforge.net/tracker/index.php?func=detail&aid=1593330&group_id=69596&atid=525127](https://sourceforge.net/tracker/index.php?func=detail&aid=1593330&group_id=69596&atid=525127) there should be some kind of driver already.

I haven't got a Asus R1E, so can't test it for you... (my Toshiba m200 still uses a serial connection)

---

