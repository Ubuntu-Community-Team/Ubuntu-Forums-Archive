---
title: "AWN Issue"
date: 2008-09-14
forum: General Help
---

### Post by chuuk on 2008-09-14
I installed AWN yesterday to have a look at it (have only been using Ubuntu for a few months now), but I find it doesn't load. A rectangular application box appears on the top left of the screen for a flash, and then disappears.
The same thing happens when I try to use Pidgin.

Anyone know what the issue could be? Is the AWN issue linked to Pidgin, or are they separate?

It might just be that my graphics card can't handle AWN, I'm running a 5 year old laptop...

Any tips appreciated.

---

### Post by tuxxy on 2008-09-14
Have you got compiz enabled

---

### Post by chuuk on 2008-09-14
Nope. I found something on the net to enable it, I follow that?
[http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200](http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200)

chuuk@chuuk-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
chuuk@chuuk-laptop:~$ compiz
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 

I tried following the instruction on that website for enabling Compiz, but there was nothing in the Hardware Manager about my graphics card. What do I do now?

---

### Post by tuxxy on 2008-09-14
Yes enable compiz, if your video card driver is installed then you can enable compiz at **system > prefs > appearance > desktop effects**

EDIT: That guide you linked is not for your graphics card, try and enable the driver at **system > admin > hardware drivers**

---

### Post by chuuk on 2008-09-14
> **tuxxy said:**
> Yes enable compiz, if your video card driver is installed then you can enable compiz at **system > prefs > appearance > desktop effects**

EDIT: That guide you linked is not for your graphics card, try and enable the driver at **system > admin > hardware drivers**

There's nothing to enable in Hardware Drivers, the box is blank.

---

### Post by tuxxy on 2008-09-14
Try the app **envyng** then, this will hopefully install the correct driver for your ATI card, open a terminal and type

```
sudo apt-get install envyng-gtk
```

---

### Post by chuuk on 2008-09-14
> **tuxxy said:**
> Try the app **envyng** then, this will hopefully install the correct driver for your ATI card, open a terminal and type

```
sudo apt-get install envyng-gtk
```

"Envy does not recognise your card as compatible with any version of the driver."

I'll try the manual install?

---

### Post by tuxxy on 2008-09-14
Read the guide also

[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

---

### Post by chuuk on 2008-09-15
> Make sure the following things are true about your video card: 
It is a 'Radeon' card 
The model of the card is in the 9xxx series, 9500 or higher, or it is in the X series (e.g. X300), or it has TV-Out capability. The 'fglrx' driver does not support cards earlier than the 9500.

Looks like I won't be able to support it anyway.
Anyone know if the Dell Inspiron 1525 can handle it?

---

