---
title: "Ugly printer fonts!!"
date: 2006-09-14
forum: Hardware &amp; Laptops
---

### Post by erikcw on 2006-09-14
Hi all,

I've got my HP Laserjet 3330 MFP working with Dapper.  Unfortunately, the fonts are UGLY!  I printed directions this morning from google maps and the fonts were jagged and the maps weren't readable.

Any idea what could be causing this?

Thanks!

---

### Post by IcemanV9 on 2006-09-14
Haha. I just printed out the Google Map direction on HP Deskjet 693C. It came out beautifully. And, I just saw this post.

Anyway, did you print test page? If so, did it came out perfectly? If not, then you need to go into Properties and select the correct paper size, advanced, and other options.

FWIW, you may want to search the forum for "HP Laserjet 3330 MFP" threads.

---

### Post by erikcw on 2006-09-14
The Ubuntu test page looks fine.  But anything printed via CUPS (I share the printer with my wife's mac) or printed from the web looks terrible!  Are there some fonts I need to install?

Thanks!

PS  I searched the forum for my printer, but found nothing relevant...

---

### Post by IcemanV9 on 2006-09-15
If print test page looks good, then you may have to fiddle with Mac to make sure it is shared with others. For testing purpose, can you attach the printer to your box? Then, print test page AND the Google Map direction OR any page from the website. If it comes out good, then it is Mac. If not, then you may have to find the right driver for the printer.

Other than printer problem, you may want to install msttcorefonts (Win32 fonts such as Verdana, Comic Sans MS, etc).

---

### Post by erikcw on 2006-09-15
Thanks Iceman - I already have the MS fonts installed, and the printer is connected to the Dapper box and sharred via CUPS to the mac...

I guess I should try different drivers...

---

### Post by IcemanV9 on 2006-09-15
FWIW, this [**[COLOR="RoyalBlue"]solution[/COLOR]**]("http://cups.org/articles.php?L230+I0+THow-To+P1+Qnetwork") worked for me when I tried to setup HP Deskjet 693C as network printer.

---

