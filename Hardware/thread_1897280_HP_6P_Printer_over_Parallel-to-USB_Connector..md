---
title: "HP 6P Printer over Parallel-to-USB Connector."
date: 2011-12-18
forum: Hardware
---

### Post by melee27a on 2011-12-18
I have a Dell Vostro laptop with 10.04 with a few USB ports (and obviously no parallel ports), and I'm trying to set up my old HP Laserjet 6P printer to work with it.  I have a cheap parallel-to-USB cable.  After a few hours, I can get the printer to print garbage, but no more.  

I've tried following instructions here: 
[http://ubuntuforums.org/showthread.php?t=894223&page=11]("http://ubuntuforums.org/showthread.php?t=894223&page=11")

So in summary, if I try to add a new printer under System->Admin->Printing, and add a printer:
URI: 'usb:/dev/usb/lp0'
Driver: 'HP Laserjet 6p hpijs, 3.10.2'

Then if I click print test page AND go to a terminal and type

```
lpadmin -p HP-Laserjet-6p -E -v file:/dev/usb/lp0
```

(which I found on the internet somewhere :) ) then it will print garbage for a while.  

Any leads?

also, lsusb returns:
...
Bus 002 Device 005: ID 4348:5584 WinChipHead  CH34x printer adapter cable
...

Thanks!

---

### Post by melee27a on 2011-12-21
bump!

---

### Post by bluexrider on 2011-12-21
have you tried CUPS to see if it locates the printer? [http://localhost:631](http://localhost:631)

---

### Post by melee27a on 2011-12-21
I hadn't, thanks.

Here's what happens:

--Under Administration -> Find New Printers, the printer shows up as HP Laserjet 6P (a good sign!).
--The "connection" was usb://HP/LaserJet%206P (which I can't seem to change in CUPS), and the driver was "HP LaserJet 6P - CUPS+Gutenprint v5.2.5".
--I installed normally.
--I tried to print a test page, nothing came out and I got the message "Unable to write print data: Input/output error".

Thanks for the help.

---

### Post by melee27a on 2011-12-23
help!

---

