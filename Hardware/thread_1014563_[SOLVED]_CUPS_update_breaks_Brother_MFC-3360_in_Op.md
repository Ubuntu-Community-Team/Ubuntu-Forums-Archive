---
title: "[SOLVED] CUPS update breaks Brother MFC-3360 in Openoffice (and some apps)"
date: 2008-12-17
forum: Hardware
---

### Post by raycosm on 2008-12-17
So there was a CUPS update in Update Manager some time today, and I installed it, and now I can't print to my Brother MFC-3360 in Openoffice and Evince (there are probably more apps were they don't work, but I haven't tried yet). It's been working great before I the update, and I haven't been using the printer long enough to have it been broken by a previous update. I installed the printer using the information at [https://wiki.ubuntu.com/BrotherDriverPackaging]("https://wiki.ubuntu.com/BrotherDriverPackaging") on Intrepid.

When I try to print, it the little tray icon pops up, then goes away within a few seconds. Kind of like when a successful print job does happen, except it goes much faster and a successful print job does not happen.

Another note, I can still print using Firefox (and probably other apps too).

EDIT: I can't seem to print just plain html files off of my hard drive, but I can print web pages in Firefox. Printing an html file gives the same result as printing from Openoffice.

---

### Post by NaGahl on 2008-12-18
I had this problem to w/ a HP OfficeJet 6200 after updating CUPS today. Attempting to print a test page from the printer configuration app gave me a permissions error. 

I fixed it by deleting the printer and reinstalling it. Works fine now.

---

### Post by raycosm on 2008-12-22
Well that worked for me, but another CUPS update came a few days later and I got the same problem. That time, I didn't do anything, and the next time I restarted my computer, the problem was gone. Weird. I guess you just ignore it.

---

