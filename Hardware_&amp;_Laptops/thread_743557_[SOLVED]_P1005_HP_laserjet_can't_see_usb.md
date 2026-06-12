---
title: "[SOLVED] P1005 HP laserjet can't see usb"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by bcn17 on 2008-04-02
HOW TO get an HP P1005  printer working in 7.10 [http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html) 
these instructions are in the further reading, a bit of an amendment to the front page linked above.
* If you get the print manager up and running (the last step initializes it or system - administration - printing) and can't see the usb option check that the correct usb cord from the pile of cords on your desk is plugged in ;) ....
     
        $ sudo apt-get install build-essential
	$ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
	$ tar zxf foo2zjs.tar.gz
	$ cd foo2zjs
	$ sudo make uninstall
	$ make
	$ ./getweb P1005
        $ sudo make install install-hotplug cups
        $ sudo system-config-printer

select new printer and click the usb option

---

