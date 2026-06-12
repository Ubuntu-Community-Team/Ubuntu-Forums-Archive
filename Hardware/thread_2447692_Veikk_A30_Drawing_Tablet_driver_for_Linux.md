---
title: "Veikk A30 Drawing Tablet driver for Linux"
date: 2020-07-23
forum: Hardware
---

### Post by KayaE on 2020-07-23
Hello,

i bought Veikk A30 drawing tablet today. it has no linux driver support.  
and only page i could find help is
[https://github.com/Axonny/veikk_a30_driver/blob/master/README.md](https://github.com/Axonny/veikk_a30_driver/blob/master/README.md)

but (sudo make install clean) command didnt worked for me.
terminal says: " make: *** No rule to make target 'install'.  Stop. "

i also found this video on youtube which shows how to use same source.
[https://www.youtube.com/watch?v=8ahR8RGj7xA](https://www.youtube.com/watch?v=8ahR8RGj7xA)
but (make) command does not work for me as it worked on video.

can you guide me to install this driver?

Hardware is:  [https://www.veikk.com/product/40.html](https://www.veikk.com/product/40.html)

---

### Post by KayaE on 2020-07-23
i contacted Denshi (who created instruction video on youtube) and thanks to his help i could install veikk driver as his video shows.

solution for Ubuntu 20 lts is,
type in terminal this command
(sudo apt-get install build-essential)
 and then 
(sudo make install clean)

---

