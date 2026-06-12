---
title: "Canon MP270 driver on 20.04"
date: 2021-12-11
forum: Hardware
---

### Post by freesitebuilder on 2021-12-11
I have an old but very reliable Canon MP270 printer/scanner which is enough for my needs - I now use it very infrequently. It's worked perfectly well on 20.04 on two previous machines.

Two years ago got a brand new Linux pre-installed machine, my printer worked OK on that on 20.04, that machine is now virtually dead. I've replaced it with a refurbished Thinkpad, dual-booting until my 2year warranty expires, using almost all the ssd for Ubuntu.

I did a clean install, and then restored from my backup (Deja Dup). Only thing not working is my printer. CUPS is 2.3.1, and tells me I have only a generic grey-scale text-only driver. Canon drivers page tells me this machine isn't supported on 64-bit Linux. I have the Gutenprint app installed, although this only shows in the Ubuntu Software, not when I search in applications.

Obviously missing something here, so grateful for any pointers! My previous machine will start so I can access it to copy anything I missed out on Deja Dup if necessary.
TIA

---

### Post by nginmu on 2021-12-13
I just tried typing 'printers' in the search that comes up off the desktop main menu button (I'm on 64 bit lubuntu). That brings up a frontend for CUPS. I clicked Add, and was able to install a driver for the MP270 from the 'Generic-CUPS-BRF-Printer' option. When it asked me to enter the device URI, I just left it blank and clicked 'forward', it let me choose from a long list (the Foomatc Database I think). I have a test page sat in the queue, but can't go any further without an actual MP270.

[This](https://www.howtogeek.com/215235/how-to-install-printer-drivers-on-linux/) seems like a helpful page.

I seem to have CUPS 2.3.3; the MP270 driver it's showing me mentions all manner of colour options, it doesn't look like a grey-scale text-only driver at all..

---

### Post by freesitebuilder on 2021-12-17
Only have CUPS 2.3.1 which software manager tells me is latest (unless I install manually of course). My printer isn't listed. I loaded Gutenprint through firefox, and it could see the printer, and I printed a test page OK. LibreOffice told me that a generic text-only driver wouldn't print my page. I switched off, and went away to do other things. Today switched back on, got a notification that a printer MP270 had been added, and now I can print just as before. 

So thanks for all the help - although worryingly I don't really know what I did to make it work!

---

### Post by nginmu on 2021-12-18
Maybe your Internet connection was playing the silly goat at the time, and when you came back, the first thing it did was see a good stable connection and managed to download some pending thing it needed. Working now anyway.. good stuff. Deja Dup sounds useful, I'll check it out.

---

