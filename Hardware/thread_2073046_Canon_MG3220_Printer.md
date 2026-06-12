---
title: "Canon MG3220 Printer"
date: 2012-10-18
forum: Hardware
---

### Post by K3ZV on 2012-10-18
I just got a Canon MG3220 printer.   Does anyone know how to get this working with Ubuntu ?  I cannot find a driver or a PPD file anywhere on the web.

Thanks,

John

---

### Post by dmahoon on 2012-10-18
Hi John,
 
I've got a Canon MP 630 All-in-one printer and I was able to download a Linux driver from [www.canon.com]("http://www.canon.com") in the downloads section.
 
Have you tried there?
 
DM

---

### Post by K3ZV on 2012-10-18
Hi DM,

I found drivers for the 3100 and 5200 series and not for the 3200 series. These are on the Australian site.

John

---

### Post by K3ZV on 2012-10-18
DM,

I just got the printer working.  I downloaded the driver source code from the canon site.  When I extracted the file, one of the folders was PPD files.  I loaded the one for the 3100 series and can now print in colour.  I doubt the scanner is working but I can now at least print.

John

---

### Post by dmahoon on 2012-10-19
Hi John,

Half way there I guess.

Here's another link from the forums that may help:

 [http://askubuntu.com/questions/198363/how-to-install-canon-mp610-printer-on-ubuntu-12-04-x64](http://askubuntu.com/questions/198363/how-to-install-canon-mp610-printer-on-ubuntu-12-04-x64)
  
The model number is different but it might work.  Trial and error is the name of the game it seems.  I just started using Ubuntu and every day is a new challenge!  An enjoyable one though...

DM

---

### Post by aikishugyo on 2012-10-19
The new MG series and iP7200 series have no linux drivers yet from Canon.
You can try the latest gutenprint driver compiled from CVS source, I have added experimental support for all these new models (incomplete for the upper-class models).
Please provide feedback to help with development.
Here's what works for me after checking out the CVS code (see gutenprint website for how to get the source):

./autogen.sh --enable-debug --disable-shared --with-cups-nickname=" - CUPS+Gutenprint-CVS v" --disable-libgutenprintui2 --without-doc --enable-cups-ppds --enable-testpattern && make clean && make && make install && /etc/init.d/cups restart && /etc/init.d/cups force-reload

Try to take the commands apart first (split at the && command), you need the configure to work first. You'll need many dependencies to compile, just go through them one at a time, and ask if you have trouble.

---

### Post by kreezxil on 2013-07-18
I know this is 6 months later, but after having Canon replace my MG3100 with an MG3220, I just want to say the latest gutenprint that came with the Linux Mint 14 repository that is based on the Ubuntu 12.10 build when set to the MG3100 driver works flawlessly for everything including color on the MG3220.

---

### Post by Robertjm on 2013-11-20
Clarify for me, if you would.

When you say "...works flawlessly for everything..." do you mean that printing, scanning AND fax are all working?

I need to get a color ink tank for my current printer. However, this model is on Black Friday sale for the same amount of money I'd be spending!! Might as well "upgrade" for the same amount of money.

Robert

> **kreezxil said:**
> I know this is 6 months later, but after having Canon replace my MG3100 with an MG3220, I just want to say the latest gutenprint that came with the Linux Mint 14 repository that is based on the Ubuntu 12.10 build when set to the MG3100 driver works flawlessly for everything including color on the MG3220.

---

### Post by aikishugyo on 2013-11-28
It is really good to know that the gutenprint driver works for you. There is a MG3200 in the latest gutenprint also, but perhaps requires compiling from CVS (a look at the NEWS file in the source code on sourceforge tells you when the MG3200 support was added).
Regarding scanner, gutenprint is a printer driver, for scanning one requires a scanner driver, like SANE. The latest stable and CVS SANE have online listings of which devices are supported. The source code for the pixma*.c files can also be examined to see which devices are listed at the end of each file with their capabilities.

---

