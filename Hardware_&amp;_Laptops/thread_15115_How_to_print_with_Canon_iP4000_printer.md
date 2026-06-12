---
title: "How to print with Canon iP4000 printer"
date: 2005-02-12
forum: Hardware &amp; Laptops
---

### Post by net_benjo on 2005-02-12
I think ubuntu is great and I would really like to be able to set up my printer on it.  

I have Canon Pixima iP4000 printer.  The following is what I've done to try to get my printer working..

1) in gnome panel:: Computer>>System Configuration>>Printing.   I clicked on 'New Printer', however, because my printer model is fairly new, it wasn't listed there.

2)  I searced the ubuntu forums with surprisingly little luck.  It seems not many pple have problems setting up their printer..

3) I did a google search on 'ip4000 linux drivers'.  I found Turboprint drivers which claim to work.  I tried them and they did work.  However, because it is a free version their logo always prints on the pages I'm printing. 

My question is:  what are my choices.  Do I just have to by the licence for abour $30 bucks or can I print in some other way?

Thanks...

I loved the Ubuntu Startes Guide..but I was dissapointed that it didn't have ANYTHING on setting up your printer.

---

### Post by kleeman on 2005-02-12
If you can find the ppd file for this printer on the windows drivers cd you can sometimes use this:
Install kprinter (you need to have universe enabled) "apt-get install kprinter"
Fire up kprinter from a commandline
choose "add printer" (wand like button) this activates a wizard
choose 
Next
local printer (select your printer from the usb section if you have it plugged in there)

Choose "Other" in the next dialog and then select the ppd file. Complete wizard
Sometimes this works sometimes it doesn't

---

### Post by net_benjo on 2005-02-12
thank for the tip keeman...

I will do as you say and will let everyone know if it worked....

---

### Post by rykel on 2005-03-20
hi,

i am also trying to find the linux driver (ppd files will do too) for a canon pixma ip3000.

unfortunately, e best i can track down would be e "inf" files in windows XP... is there any wrapper for or a way tat linux can use tis?

if anybody can find e ppd files for our ip4000 and ip3000 respectively, it will be greatly appreciated!

as for e alternative, turboprint, i cannot afford it, and they do not offer a full-featured, non-commercial alternative.

---

### Post by grenadier on 2005-03-20
Adding a printer, any make, any model, try the following.

Gnome Desktop->System->Administration-->Printing

Select manufacturer, scroll for model, if model not found then note that there is a facility for installing a driver and insert the driver that came with your printer.
If unsuccessful, then choose Generic.
Try PCL 6/Pl XL Printer. 

Before making a Test Print, alter the printer settings to suit your printer.

One of the Generic Printer classes listed under Generic should work with your printer.

KDE Desktop->Control Center->Peripherals->Printers->add Printer/Class

Follow the same procedure as per Gnome.



It isn't rocket science, have a look on the Printer Manufacturers WebSite for the number of models that use the same driver! Note that some manufacturers installation CD's include Linux Drivers too!

---

### Post by kagou on 2005-03-21
iP3000 is supported with the bjc7000 free driver. Limitation is that you can print at more than 600dpi.

---

### Post by rykel on 2005-03-21
Hi Kagou,

Is there a difference between BJC 7000 and BJC-7000? (with a hyphen)

Coz. both are available in the Linux driver database...

Thanks for clarifying!

And to Grenadier, that sounds interesting... I'll try loading my Windows XP driver CD into Linux... if successful, I'll tell you all, ok?


Best Regards,

Rykel
Singapore

UPDATE: Fat hopes with the Canon CD... nothing that could be used by Linux in there... btw, I wonder if CrossOver or WINE can be invoked to load those Windows drivers on that CD?

---

### Post by kagou on 2005-03-21
Sorry i don't know, cause i 'v bought license for turboprint.
 :(

---

### Post by beerorkid on 2006-04-26
thank you so much

from warty to dapper I have never been able to print.  I have spent sooooooo many frustraiting hours trying every howto, gutenprint, foomatic, network printing to a XP machine, even smacking the side of the printer ;)

THANKS!!!!!!!!! :)

---

