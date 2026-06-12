---
title: "Making a Lexmark z13 work...I can't do it."
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by dreamer_nights on 2005-06-07
No matter what I do, I cannot even get the lexmark driver itself installed so I can use foomatic, and I don;t even know how to use foomatic! Please help me, I've tried using some other drivers in ubuntu, but they don;t work at all.

---

### Post by David Haas on 2005-06-07
Hi dreamer_nights--You don't have to know how to use foomatic to set up most printers, but you must have foomatic installed in Ubuntu (it probably is already). Look in System>Administration>Synaptic Package Manager at the foomatic packages to see whether they are installed. The default installation, which you probably have, is the packages from foomatic-db through foomatic-filters-ppds. You must also have the cupsys packages installed (probably are, by default). When you open the printer manager GUI (System>Administration>Printing) and select "New Printer" can you find your printer listed in the Lexmark section? If the Lexmark z13 isn't listed the Lexmark z12should be, because Ubuntu Hoary has the PPD file for this printer. Selecting the PPD file should enable your printer to work well. So, select the printer and then click through the file system in the printer GUI as follows:  /usr/share/cups/model/foomatic-ppds. In foomatic-ppds, you'll locate the ppd file for the z12. It's "Lexmark-Z12-lxm3200-tweaked.ppd.gz" (without the quotes). Since this is the same file as for the z22, z31, and z32, I assume it will work for the z13. One selects this by highlighting it and clicking on the "open" button. When the ppd file is selected, Ubuntu places and unzipped copy of the file in /etc/cups/ppd. Well, i hope this helps.
David

---

### Post by dreamer_nights on 2005-06-07
Well, I did what you said and it came up with an error: Missing asterisk?

---

### Post by David Haas on 2005-06-08
If I recall correctly, I got a similar error message when I installed my HP Deskjet last month, and others have also reported it. I think it's a bug, because when I and others ignored the message and selected install driver after highlighting the one needed, all worked well. So, try this if you haven't already. 
David

---

