---
title: "Kodak 5500 AIO Printer"
date: 2011-10-14
forum: Hardware
---

### Post by hotshot247 on 2011-10-14
hey, i just upgraded to ubuntu 11.10 and i noticed that it has more of a selection of printers to install and it actually has my printer which is a kodak 5500 aio and i get it set up and ready to print but when i try to print, it says "printing" on the printer and it even takes the paper in so i know their is communication to the printer but it just doesn't print. does anybody know how to fix this issue? thanks.

---

### Post by paulnewall on 2011-10-29
Did you try all the combinations of colour/blackand white, 300dpi/600dpi. It could be that one combination will work.
To progress after that you will need to change the loglevel in cups to debug to see the debug messages.
That means editing the file cupsd.conf (I can't remember where that is - maybe in /etc/cups ? to change loglevel=warn to loglevel=debug.
 
Then after printing, look at the /var/log/cups/errorlog file for clues as to what went wrong.

---

### Post by mörgæs on 2011-10-29
Moved to Hardware and Laptops.

---

