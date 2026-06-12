---
title: "Printer driver for FX Document Centre 186"
date: 2010-05-07
forum: Hardware
---

### Post by obakasan on 2010-05-07
My environtment:
Netbook Sony Vaio VGN-TZ190N
Ubuntu 10.04

Trying to get this printer works.

The driver isn't listed in the printer driver list. I've tried some of Generic driver (not all) but to no avail. 

Please help. Thanks in advance.

---

### Post by obakasan on 2010-05-09
It's been days since the post's been posted but no replies. I supposed there's no driver for that printer?

---

### Post by him610 on 2010-05-09
Actually, you were not quite forthcoming with all of your printer specs, for instance the manufacturer; however, I looked it up and found out the FX stands for Fuji-Xerox. 
You may not be able to find a driver specifically written for your particular printer model, but you may be able to use a driver for a similar printer from the manufacturer(s.)
A listing of linux compatible printers can be found at [http://www.openprinting.org/printers]("http://www.openprinting.org/printers") where you can find printers listed from Fuji and Xerox. You may have to revert to some trial and error to determine which if any of the drivers works for you.
If all else fails, you might try configuring with generic raw in CUPS.

Good luck

---

### Post by obakasan on 2010-05-09
well, before I posted I've searched the driver and found the PPS file in [[COLOR="Blue"]here[/COLOR]]("http://onlinesupport.fujixerox.com/processDriverForm.do?ctry_code=ID&lang_code=en&d_lang=en&corp_pid=DC186&rts=1&model=Document+Centre+186&oslist=all&selected=Go"). It's an online support for Fuji Xerox printers. But still, cant use it. The printers just sucked the paper in and out, but doesn't print the text whatsoever. Odd indeed.

Btw, thanks for the link you gave me hgh9mrp, I'll try it out

---

### Post by him610 on 2010-05-10
I in the list of drivers on the link you posted there is a PCL6 driver listed which means that you may be in luck. Quite a few printer manufacturers use the HP PCL drivers.
I have a Dell 1700n for which there are no drivers in Linux; however, it prints quite well using the driver described as Generic-PCL-6-PCL-XL-Printer. It may be possible for you to configure yours in CUPS using the same generic driver.

Good luck.

---

### Post by obakasan on 2010-05-17
after a lot of trial and error, I've succeed to print with Document Centre 400 driver.

But only with Open Office. Print with Test Print and Gedit failed :(

I think this problem is partially resolved.

---

