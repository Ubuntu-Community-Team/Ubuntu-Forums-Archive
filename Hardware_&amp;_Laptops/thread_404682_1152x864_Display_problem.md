---
title: "1152x864 Display problem"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by Slug01 on 2007-04-08
I just installed Xubuntu 6.10. I edited the xorg.conf file to allow me to use the 1152x864 display resolution I had previously been using in Windows on my ATI Xpert 98 AGP video card. It works fine except the top left corner of the screen is corrupted with a pattern that looks like a barcode. I'd say it is about 80x80 pixels or so. 

The line I added to my "section monitor" is
 Modeline "1152x864" 97.48  1152 1200 1320 1544   864  864  866  901

Any ideas?

---

### Post by heimo on 2007-04-08
> **Slug01 said:**
> 
Any ideas?


Yeah, I'd try to tweak the modeline a bit by bit, using xvidtune. Run it from a terminal, so that you can see its output when hitting "show" to show modeline.

---

### Post by jmagsho on 2007-09-02
Heimo,

Thanks for the suggestion - I was having the same problem and xvidtune did the trick.

---

