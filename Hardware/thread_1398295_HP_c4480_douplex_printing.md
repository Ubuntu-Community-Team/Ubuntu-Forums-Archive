---
title: "HP c4480 douplex printing"
date: 2010-02-04
forum: Hardware
---

### Post by nikoker on 2010-02-04
Hello!
I just wonder whether i can print on double side with HP photosmart c4480.
I used to work with the driver of this printer in windows 7 and there was a selection for double side printing, booklet, many pages per page etc.
It would be useful if i could use this feature in Kubuntu 9.10 with with HPLIP driver from HP.

I can see a selection in HPLIP ToolBox -> Print Settings -> General -> Double sided printing and it has long edge and short edge but it doesn't work.

PS: Sorry for my English . I try to improve it.

---

### Post by Leppie on 2010-02-04
have you tried looking in cups admin?
open a browser and go to the following address: [http://localhost:631]("http://localhost:631/")

---

### Post by nikoker on 2010-02-04
I tried cups , i added the printer. In the "Set default options" section i choose "long edge" in the double sided printer but it doesn't work. 

In Manufacturer's features i see that the printer can't support double sided printing: [B]*Duplex printing* None (not supported).

[/B]But in Windows i used to do this manually. A message appeared in the screen when half of pages had been printed with instructions how i turn the pages.

---

### Post by nikoker on 2010-02-04
I want only to do this manually. I wanna make my printer print half of pages and then printer will pause and i manually return the pages and put it to the printer for double sided printing.

---

### Post by Leppie on 2010-02-04
then issue the print command like that...

---

