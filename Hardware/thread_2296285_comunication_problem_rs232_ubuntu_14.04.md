---
title: "comunication problem rs232 ubuntu 14.04"
date: 2015-09-24
forum: Hardware
---

### Post by Richard Sandi on 2015-09-24
Buen día.

Hello

Im try to make comunication whith the rs232 serial port. But i can´t make the comunication.
Im install Cutecom but dosent work.
Cutecom give me  this error  Could not open/dev/ttyS0


  dmesg &#9130;grep tty 

 [ 0.000000] console [tty0] enable
[1.374425] 00:05 ttyS0 at I/O 0x3f8 (irq=4,base_baud=115200) is a 1655

 

 any help 

Regards

---

### Post by UncleBoarder on 2015-10-12
Same problem. Upgraded from 10.04. Same hardware previously worked with... I forget the name of the terminal program. 

So, on my 14.04 I also downloaded GtkTerm and it gave me an additional error of "Permission denied". SO... I changed to "sudo gtkterm" and it WORKED!

I certainly don't have all the answers as to how this should be fixed properly but this wokred for me.

Note: even GtKTerm didn't work from the GUI, I had to do it from command-line. Hopefully someone can provide additional instructions for a better solution.

I run 14.04 in Gnome-fallback.

---

### Post by UncleBoarder on 2015-10-12
Check this out... [http://askubuntu.com/questions/217871/cannot-open-dev-ttys0-permission-denied-but-in-dialout-group](http://askubuntu.com/questions/217871/cannot-open-dev-ttys0-permission-denied-but-in-dialout-group) 

add yourself to the dialout usergroup and it should work. :grin:

---

