---
title: "Video Card: VIA PN800"
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by neonfx on 2007-10-06
Hi, i have a VN896 VIA Chrome9™ HC integrated graphics video card on an MTECH 665SE and i cant seem for the life of me to get it to work right in Ubuntu. Xorg is reading it as a compatible card and is only letting me run it under 1024x768 where it can use 1280x800. not only that... but when i log off the screen will go black, but i know everything else is working cause i can type my username and password and when i hit enter i get the welcome music.

When i run Puppy Linux off my thumb drive it uses xvesa and it loads the correct resolution. only i cant figure out how to do this in ubuntu.

i found this: which seems to be the drivers for it, only either i dont know how to install them, or they're just not the right ones
[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=185](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=185) 

thanks to whoever can help.

---

### Post by kecsap on 2007-10-11
I can't compile the official VIA driver in Feisty too, because the Xorg version is different what is supported by the driver.... :(

Use the experimental branch of OpenChrome driver! My laptop has VN896 and it works in 1280x800. :) No 3D-acceleration, but works.

[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Work%20In%20Progress](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Work%20In%20Progress)

---

