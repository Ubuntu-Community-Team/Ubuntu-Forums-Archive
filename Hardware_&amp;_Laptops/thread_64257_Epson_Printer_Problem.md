---
title: "Epson Printer Problem"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by Goober on 2005-09-10
Ok, I am hoping that this thread will allow my bloody printer to work, which is one of the 2 things (the other thing being playing Windows only Games) that I cannot yet do in Linux.

I have an Epson Stylus Colour 777.  I have tried System -> Administration -> Printing, and gone through that New Printer wizard many times, but it doesn't work.  I have tried all 3 of the available Printer Drivers for my style printer, and none work.  All seem to do the same thing - when I try and print something, the printer starts up, prints 4 lines at the top of the page, and then stays there, green LED flashing, doing nothing.  I am not sure what is going on, and if anybody can help, I would be very grateful.

Oh, and I have been to [www.linuxprinting.com](www.linuxprinting.com), but got more confused then ever.

Thanks in advance,

Goober.

---

### Post by kleeman on 2005-09-10
Sounds like your printer should work but that there is a networking issue. You can debug better if you edit
/etc/cups/cupsd.conf
and find 

LogLevel info

change this to
LogLevel debug

submit a print job then look in this file for info and post:

/var/log/cups/error_log

---

### Post by coolclassic on 2005-09-11
Turboprint has excellent drivers for epson printers:
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

---

### Post by Goober on 2005-09-11
Hrm, ok, thanks for the advice, I shall try both, however, I just realized that the printer is out of black ink, which might be why it wasn't working . . . 

After I get ink, I'll try these, thanks for the suggestions.

---

### Post by coolclassic on 2005-09-11
With turboprint you can check ink levels so the next time you'll no when you have ran out of ink  \\:D/

---

### Post by Goober on 2005-09-11
[QUOTE=coolclassic]With turboprint you can check ink levels so the next time you'll no when you have ran out of ink  \\:D/[/QUOTE]
 Well, when I am in Windows, and I install the Drivers using the CD that contains the drivers that came with the stupid printer (excuse my pessimism, I really hate the fact that I have to have the printer because my parent's computer is too crappy to have it, but excuse my ranting), then I can see the Ink Levels, but that involves going into Windows, which I dun like doing, for obvious reasons.

---

