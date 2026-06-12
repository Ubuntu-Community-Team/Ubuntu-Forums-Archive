---
title: "mmc no mount"
date: 2014-12-07
forum: Hardware
---

### Post by alek5a on 2014-12-07
[IMG]https://m.ak.fbcdn.net/photos-h.ak/hphotos-ak-xpa1/v/t1.0-0/10410646_858044337588404_365120339198399974_n.jpg?oh=6e37551e7b4f7aa29b84bdd7d8a1871b&oe=5515EDF2&__gda__=1427354831_ec57dffcba132fe29c976e1330047b09[/IMG]

---

### Post by alek5a on 2014-12-07
Is ubuntu genaraly fussy with reading sd cards of different brands or I am missing something?

---

### Post by alek5a on 2014-12-07
?

---

### Post by alek5a on 2014-12-07
Get the feel that certain brands of sd cards not ubuntu compatible or?

---

### Post by Bucky Ball on 2014-12-07
"Unknown filesystem type=exfat."

Last line of your error. What do you have the SD formatted as?

Ubuntu is not fussy with SD card brands as far as I know. It is fussy if they are formatted with a filesystem it doesn't recognise. It recognises FAT fine, but never heard of 'exfat'. Maybe something went wrong with the format or it is somehow formatted specifically for a Win or Mac by the manufacturer.

If you install Gparted (if it isn't already) and launch it, reformat the SD to something else, e.g. NTFS or EXT. FAT is kinda dated and has limitations anyhow. 

Good luck.

---

### Post by alek5a on 2014-12-09
What I've done. Put sd card in my old thc phone wich got confused with it and asked to format it. After that everything worked

---

