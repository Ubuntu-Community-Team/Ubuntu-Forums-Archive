---
title: "Installing Brother HL-2270DW"
date: 2012-12-09
forum: Hardware
---

### Post by camelface on 2012-12-09
Hello mates, 

I have just upgraded my OS to 12.04. My driver installations are wiped out from what I can see. I can't say I remember how to install these. I just downloaded a fresh pair of cups and lpr drivers on the Brother website, but I do not know what to do with them. 

I am a true newb and do not know command prompt commands. So I would appreciate if someone could help me get my printer installation wizard to recognize those drivers in the selection list (I remember that I used to pick my drivers from the list in the Brother section because I had installed them on the computer and let the OS recognize their presence, but I do not remember how to do this). 

Thanks!

---

### Post by Peter Maunder on 2012-12-09
To add a new printer you need to go to SYSTEM SETTINGS  > PRINTER or from the terminal use system-config-printer to bring up the Printer Settings. 
Click the + sign at the bottom left hand side to add a new printer and follow the instructions. 

With my HL-5250DN I added the printer several times to create specific settings Duplex, Simplex, Booklet so that I could select settings quickly.

---

### Post by deadflowr on 2012-12-09
Oddly enough I was working on this exact same printer last week.

I found this thread

[http://ubuntuforums.org/showthread.php?t=1842880]("http://ubuntuforums.org/showthread.php?t=1842880")

And followed the procedure in this link

[http://chadchenault.blogspot.com/2011/09/brother-hl-2270dw-printer-driver.html]("http://chadchenault.blogspot.com/2011/09/brother-hl-2270dw-printer-driver.html")

Download the patched versions for easier installation.

It worked perfectly for me.

---

### Post by camelface on 2012-12-09
> **Peter Maunder said:**
> To add a new printer you need to go to SYSTEM SETTINGS  > PRINTER or from the terminal use system-config-printer to bring up the Printer Settings. 
Click the + sign at the bottom left hand side to add a new printer and follow the instructions. 

With my HL-5250DN I added the printer several times to create specific settings Duplex, Simplex, Booklet so that I could select settings quickly.


Thanks Peter but HL-2270DW is not a printer that is supported by the default ubuntu installation. There are many Brother printers on the list but not 2270!

Thanks flowr I will try that tonight.

---

### Post by pdc on 2012-12-10
hi camelface

in post #4 here

[http://ubuntuforums.org/showthread.php?t=1999216](http://ubuntuforums.org/showthread.php?t=1999216)

Kurt gave the link for the installer that Brother provides ....

if you download and run that, it should do things for you ............

---

