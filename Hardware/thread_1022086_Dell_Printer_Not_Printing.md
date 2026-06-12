---
title: "Dell Printer Not Printing"
date: 2008-12-26
forum: Hardware
---

### Post by broken tibula on 2008-12-26
Hello!

I have an old Dell A940 printer, and I'm trying to get it to work with Ubuntu (running 8.10 on a desktop).  [This site](http://ubuntuforums.org/archive/index.php/t-66634.html) told me to download a Lexmark driver that would do the same thing, so I did, and then I used Alien to convert it to .deb and installed the file.  Under *System > Administration > Printing*, it registers the printer, but when I try to print something, it doesn't send.  The printer doesn't receive it and *Applications > Accessories > Print Jobs* doesn't show anything either.  When I try to print a test page, via *Printing > A940 > Print Test Page*, it gives me this error message: 

> There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

I Googled the error message, which led me [here](http://forums.fedoraforum.org/showthread.php?t=180014).  So I opened /etc/cups/mime.convs, uncommented the line that filtered the printing arbitrary files, and restarted CUPS.  This solution did not work.  I looked for other solutions, but wasn't able to find anything.

Can anyone help me?

---

### Post by broken tibula on 2009-01-02
*bump* 

Anyone?

---

### Post by DarkReaper79 on 2009-01-02
Im going to assume you did everything listed in the first post of this how-to

[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

Did you set the drivers as the Z600 ones?

This worked for my A910.

---

### Post by broken tibula on 2009-01-02
Yeah, I tried that tutorial as well, and it resulted in the same thing.  

This printer is kind of old--would I be better off just buying a new one?

---

### Post by DarkReaper79 on 2009-01-03
At the price of printers now, and how its a bit old. I would say look into a new one.

---

### Post by broken tibula on 2009-01-04
Yeah--my friend has an HP that she's looking to give away.  There's working drivers for it, but it's a laserjet, so no color...

Oh well.  Better to have only black and white printing than to have no printing at all!  Thank anyway, guys.

---

