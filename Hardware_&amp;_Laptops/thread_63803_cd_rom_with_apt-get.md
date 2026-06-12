---
title: "cd rom with apt-get"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by mwolfe on 2005-09-09
For some reason my apt-get is asking for me to insert my ubuntu disk into /cdrom/

i've had this before and it was no problem, it only worked on one of the drives, but that was fine. Now it doesnt work in either, and both of the drives are working. 

the cdrom i have it in now is mounted at /media/cdrom1
i think the other one is /media/cdrom0 but i'm not sure, either 0 or 2.

How can i fix this, its very annoying!

---

### Post by jasmuz on 2005-09-09
Just open up a terminal, type sudo gedit /etc/apt/sources.list and place a # where it says the information about the cdrom, save and close, then sudo apt-get update, and that's it!

---

### Post by mwolfe on 2005-09-09
thanks.. You know what i have no idea how i fixed it.. Eventually it just worked. THen this morning i realized what the problem was all along, i was putting in the ubuntu live cd not the regular one.. oops

---

