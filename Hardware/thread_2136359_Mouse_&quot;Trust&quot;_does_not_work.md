---
title: "Mouse &quot;Trust&quot; does not work"
date: 2013-04-17
forum: Hardware
---

### Post by machinehater on 2013-04-17
Hey guys!
I've bought the mouse 17177-02 "Trust", this one: 

[http://www.trust.com/products/product.aspx?artnr=17177](http://www.trust.com/products/product.aspx?artnr=17177)

It does not work, turning of and on the computer or restarting the x-server does not help.
lsusb changes, if i plug in the mouse, this line is added:


Bus 004 Device 004: ID 0c45:0520 Microdia

Any chance to get the mouse working?
I am using precise pangolin

Thank you in advance!
Armin

---

### Post by machinehater on 2013-04-18
no one?

---

### Post by stinkeye on 2013-04-18
Give this a try.

In terminal...
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

and comment ([COLOR="#FF0000"]#[/COLOR]) the line
**blacklist usbmouse**

eg
```
# these drivers are very simple, the HID drivers are usually preferred
[COLOR="#FF0000"]#[/COLOR]blacklist usbmouse
blacklist usbkbd
```
Save and reboot.

If it doesn't work, revert the changes made to /etc/modprobe.d/blacklist.conf

---

### Post by machinehater on 2013-04-18
I am such an idiot, there was a plastic piece of plastic, preventing the battery to make contact.
sorry guys :-D

---

