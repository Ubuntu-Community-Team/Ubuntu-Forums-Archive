---
title: "Wifi for live usb"
date: 2010-04-11
forum: Hardware
---

### Post by oleink on 2010-04-11
I just started messing around with xubuntu on a live usb.  First thing i noticed was that drivers were available for wifi but it said it could not load them.  Is this because I didn't have xubuntu disk in but instead ubuntu disk or am i missing something

---

### Post by garvinrick4 on 2010-04-11
> **oleink said:**
> I just started messing around with xubuntu on a live usb.  First thing i noticed was that drivers were available for wifi but it said it could not load them.  Is this because I didn't have xubuntu disk in but instead ubuntu disk or am i missing something It will be in /etc/resolv.conf

2 ways to put it in your OS that you want to use in live cd. 

In GUI can copy from live cd file system in /etc/resolv.conf and paste it in the OS you are
want to get wifi access while it is in root GUI.

You can use code, use your own label (mine is lucid for this) your own sda # (mine is sda5 for this)

sudo mkdir /media/lucid

sudo mount /dev/sda5 /media/lucid

sudo cp /etc/resolv.conf /media/lucid/etc/resolv.conf

sudo chroot /media/lucid

#You now have a directory,mounted,wifi connection, in root.

---

### Post by oleink on 2010-04-12
Alright I'll try it out

---

### Post by oleink on 2010-04-13
Eh.. I gave up after a little while.  I knew if i spent some time i could get it working but i decided I wanted my usb to have full space capacity so I could just save my data on it.  Thanks though.  I reformated it

---

