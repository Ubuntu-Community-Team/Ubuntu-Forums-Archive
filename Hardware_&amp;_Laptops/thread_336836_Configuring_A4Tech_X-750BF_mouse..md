---
title: "Configuring A4Tech X-750BF mouse."
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by LeXz on 2007-01-12
I just bought [A4Tech X-750BF]("http://www.a4tech.us/product2.asp?CID=102&SCID=103&MNO=X-750BF") mouse.
"3xFire" button and dpi switching button works great, but those side buttons "forward" and "backward" don't work. Drivers are only for Win and Mac.
Is there a way to make those two buttons work in Ubuntu ?

---

### Post by qstraza on 2007-10-17
i just bought this mouse 2.
Any one knows how to edit xorg.conf to get the best of it?;>

---

### Post by Tosa on 2007-10-18
After some fiddling I've got it working with these settings:

"Protocol"               "EexplorerPS/2)
"Buttons"                "7"
"ZaxisMapping"       "4 5"
"ButtonMapping"     "1 2 3 6 7"
"Emulate3Buttons"  "false"

HTH!

---

### Post by qstraza on 2007-10-18
can u paste the whole xorg.conf?
i get error for the Eexplorer ....

---

### Post by SoulSmasher on 2008-02-18
it's a bit late, but ive a solution working for me..

i found [this italian guide]("http://natonelbronx.wordpress.com/2007/07/10/mouse-a4tech-x7-con-linux-facciamo-funzionare-tutti-i-tasti/"), and changed within help of google translator to my language, turkish, which is [here]("http://www.soulsmasher.net/ubuntuda-a4-tech-x7-gamer-mouse-buton-ayarlari/")

i'm planning to translate to english, but laziness keeps me on :D
hope this helps a bit

---

### Post by qstraza on 2008-02-18
> **SoulSmasher said:**
> it's a bit late, but ive a solution working for me..

i found [this italian guide]("http://natonelbronx.wordpress.com/2007/07/10/mouse-a4tech-x7-con-linux-facciamo-funzionare-tutti-i-tasti/"), and changed within help of google translator to my language, turkish, which is [here]("http://www.soulsmasher.net/ubuntuda-a4-tech-x7-gamer-mouse-buton-ayarlari/")

i'm planning to translate to english, but laziness keeps me on :D
hope this helps a bit

Its never too late:P
heres the link in English:
[http://209.85.135.104/translate_c?hl=en&langpair=it%7Cen&u=http://natonelbronx.wordpress.com/2007/07/10/mouse-a4tech-x7-con-linux-facciamo-funzionare-tutti-i-tasti/](http://209.85.135.104/translate_c?hl=en&langpair=it%7Cen&u=http://natonelbronx.wordpress.com/2007/07/10/mouse-a4tech-x7-con-linux-facciamo-funzionare-tutti-i-tasti/)

Well thanks for this, I will try it when i get my hands on the mouse ;)

---

### Post by SoulSmasher on 2008-02-19
this guide works also on its brother, x750-f  which i am using now (and i think also on lower models) :)

shortly: worth trying on all a4tech x7 series mouses

---

