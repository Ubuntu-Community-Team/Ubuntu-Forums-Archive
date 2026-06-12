---
title: "Printer won't print after stopped printing"
date: 2011-05-07
forum: Hardware
---

### Post by NewReformist on 2011-05-07
Okay I am not too sure if this goes to the hardware topic, but since a printer is a hardware I guess so.

So I have Ubtuntu 11.04 (run in classic mode) and a HP LaserJet P1005 printer. I installed the drivers and everything worked, but just as with previous Ubuntu versions when I for some reason stop a print then when re-starting it it just won't print. 

I even re-started my system but the printer is dead. In previous Ubuntu versions I could just re install the foo2zjs driver through terminal and the printer would start, but in the new ubuntu this won't work either.

I find this annoying and buggy, I mean sometimes you just have to stop a print for whatever reason (or it stops by itself as in this case there weren't enough papers).. but then you can't re-start the print or anything.

---

### Post by amishtrucker on 2011-05-31
I have this same annoying problem with my HP P1005. I even updated to the latest HPLIP file which is more current than the one in the repository.

I have discovered that if I log into Windows and print something there, then I can come back to 11.04 and it works.

I understand that a bug report has been filed.

---

### Post by enginkzlgn on 2011-06-02
i dont like say me too but if i turned on (p1005) printer on windows and come back to ubuntu 11.04 it works. I use 64bit Ubuntu (11.04 Natty...) and  i try purge and remove hp libs and cups libs later reinstall it but nothing is changed ,i have same problem now.

---

### Post by roderickf on 2011-07-02
EXACTLY the same problem here.

If I turn off the printer, then I must log in Windows and print something. Otherwise, printing on ubuntu 11.04 won't work no matter how.

I wonder if someone survive in this situation where he/she doesn't dual-boot.

---

### Post by roderickf on 2011-07-02
I found a solution to the problem.

First go to 
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)
and download the .run file and follow the steps.

After restart, you would find a HP logo on the top panel, double click it and under Action tab, do "Download Firmware".
Your dead P1005 will then come alive.

:)

---

