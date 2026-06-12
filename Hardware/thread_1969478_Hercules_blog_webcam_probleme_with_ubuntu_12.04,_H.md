---
title: "Hercules blog webcam probleme with ubuntu 12.04, HELP PLZ !!!!"
date: 2012-04-30
forum: Hardware
---

### Post by foooudre on 2012-04-30
hello my friends;
i have a probleme with my hercules blog webcam after upgrading my ubuntu from 10.10 to 12.04
in maverik no problem with gspca drivers but now with 12.04 the LED is always ON,and cheese , skype .... doesn't recognize my webcam
with lsusb commande all is ok my webcam is listed
after updating headers and instaling gspca driver from moinejf.free.fr my webcam still not working
any help my friends please

---

### Post by foooudre on 2012-04-30
> **foooudre said:**
> hello my friends;
i have a probleme with my webcam hercules after upgrading my ubuntu from 10.10 to 12.04
in maverik no problem with gspca drivers but now with 12.04 the LED is always ON,and cheese , skype .... doesn't recognize my webcam
with lsusb commande all is ok my webcam is listed
after updating headers and instaling gspca driver from moinejf.free.fr my webcam still not working
any help my friends please
I do not know what to do to make it work

---

### Post by foooudre on 2012-04-30
up!!

---

### Post by foooudre on 2012-05-05
no one ? :confused::icon_frown:

---

### Post by foooudre on 2012-05-05
here's the solution for my problem,
a very  big thanks to my friends "**Stemp**" and "**Jean-François moine**"

the solution by Jean-François moine : 
downloading the latest GSPCA driver at [http://moinejf.free.fr](http://moinejf.free.fr)/ 

adding this litle detail **"msleep(10);" **in **build/ov534.c at line N° **[B]837

like this: 
[/B][B]  for (i = 0; i < 5; i++) {
               data = ov534_reg_read(gspca_dev, OV534_REG_STATUS);[/B]

to this 
[B] for (i = 0; i < 5; i++) {
               msleep(10);
               data = ov534_reg_read(gspca_dev, OV534_REG_STATUS);

[/B]If it does not work, you can try to ignore the error
 to see if the webcam starts anyway. it is done at line 842 in
 changing "return 1;" to "return 0;"

                case 0x00:
                        return 0;

 Do not forget to purge the memory after regeneration

after this use "**make**" **and** "**sudo make install**"

for me the first solution work fine ;)

thanks my friends

---

