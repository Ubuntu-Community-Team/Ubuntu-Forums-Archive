---
title: "Acer Aspire E5-571-5552 Hardware Problems or Software?"
date: 2015-07-22
forum: Hardware
---

### Post by anthony72 on 2015-07-22
[h=1][SIZE=3]Acer Aspire E5-571-5552 
Intel Core i5 4210U 
1.6GHz [/SIZE]
[SIZE=3]Intel HD Graphics 4400
 4GB Memory
500GB HDD 5400 rpm[/SIZE][/h]If I do a file transfer to a external hard drive the laptop slows down so much It becomes unusable until the transfer is done. There is just general slowness with all task. Video playback has screen tearing.  I did some searching and disabled animations that I could with compiz config manger and the whole system is more responsive now. Not sure If it just old hardware and pushing it to hard or driver/software?

---

### Post by weatherman2 on 2015-07-22
What version of Ubuntu are you running?

i5-4210U is *NOT* old hardware - this is a 4th generation Intel core CPU, fairly recent.  (They are now on 5th generation.)  Actually, the fact that it is too new could be your real issue - maybe there aren't yet good drivers for it.  But that would depend on the version of Ubuntu you are running...

---

### Post by anthony72 on 2015-07-22
Nothing comes up in additional drivers in software and updates. Its 14.04.2 LTS with all the updates it would give me. Sorry should have specified before. I also tried 15.04 with same results.

---

### Post by weatherman2 on 2015-07-22
For fun, try installing Gnome Flashback in Ubuntu Software Center.  Logout, then before logging back in change the session type to "Gnome Fallback (Metacity)" - this looks like the old-style "Gnome" interface and works better for old graphics cards...or, perhaps, new graphics cards without a good driver.  If this works fast, then you may be able to pursue a fix to use the original "Unity" desktop - maybe install the Intel graphics driver or something.

---

### Post by anthony72 on 2015-07-22
Tried Gnome Flashback works very fast but have touch-pad problems which made it unusable. I tried Intel graphics graphics installer for linux but all i get is  " Distribution not supported".

---

