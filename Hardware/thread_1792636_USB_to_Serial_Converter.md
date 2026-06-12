---
title: "USB to Serial Converter"
date: 2011-06-28
forum: Hardware
---

### Post by Castania on 2011-06-28
Hi folks.

I've been using Fedora for several years, but have decided to switch over to Ubuntu Natty.  So far, so good.  

I have a Dell Inspiron (64bit) that did not come with a 9-pin serial port, but (of course) I have an application that needs this:  a Casio calculator program.  (I'm a math teacher.)  I followed the instructions at this website:

[http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html](http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html)

and everything works great . . . _except_, if I add the line 

      [CENTER]***usbserial vendor=0x067b product=0x2303***
[/CENTER]

to the /etc/modules file, I cannot get the program to work.

However, if I omit the change to /etc/modules and just enter

      [CENTER]***sudo modprobe usbserial vendor=0x067b product=0x2303***
[/CENTER]
 
from the command line, then everything works like a charm?!?!

What am I doing wrong?:confused:

Ken

---

### Post by Castania on 2011-06-28
Should this be in quotations marks?

Hmmm . . . apparently so.

---

