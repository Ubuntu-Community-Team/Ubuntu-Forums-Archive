---
title: "Printer Cutting Off Bottom"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by afoglia on 2007-05-16
I'm having trouble getting an HP Photosmart 1215 to print a full page correctly.  The CUPS printer test page ends abruptly about a half inch from the bottom of the page.  (As does a PDF I'm currently trying to print.)  I'm using the hpijs driver, with the PhotoSmart P1215 selected.  The page size according to the CUPS "Set Printer Options" web interface is Letter, and the other 3 options don't seem relevent (printout mode: normal, media source: printer default, double-sided printing: off).

Anyone having any ideas what else to check?

---

### Post by munkydust on 2007-05-16
Personally I'd recommend not sitting on it :-) sorry I couldn't resist.

Can you not change the paper size to A4 if it says letter? When you go to print, select Properties > Paper Size > A4. Hope that helps.

---

### Post by mitch.c on 2007-05-16
If the 1215 is like the 1000, you have a fairly good size non-printable margin at the bottom. For the 1000 the measurements are (72/inch):

top:5
left:18
right:25
bottom:32

You might try something like:
```
# run as root (sudo) to set for all users
$ lpoptions -p your_printer_name -o page-top=5 -o page-left=18 -o page-right=25 -o page-left=18
```

lpoptions without the -o option will show you current option settings.

You can do all this from the web interface, but I'm a masochist. :)

-- 
Mitch

---

