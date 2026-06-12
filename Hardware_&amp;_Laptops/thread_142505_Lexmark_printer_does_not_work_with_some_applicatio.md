---
title: "Lexmark printer does not work with some applications."
date: 2006-03-10
forum: Hardware &amp; Laptops
---

### Post by EMG on 2006-03-10
My distribution is Ubuntu 5.10 with GNOME.
I have a Lexmark Z600, installed by myself thanks to a HOWTO in your forums.
It works perfectly with Firefox, gedit, OpenOffice.org (and when printing a test page, of course).
It does not work at all with GQview and the GIMP when trying to print photos, images, etc.

The following happens with GQview:

* I try to print a JPEG.
* I choose 300 dpi, default printer.
* I choose A4 paper size.
* I set "image" as printing source, one image per page.

Results: Printing job does not even lists in printer window.

* Changing printer to a personalized one.
* The command that it will use is "lpr -P Z600-v1.0-1".

Results: Same as before.

With the GIMP:

* I choose A4 paper size.
* I choose listed printer name: "*Z600-v1.0-1".
* GIMP does not detect my model, so I try PostScript 1 and 2.
* The command that it will use is "lp -s -dZ600-v1.0-1 -oraw".

Results: Printing job DOES appear in list, with the correct state "job-printing", but never starts the actual printing. It shows "(stdin)" as file name. A bit later, the job vanishes from the queue.

* I manually pick the PPD file: "/usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd".

Results: The same.

* I try all Lexmark models that GIMP knows about.

Results: The same, but now the job does not dissapear from the list.

I will thank some advice or clue that I could try to fix this. It would be very disappointing to have to trash Ubuntu for my printer's fault :( .

---

