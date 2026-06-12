---
title: "Screen Flicker on Dell Inspiron 1150"
date: 2008-10-31
forum: Hardware
---

### Post by Patch Adams on 2008-10-31
I posted this at:

[http://ubuntuforums.org/showthread.php?p=6054184](http://ubuntuforums.org/showthread.php?p=6054184)

Before these threads were closed.

The screen rapidly flickers especially at the log in and password screens under Intrepid which wasn't a problem under Hardy. It seems to be isolated to Dell's Inspiron 1150 so far but is very annoying. 

Any Ideas would be appreciated

Thanks

---

### Post by Patch Adams on 2008-10-31
Like the other user affected said, the issue does not occur on battery power and the screen remains on with the lid closed.

---

### Post by Patch Adams on 2008-10-31
I think it must be something to do with the power manager but none of the settings make any difference, ie changing the brightness slider, it just stays at 100%. But using the keyboard shortcuts causes all manour of problems as things lock up

---

### Post by societyblind on 2008-11-02
I'm having the same screen flicker issue in Ibex, I assumed it was just a driver thing but displayconfig-gtk has been removed :( so I can't try to change it there.  I attempted to copy the device section from the xorg.conf of a hardy live cd on this computer which contains: 
```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Intel 85x"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection
```
but then the X-server fails to load. Any help would be appreciated.

The screen flicker is less noticeable on lower brightness settings but still significant.

---

### Post by Patch Adams on 2008-11-02
I just tried messing about with the xorg.conf file and had to run dpkg-reconfigure xserver-xorg.

Neither helped and the flicker is as bad as ever

---

