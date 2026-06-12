---
title: "Canon Printer Driver"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by measekite on 2007-09-20
[B][http://www.canon-europe.com/Support/Software/Linux/2006/download.asp](http://www.canon-europe.com/Support/Software/Linux/2006/download.asp)
[/B] 
The link above is for a Canon website in Europe that has a driver for the Canon Pixma IP4200.

I have an Canon Pixma IP4000.  I also would like to get a Canon Pro 9000.  That most likely takes a different driver and will be addressed in another post.

[COLOR=Red] The IP4000 is close to the IP4200[/COLOR] but you never know what differences there are beneath the hood.

I downloaded and extracted the manual.  [COLOR=Red]The installation instruction say that the driver is for Fedora or Suse.[/COLOR]  So my first question is will it work for Feisty?

There are also lines in some config files that may need to be changed to (what I do not know) that reference Fedora.

I have 2 weeks if Linux experience and many years of Windows experience. I find that the Windows experience does count a little but Linux is a whole new world.

If any of you readers have a printer that is close to the IP4000 and have had sucess with either this driver or another and have a desire to provide a HowTo in detail to do this I (and many others) would appreciate it.

And if anybody knows how to get a Canon Pro 9000 working properly I would also like to know this.  The printing (Canon printers) and the Scanning (Epson [4180] are the show stoppers that are preventing me form using Ubuntu as a primary OS.  I also need a replacement from quicken that can download stock quotes into a portfolio.  GNUcash does not cut it.

Thanks in advance.

---

### Post by gautada on 2007-09-20
Check [openprinting.org]("http://openprinting.org"):

[LIST]
[*][IP4200]("http://openprinting.org/show_printer.cgi?recnum=Canon-iP4000") - Mostly supported with the gutenprint driver
[*]I couldn't find the 9000 printer
[/LIST]

---

### Post by measekite on 2007-09-21
What does this mean "mostly supported with the Gutenprint driver"?  Does this mean that Gutenprint uses its own built in driver?  If so the results are not good and it only prints in low resolution.

Can't Gutenprint use drivers outside of Gutenprint if they are there and just act like a GUI to the driver?

---

### Post by pirxx on 2007-09-23
Here are the Canon IP4200 drivers, convereted from rpm to deb using Alien. 

YOU DOWNLOAD THESE DRIVERS ENTIRELY AT YOUR OWN RISK. THERE IS ABSOLUTELY NO WARRANTY, NEITHER IMPLIED OR EXPRESSED REGARDING THESE DRIVERS. THESE DRIVERS CARRY ABSOLUTELY NOSUPPORT,  NEITHER FROM CANON NOR FROM ANYBODY ELSE!

[http://www.pirx.net/ubuntu/canon/](http://www.pirx.net/ubuntu/canon/)

---

### Post by gautada on 2007-09-24
> **measekite said:**
> What does this mean "mostly supported with the Gutenprint driver"?

Well if you follow the link it tells you what it means

> **measekite said:**
> Does this mean that Gutenprint uses its own built in driver?

Since gutenprint is a print driver yes it uses it's own driver

> **measekite said:**
> If so the results are not good and it only prints in low resolution.

If you say so but I am able to print @1600dpi but then again I read the information provided in the links.

> **measekite said:**
> Can't Gutenprint use drivers outside of Gutenprint if they are there and just act like a GUI to the driver?

Why? just use cups as your mechanism and choose which driver (including gutenprint) for the job it is best suited.

---

### Post by measekite on 2007-09-24
[QUOTE=gautada;3418098]Well if you follow the link it tells you what it means


If you say so but I am able to print @1600dpi but then again I read the information provided in the links.



Please be specific.  What information did you read and where did you read it that allows you to print at that resolution.

Also, would you say that with Gimp and Gutenprint I can get the same high quality results that I can get with either Gimp for Windows or Photoshop 7 for Windows?

And if I wanted to use Gutenpriont as a GUI and use an official Canon (IP4100) driver could I do so and how do I do it?

---

### Post by gautada on 2007-09-25
> **measekite said:**
> Please be specific.  What information did you read and where did you read it that allows you to print at that resolution.

As referenced on my first post I setup the gutenprint driver for the  4200 because it was referenced on openprinting.org.  This was setup in CUPS.  This is a setup via the standard System->Administration->Printing with specific selection of gutenprint.  You should follow the gutenprint [docs]("http://gutenprint.sourceforge.net/p_Documentation.php3") for specific settings.

> **measekite said:**
> Also, would you say that with Gimp and Gutenprint I can get the same high quality results that I can get with either Gimp for Windows or Photoshop 7 for Windows?

I don't know.  I don't run windows.

> **measekite said:**
> And if I wanted to use Gutenpriont as a GUI and use an official Canon (IP4100) driver could I do so and how do I do it?

I still do not know what you are trying to do here.  Drivers are drivers use CUPS as your interface.  I do not believe that you can use gutenprint with a proprietary driver.

After reviewing your post and noticed that you have to [4000]("http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP4000") not the 4200.  Again if you lookup the printer you would see that this printer is described as  "Color inkjet printer, max. 4800x1200 dpi, works Perfectly".  Read the gutenprint docs and setup the printer.

---

