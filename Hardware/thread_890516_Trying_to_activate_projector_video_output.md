---
title: "Trying to activate projector video output"
date: 2008-08-15
forum: Hardware
---

### Post by bill.p on 2008-08-15
I've been asked to give a presentation for which I wish to use a
video projector. I'm running Ubuntu 8.04LTS on my Toshiba Equium
Laptop. Plugging in the projector just gives - No Signal.
I tried rebooting the machine and I get the display during the
early phases of booting up but when it starts the display manager
I just get a blank screen and 'No Signal'. I've booted into BIOS
and set the video mode to LCD+Analog but I guess the display manager
is resetting this to LCD only. How can I get it work? If all else fails
I'll have to fall back on (bated breath)Micro$oft Powerpoint(gasp).

Please help - urgent - I have to give my talk next Tuesday!

Bill

---

### Post by lisati on 2008-08-15
Does using fn+F5 to switch output help at all?

---

### Post by bill.p on 2008-08-15
Using Fn+F5 works during the boot phase, but not once X11 starts up.
No effect at all once I'm logged in.

Bill

---

### Post by silvanus2005 on 2008-08-15
You should activate Clone display in Display properties, and you should have no problem. I tried something else, also - I plugged my projector (Epson) to my laptop when Ubuntu was running; it was detected automatically; it changes my screenresolution from 1280*800 to 1024*768, but it``s working very good.

---

### Post by bill.p on 2008-08-15
Thanks for the suggestion.

Managed to find what I think is the panel you mean:
System->Preferences->Screen Resolution.
Clicked on Clone Screens then on 'Apply'
Got a prompt to choose between 'keep settings' or 'use previous settings'
and chose keep settings. Still just a blank on the projector.

:(

Bill

---

### Post by silvanus2005 on 2008-08-15
Follow that link, maybe it will help you>
[http://ubuntuforums.org/showthread.php?t=411674](http://ubuntuforums.org/showthread.php?t=411674)

---

### Post by bill.p on 2008-08-15
Many thanks for the link. Unfortunately, my graphics is an ATI Radeon
and that seems to be excluded from the solutions suggested there.

Looks like I'll have to fall back on a borrowed laptop with M$ PP  :(

Bill

---

### Post by silvanus2005 on 2008-08-15
Serch wih Google, maybe you will find elsewhere information you need. I also have a Toshiba laptop, but my graphic card is Intel, and it is working perfectly.

---

### Post by silvanus2005 on 2008-08-15
Maybe this will help:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

