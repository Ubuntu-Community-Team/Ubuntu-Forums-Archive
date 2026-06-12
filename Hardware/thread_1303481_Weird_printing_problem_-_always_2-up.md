---
title: "Weird printing problem - always 2-up"
date: 2009-10-28
forum: Hardware
---

### Post by grkuntzmd on 2009-10-28
I am running 9.04 x64 on a Dell Inspiron 1720. My local (USB) printer is a Brother HL-5140 using the driver "Brother HL-5140 Foomatic/hl1250".

My localhost printer always prints PDF files 2-up. If I tell acroread to print 2-up, I get 4 pages per letter-sized sheet.

If I print to any of the network printers, the output is 1-up (assuming acroread is configured for 1-up printing).

This seems to have started a couple of days ago after usual a apt-get update.

Where is the output format for cups/PDF controlled?

I checked the /etc/cups directory, but could not find anything. Am I in the right place? I also looked at the a2ps config files and went through the [http://localhost:631](http://localhost:631) cups configuration.

Thanks.

---

### Post by Anthon on 2009-10-28
Have you looked at the default printer properties ( System -> Administration -> Printing then right click the local printer and select Properties -> Job Options)? There is setting there that indicates the default # of pages per side.

---

### Post by grkuntzmd on 2009-10-28
That's another weird thing.

System->Administration->Printing hangs with high CPU usage on Python.

The only way for me to administer the printers is through the HTTP interface to cups.

This too started a few days ago.

Glad I'm doing a clean install of Karmic soon :-).

---

### Post by grkuntzmd on 2009-10-28
I edited the file /etc/cups/printers.conf, removing the lines "Option number-up 2" and then restarted cups.

---

