---
title: "Epson Stylus Photo 925"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by Ferio on 2005-06-19
My printer seems suddenly not to be detected by my Ubuntu, when it was in the past. It's connected via an USB port as a locale printer, and when I send works to the queue, they just appear there, but the printer doesn't work. Any idea that could help me?

---

### Post by David Haas on 2005-06-19
Hi Ferio--I don't know what happened, but can suggest some things to try. Did you do any upgrades before you "lost" the printer? When you open the Gnome printer manager, is you printer listed? Is the PPD file for your printer listed in /etc/cups/ppd? It should be, because Linux places a copy of the PPD file here when the PPD is installed (selected). What PPD file did you select? The one I see in Hoary is escp2-925.ppd.gz in the directory 4.2 at /usr/share/cups/model/gimp-print/4.2. I'd suggest deleting your printer from the printer manager if it's still listed there and installing it again by starting with "New Printer". I hope that the Epson hasn't died, though this remains a possibility. If you can't get it working soon, you could connect it to a Windows machine to see whether it's operative.  
David

---

### Post by Ferio on 2005-06-20
Hi, David. I applied some updates, but they were for Gaim, so I think (or at least, I hope) they have nothing to do, and it does appear in my Gnome Printer Manager; in fact, the works are in the queue and it says it's printing, but the printer doesn't works. :neutral: I don't know about the file you tell me, but I'll check it as soon as I got home tonight; it's not the printer, 'cos it works under Win XP.

---

### Post by Ferio on 2005-06-20
Hi, David, I've just found out how can I fix this problem, though it's not a real solution: I must switch the printer on before my Ubuntu loads, and this way it works perfectly; if I do it other way, it doesn't work. At least is a partial solution... Thank you for your time!

---

### Post by David Haas on 2005-06-20
Ferio--Well done! I had to do this with my former Epson Stylus C82, when I was running Warty, which didn't have hotplug, but don't need to have my current HP Deskjet printer on before booting Hoary, I assumed this had to do with the hotplug support in Hoary.
David

---

