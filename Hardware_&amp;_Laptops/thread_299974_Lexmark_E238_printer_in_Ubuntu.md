---
title: "Lexmark E238 printer in Ubuntu?"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by Hikaru79 on 2006-11-15
Has anyone had any luck in getting a Lexmark E238 printer to work properly under Linux? A preliminary google search turned up nothing, but I'm hoping someone here has scaled this particular wall before.

Thanks in advance :)

---

### Post by Den-Can on 2006-11-20
I got a Lexmark E232 (should be the same for E238) In the printer setup I enter HP Laserjet ( just Laserjet no model number ) and it work great ...

---

### Post by Hikaru79 on 2006-11-20
Wow, really? Who'd have thought you should use an HP Laserjet driver with a Lexmark printer... o_O; I'd never have thought of that. I'll give it a try, thanks! :)

---

### Post by Hikaru79 on 2006-12-17
Wow, strangely enough, it worked like a charm!

Actually, the quality of the final print job is not quite up to my standards (Windows, for example, prints orders of magnitude better), but it's better than nothing. Thanks! :D

Anyone have any clue WHY the HP Laserjet driver works for a Lexmark printer, but the Lexmark driver does not?

---

### Post by schuelaw on 2006-12-26
I've been screwing around with my Lexmark e238 this morning and have found that choosing a "Generic" printer manufacturer and the "PCL6/PCL XL Printer" as the model and accepting the defaults works quite well with the quality the same as under windows.  You may want to adjust the paper size too.  The default is A4.  There is a small problem with printing the test page which appears to be an A4 size regardless of the specified paper size in the driver, but if I print US letter documents they come out just fine.

Albert

---

### Post by hughh on 2007-01-03
I'm a relative newbie to Ubuntu, but managed to get Lexmark's driver (with E238 plugin) installed and it seems to be working okay.  Follow [COLOR="Blue"]_[this link]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:512:0:0&searchLang=en&os_group=Debian%20GNU&target=")_[/COLOR], or 
[LIST]
[*]go the the Lexmark[COLOR="Blue"] _[home page]("http://www.lexmark.com")_[/COLOR], 
[*]search for "E238" in the search box, 
[*]click on the "List All Drivers" link on the E238 page, and 
[*]click on "Debian GNU/Linux" link.
[/LIST]
Download and install 'print-drivers-linux-glibc2-x86.deb'.
Download 'Print-Drivers-LMABH_DRV.plugin'.
Then follow the instructions for "Using the Plugin Manager utility" in the *User Guide* located under [FONT="Courier New"][COLOR="Gray"]/usr/local/lexmark/unix_prt_drivers/docs/ug/<your language>[/COLOR][/FONT].

Hope this helps! ](*,) 

Hugh

[CENTER]Linux--the choice of a GNU generation[/CENTER]

---

### Post by omegamormegil on 2007-10-18
I have no luck with the software from Lexmark's site, and I've gone back and tried it a few times.  Every time I try printing their way, the print jobs come out covered in Postscript garbage and it wastes tons of paper and toner.  I emailed Lexmark about it, and Niraj from the Lexmark eSupport Team kindly told me this:

"I would like to tell you that this printer only supports Postscript from macintosh
From all other Operating  systems you must print PCL to make it work. there is no work around for this though as of now."

Gee, thanks for the Linux drivers, Lexmark.  

The good news, and it's _very good news_, is that Ubuntu Gutsy recognizes the printer as soon as it's plugged in, and it prints fine!  Now, if I can only get my Brother P-Touch QL500 label printer working...

---

### Post by toomuchcomputertime on 2008-02-07
I am new to forums and linux, I'll say that from the beginning. I have been trying to use our Lexmark E238 printer through a XP. It is connected to the XP, which is networked to this Ubunbu (previously ME). I have been looking through forums and googling for the past 2 days trying to fix this. I would appreciate help (the sooner the better, this is a family computer). Thanks in advance everyone.

---

### Post by toomuchcomputertime on 2008-02-13
The generic pci drivers worked with some configuration.

---

