---
title: "Trying to clear micro sd card [nothing works]"
date: 2017-01-06
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2017-01-06
So the Raspberry pi my mom has has been giving me issues, i figure the card got corrupt
i was unable to repair it with gparted, so ughh i have to reinstall it, ok never had a issue like this before
even if i delete files of the card as soon as it is remounted they are back
I have tried using gparted, dd, and cp to clear this card (with 2 different card readers and computers): [https://youtu.be/Tevk3RtMGkw](https://youtu.be/Tevk3RtMGkw)
Aside from RMAing the sd card does anyone know any other method to delete what is on it
i have also tried writing a new img file to it, no change to the cards content

---

### Post by Bucky Ball on 2017-01-06
Just a suggestion. In Gparted, unmount the partitions on the SD card then Device> Create partition table. That will wipe the SD ... hopefully. 

You may have tried the above, but if not, let us know how you go.

---

### Post by pqwoerituytrueiwoq on 2017-01-06
i have tried that several times
i have even deleted files off the partition unmounted and remounted and they are back,
i have also added files and unmounted and remounted and they are gone

* my system is set NOT to mount external media when it detects it (very annoying when you insert a HDD with ~5 partitions on it in a hot swap bay)

---

### Post by sudodus on 2017-01-07
I suspect that the card is failing. Card and pendrives can behave like that before they fail completely. Sometimes it is possible to overwrite the whole device with zeros to make it work well again, but sometimes it is too late, and it does not help with the tools that are available to us regular users.

It is possible that some tool that writes into the internal structure of the card might work, but I don't know how to find such a tool. I think you need a new card. Save your files (personal files and tweaks), while you can still read from the card.

---

### Post by pqwoerituytrueiwoq on 2017-01-07
Backed up before trying to delete :)
i did look closer at the card and noticed it was my class 6 card, i only have one of those several class 10 in that capacity, but that this one has about 2 years of 24/7 use on it in raspberry pi that run as servers, so im not that surprised it is having issues after such a reliable past

---

### Post by sudodus on 2017-01-07
I think 2 years of 24/7 is good for a memory card :-)

---

