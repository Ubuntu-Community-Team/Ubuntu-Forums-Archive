---
title: "v4l-dvb and quickcam module"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by povvy on 2007-02-23
Hi all, I own an old logitech quickcam, wich works very well and a brand new dvb device; in my kubuntu 6.10 both work without problems, but not with the same kernel; I mean: 

-fresh install
-quickcam ok
-compiling v4l-dvb 
-putting the firmware in the right place
-dvb device works
-quickcam does not

It's a known problem, v4l is prepared for an hibryd 2-6-17 - 2.6.20 kernel, and some modules after its compilation does not work. There's also a solution, [http://www.mail-archive.com/linux-dvb@linuxtv.org/msg21319.html](http://www.mail-archive.com/linux-dvb@linuxtv.org/msg21319.html) but does not work for quickcam module. Anyone has idead on how to solve this problem? Have I to wait until new versione of quickcam comes out?

thanks

---

### Post by dinoj on 2007-04-12
Hi, 
Did You find any solution?
You can try to compile gspca driver, not spca5xx 
[http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz)
This is work for me with K(Ubuntu) 6.10
But I have same problem with feisty (2.6.20 kernel).

---

