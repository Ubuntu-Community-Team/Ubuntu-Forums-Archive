---
title: "fn keys on toshiba m105 [Edgy Eft]"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by Vega on 2006-10-30
I'm impressed with this release on how much hardware got supported but there's one minor important thing.

The fn keys to control screen brightness and to turn off/on volume controls don't work. 


I've posted screen caps of the machine if it helps any

[[img]http://i111.photobucket.com/albums/n148/InoriZ80/ubuntu/th_DSCF0978.jpg[/img]](http://i111.photobucket.com/albums/n148/InoriZ80/ubuntu/DSCF0978.jpg)[[img]http://i111.photobucket.com/albums/n148/InoriZ80/ubuntu/th_DSCF0980.jpg[/img]](http://i111.photobucket.com/albums/n148/InoriZ80/ubuntu/DSCF0980.jpg)[[img]http://i111.photobucket.com/albums/n148/InoriZ80/ubuntu/th_DSCF0983.jpg[/img]](http://i111.photobucket.com/albums/n148/InoriZ80/ubuntu/DSCF0983.jpg)[[img]http://i111.photobucket.com/albums/n148/InoriZ80/ubuntu/th_DSCF0984.jpg[/img]](http://i111.photobucket.com/albums/n148/InoriZ80/ubuntu/DSCF0984.jpg)[[img]http://i111.photobucket.com/albums/n148/InoriZ80/ubuntu/th_DSCF0985.jpg[/img]](http://i111.photobucket.com/albums/n148/InoriZ80/ubuntu/DSCF0985.jpg)

---

### Post by yachoo on 2006-11-16
I have the same problem with my Toshiba a105-s4004. There is nothing mentioned about it on [www.linux-laptop.net](www.linux-laptop.net). I've heard that problem with fn keys on that notebooks is becouse of Phoenix BIOS. I've also read about omnibook kernel patch ([http://omnibook.sourceforge.net/doku.php](http://omnibook.sourceforge.net/doku.php)), but I can't add it to my source. It may be, that I don't know how to do it, becouse I was compiling kernel just few times in my life. If you would be so kind, as to try and give me an answer if it's working?
On my laptop it'll allow me only to change brightness, but I don't need more.

PS
Sorry for my bad english.

---

### Post by zasf on 2006-12-03
thanks for the omnibook suggestion, I used s1bl for lcd dimming but omnibook module is much better. On my Toshiba Satellite M40-281 omnibook module also cover wifi/bluetooth enable/disable, hotkeys support, vga/svideo plugs and lcd brightness dimming.

Now I only need to know how to assign these functionalities to fn keys, any ideas?

btw, omnibook is pretty simple to use, you only need to compile it (make), then install and load (sudo make install, sudo make load), and it works (e.g. echo 7 > /proc/omnibook/lcd)

---

