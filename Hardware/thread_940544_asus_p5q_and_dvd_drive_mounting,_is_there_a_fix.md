---
title: "asus p5q and dvd drive mounting, is there a fix?"
date: 2008-10-07
forum: Hardware
---

### Post by Cew27 on 2008-10-07
hey guys i had problems installing ubuntu with this mobo and found fixes using the all_generic_ide parameter in grub, this worked for installing however i didnt put it into my menu.lst . Today i tried to burn a debian dvd and realised my disk wasnt mounting, i edit the grub and all is fine although when i boot i get a 5 second halt saying i have a pci bug ect.
to summarise i want to know if there is a fix coming in intrepid? or if there is a fix out there maybe a bios update sorts it? 
thanks alot 
Cew27

---

### Post by Marshal0505 on 2008-10-07
I have the same board and never had a problem with dvd mounting. Are you sure about the cause being in Hardy or it's kernel? I used every kernel between 2.6.24.16 and 2.6.27.rc9 with the P5Q board.

---

### Post by Cew27 on 2008-10-07
hmm what sata ports are you dvd drives in? i think mine are in the multicolouted ones and are they sata

---

### Post by Marshal0505 on 2008-10-07
Hmm, yea my bad, my sata devices are all hard drives.Sorry bout the confusion.But still ...by changing the 'Configure sata as...' in the bios I can sorta reproduce the problem.Have you tried changing this setting from it's default to either 'raid' or 'ahci'?

---

### Post by Cew27 on 2008-10-07
yep both result in a stupidly long bios hand and doesnt help the situation

---

### Post by Marshal0505 on 2008-10-07
Too bad I can't be of assistance, but like I said I have no experience with sata dvd drives.One last question though; is the result the same using the red sata ports compared to the orange/white ones?

---

