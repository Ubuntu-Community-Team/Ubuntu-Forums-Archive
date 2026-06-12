---
title: "How to tell what devices (reported by lsinput) use for a driver?"
date: 2011-05-29
forum: Hardware
---

### Post by lumix on 2011-05-29
So if I see:

> /dev/input/event9
   bustype : BUS_USB
   vendor  : 0xc45
   product : 0x76f4
   version : 256
   name    : "SONiX USB Keyboard"
   phys    : "usb-0000:00:16.2-1.2/input1"
   uniq    : "0131"
   bits ev : EV_SYN EV_KEY EV_REL EV_ABS EV_MSC


Then 

A) How do I find out what driver this is using?  I don't want to know what the driver is right now, I just want to know how to discover or identify it.  Also, I don't want to know what xorg.conf.xyz has *tried* to assign to it, I want to know *what is actually using.*

B) What's an EV_ABS, or EV_SYN

Thanks.

---

### Post by lumix on 2011-05-30
Figured it out.

---

