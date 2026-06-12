---
title: "Apple 20&quot; Cinema Display Resolution unsupported"
date: 2004-10-22
forum: Hardware &amp; Laptops
---

### Post by thevine on 2004-10-22
Any help with gettin a working XF86Config-4 for this beasty would be greatly appreciated, it's running off a DP G4(PPc) with a Radeon 9000 Pro, the release install of Ubuntu and some tweaking have given me a stretched 1400x1050 but no modeline addition will give me the correct 1680x1050. This is a fabulous distro that I would love to use and work in but I need to straighten out this deal breaker. Thanks in advance if you can help.

---

### Post by iwasbiggs on 2004-10-22
Have you tried editing /etc/X11/XF86Config by hand and putting your desired resolution in the screen section (making sure it's the first entry)?

Or maybe this is what you meant as modeline?

---

### Post by thevine on 2004-10-25
Thanks Iwasbiggs, I have put the correct resolution in the modeline which seems to work for other widescreen resolutions (I have a working 1152x768 on my powerbook) but the 1680x1050 just does not work, does anyone at Ubuntu know if the version of XF86 included at install supports this resolution?

---

### Post by jlintz on 2005-01-28
I had  1680x1050 working in warty but then when I upgraded to hoary with xorg I can not for the life of me get 1680x1050 to show up or work

---

### Post by davegod75 on 2005-01-30
can't get 1680x1050 to work in hoary either

---

### Post by BMWolf on 2005-01-31
jlintz 
how did you get 1680x1050 in warty? i have a dell2005fpw  and a 6800gt and i cannot get it to work for the life of me. i installed the drivers, edited the config file, tried hoary upgrade, edited the config file.....nothing.i need to clean and reinstall all of my stuff here soon so i'll be starting from scratch.  Any help would be greatly appreciated!

---

