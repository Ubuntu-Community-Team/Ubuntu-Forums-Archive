---
title: "canon Bjc 80 printer infrared irda connection"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by pet22 on 2006-10-23
HI everyone

I have an old good printer bjc-80. Just changed my laptop to IBM x41t so the only connection to the printer would by via ir. Looked everywhere on the web and in this forum and only info I would find is that infrared printing should work out of the box??? In the printers wizard there is only "bluetooth printers" and no irda option. 

Please any help would by very appreciated. ](*,) 

Piotr

---

### Post by pet22 on 2006-10-24
Since there was no one to help me I had to find my own way. Hope now it can be useful to some.
 
It involves a ubuntu bug.

after you put irda module in place (should come with the system install) and the driver for the printer, downloaded and compiled or installed from a repository you can start.

The problem is that after adding the modules there is no irda device in /dev/

What I did for my kubuntu 6.10 Edgy on my x41t is 

added the following to a file /etc/rc.local

before the line exit 0 I added:

mknod /dev/irlpt0 c 161 16
chgrp lp /dev/irlpt0
chmod g+w /dev/irlpt0

this is the making of the connection from core address to the device and than giving its proper rights to use for a system user.

Then simply create a new network printer and under the url write 

parallel:/dev/irlpt0

if you did install the latest driver which is called gutenprint, the version I used was 5.0 and it may come in the repositories (did for my edge settings I fiddled with so I'm not sure if it will come "out of the box"). Anyway, if you have it it will give you the option of picking up your printer and the driver.

Add it should work.

Hope it helps someone.

good luck to all the printer works perfect, Piotr

---

