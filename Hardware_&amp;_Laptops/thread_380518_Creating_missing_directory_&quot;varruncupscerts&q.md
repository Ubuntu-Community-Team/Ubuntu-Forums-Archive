---
title: "Creating missing directory &quot;/var/run/cups/certs&quot;"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by schumifer on 2007-03-09
OK i will shortly describe to you what happened and how and then i will log out to reinstall my kubuntu .
I was printing a couple hundred pages on my Epson C46 and i had to temporarily stop printing . After that my 32bit edgy stopped sending pages to the printer. Using turboprint i could see the print level, and lsusb returned my printer as always ,so i know that the printer was there. Turned on the second epson printer and -unbelievably- the same issue was present. Usb communication was intact, no page was being sent to the printer(s).
Checked the cups.log.  Only one entry.
Creating missing directory "/var/run/cups/certs".

So what to do?
Google of course.
A couple of links gave only the same problem as me but the only solution was reinstall. So i decided to give it a go. 
Reinstall cups....................nop
reinstall *cups*..................nop
purge *cups* && install *cups*........nop
purge *cups* ,manually delete *cups* , install *cups*............NOOOOOOOOOOPPPPP
Don't do the last one. I had to reinstall kdelibs.
Well after the last stunt, the result was i had a brand new printer section in my system settings with no installed printers. Hmmmm goooddd you would say. Well it would be if the darn thing allowed me to add my 2 local printers. Instead the local printer line was grayed out!!!!!
Logged on as root, same thing.
Well that was it.
 Going to reinstall.
You know what bugged me? until now i always booted Linux to make sure that something was a windows problem, not a hardware one. Now i did the opposite... LOL

---

