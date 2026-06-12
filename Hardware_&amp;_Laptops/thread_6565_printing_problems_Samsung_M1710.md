---
title: "printing problems Samsung M1710"
date: 2004-11-29
forum: Hardware &amp; Laptops
---

### Post by plebeien on 2004-11-29
I have a problem in printing something, openoffice or gimp just can't print anything... suppose that may be CUPS. my printer is the laser samsung M1710, the only application I found to be ok is gthumb for the images... with gimp, nothing starts, with OOo it prints a blackline and basta...

gthumb uses CUPS ?

---

### Post by bob k on 2004-11-30
[QUOTE=plebeien]I have a problem in printing something, openoffice or gimp just can't print anything... suppose that may be CUPS. my printer is the laser samsung M1710, the only application I found to be ok is gthumb for the images... with gimp, nothing starts, with OOo it prints a blackline and basta...

gthumb uses CUPS ?[/QUOTE]


Try Installing these 2 files form the Ubuntu repository.

cupsys-driver-gimpprint
cupsys-driver-gimpprint-data

Bob

---

### Post by plebeien on 2004-12-01
thanks Bob but they're already installed.

it may be something else.

---

### Post by plebeien on 2004-12-29
everything running GTK 2+ seems to work ok, gthumb, gpdf and so on but openoffice nothing, x applications nothing either... strange that firefox neither, the printer seems to work but the page is blank or worst, full of blanck lines and stuff like this.

I got the ML1710.ppd in /etc/cups/ppd but can't tell exactly what's going on.

---

### Post by bob k on 2004-12-30
I did install the Linux drivers that are included on the driver CD, and I can print from open office. The print speed sucks, it loads a buffer, prints a buffer, then wait for the next buffer.

When they load they are under the applications menu under other and want to use LPR. Since every thing is working, I have not tested this path. This worked in FC1.

If it works don't break it.

---

### Post by autek on 2004-12-31
FWIW-   I have a Lexmark printer and on someone else's advice I installed the following

cupsys-bsd
cupsys-client
foomatic-bin

Not sure which of the 3 fixed my printer, but it now works from any app that  I need. Prior to this I could not print from OO  HTH

Ed

---

### Post by plebeien on 2004-12-31
I already have the three packages installed on my system but didn't change anything. thanks :)

---

