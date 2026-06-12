---
title: "Canon LBP-1120"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by Dennis Laumen on 2005-10-24
Hi,

I've been trying to get a printer running on the Breezy Badger (x86). It's the Canon Lasershot LBP-1120. I have tried installing it with these [http://www.boichat.ch/nicolas/capt/](http://www.boichat.ch/nicolas/capt/) and the official drivers from Canon.

I think the Canon drivers aren't really working but I could be mistaken (they are RPM's so I had to convert them with with Alien first).

If anybody can help me (or tell me this printer just simply isn't gonna work) I would really appreciate it.

Dennis

---

### Post by fulano2040 on 2006-04-26
well after a long time i finally make work this printer this how i did it
1 dowload the file capt-0.1.tar.gz from [http://www.boichat.ch/nicolas/capt/]("http://www.boichat.ch/nicolas/capt/")
2 extract the file with file roller(just double click)
3 open a terminal window and write 
#sudo su
<type your password>
change folder to that where you extractec the file an type
#make
#make install
#modprobe usblp
#chmod a+rw /dev/usb/lp0
#/etc/init.d/cupsys restart
then you have to go to
System -> Admin -> Printers-Add new printer
type of printer -> local printer
[COLOR="Red"]dont select use detected printer[/COLOR]
select -> use other printer from port
USB Printer #<number> (Canon Laser Shot lbp-1120)
click next
Manufacturer Canon
and select the printer lbp-810
and thats all
i hope thi work for all you

---

