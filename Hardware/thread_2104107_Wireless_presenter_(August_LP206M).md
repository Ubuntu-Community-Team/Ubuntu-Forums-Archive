---
title: "Wireless presenter (August LP206M)"
date: 2013-01-12
forum: Hardware
---

### Post by Englishman12345 on 2013-01-12
Hi

I'm enthusiastically trying to abandon Windows so I'm try to iron out the few things holding me back.

I have a USB wireless presenter (labelled as August LP206M)
 [IMG]http://di1-1.shoppingshadow.com/images/pi/21/e1/02/122427943-149x149-0-0_august+electronics+august+lp208m+wireless+presente.jpg[/IMG]
It doesn't seem to do anything with Ubuntu. 

I run Virtualbox with Windows XP and that recognises the device as a "XinXin" USB presenter.

Under windows I can use the arrows to guide the mouse and the buttons and right and left click.

On another setting I can use it to switch Powerpoint slides (I think it sends a "Page up, Page down" signal.)

Is there anything I can do to get any of the functions? Just switching slides in PPT/Impress would be fantastic.

I'm not an advanced user but I can copy and paste things into Terminal! 

Thank you in advance for your efforts.

---

### Post by Englishman12345 on 2013-01-12
I ran "lsinput" and got the following information.

Can I do anything (manually??) to get some buttons to work?

> /dev/input/event9
   bustype : BUS_USB
   vendor  : 0x1d57
   product : 0x4173
   version : 272
   name    : "XinXin Wireless Presenter"
   phys    : "usb-0000:00:1d.2-1/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event10
   bustype : BUS_USB
   vendor  : 0x1d57
   product : 0x4173
   version : 272
   name    : "XinXin Wireless Presenter"
   phys    : "usb-0000:00:1d.2-1/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_REL EV_ABS EV_MSC


thanks in advance

---

### Post by Englishman12345 on 2013-01-12
SOLVED

I changed the batteries in the presenter unit :oops:

---

