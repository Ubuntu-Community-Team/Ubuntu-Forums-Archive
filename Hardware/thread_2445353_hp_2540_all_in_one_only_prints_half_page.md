---
title: "hp 2540 all in one only prints half page"
date: 2020-06-12
forum: Hardware
---

### Post by tuesdaybarrett on 2020-06-12
I'm using Ubuntu 20.04 and have a Hp 2540 all in one printer. I installed hplip 3.20.5. I tried unplugging it and then connected it to wall outlet. I tried this several times but it only prints 1/2 page. I even uninstalled and remove it and then reinstalled it. then I unplugged it &etc to no avail.ny help would be appreciated.

---

### Post by tuesdaybarrett on 2020-06-12
My hp all in one only prints a half page of pdf. any help and *&#8203;I would be grateful.*

---

### Post by QIII on 2020-06-13
Threads merged.  Please to not create duplicate threads.

---

### Post by ajgreeny on 2020-06-13
Check the default paper size using the printer  setup dialogue from cups.

---

### Post by tuesdaybarrett on 2020-06-13
I checked the print paper size & it is set to 8.5 by 11. With hplip 3.20.5 I got communication device error 5012 as well. So I added hlip-data-3.20.5+dfsg0-3_all.deb to this system. I went to print and still only get 1/2 page of pdf file. any suggestions or help is greatly appreciated

---

### Post by tuesdaybarrett on 2020-06-15
i used [COLOR=#242729][FONT=Consolas]lpoptions -l to check on paper size i'm using.this is what i got 
[/FONT][/COLOR]PageSize/Media Size: Card4x6 Photo4x6 Photo4x6tab A6 Hagaki Card5x8 Photo2L Oufuku Photo5x7 Photo13x18 A5 6x8 Mutsugiri 8x10 FLSA B5 JB5 Executive Legal Photo10x15 Photo10x15tab A4 *Letter Statement EnvDL EnvC6 EnvC5 EnvCard EnvChou3 Env10 Custom.WIDTHxHEIGHT
InputSlot/Media Source: *Auto Main
ColorModel/Output Mode: CMYGray KGray *RGB
MediaType/Media Type: *Plain Photo
It doesn't show  regular paper size of 8.5x11
How do add this size for printer recognition?

---

### Post by ajgreeny on 2020-06-16
Go to [http://localhost:631/](http://localhost:631/) in a web-browser and you should be able to set the default paper size in the Administration tab, Printer management page.

---

