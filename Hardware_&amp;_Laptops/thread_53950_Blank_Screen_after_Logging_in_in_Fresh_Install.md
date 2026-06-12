---
title: "Blank Screen after Logging in in Fresh Install"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by superchar42 on 2005-08-02
I have tried MANY times to get this working right. 
I know it's got to be something about "seeing" my monitor, but here it is.

I'm on a ThinkPad 600X, 192mb of ram. 

I've done a fresh install with the DVD version and with the CD version of Hoary. Warty worked fine, but I wanted to use a more updated version... hm. 

Installation goes fine, after I log in as a user I get a cursor over a black screen. I can choose to go into the failsafe terminal mode, but I've no clue what commands to use, xorgconfig got me SOMEWHERE but I don't know anything about refresh rates and all and don't want to screw anything up. 

Any ideas?

---

### Post by amohanty on 2005-08-03
This might help:

[http://www.io.com/~manojk/linux-tp600x/](http://www.io.com/~manojk/linux-tp600x/)

Look at the XF86Config file (link in text) to determine your refresh rates and syncs..

HTH
AM

---

### Post by superchar42 on 2005-08-03
Thanks. I got it figured out not too long ago. acpi=off did the trick. :)

---

