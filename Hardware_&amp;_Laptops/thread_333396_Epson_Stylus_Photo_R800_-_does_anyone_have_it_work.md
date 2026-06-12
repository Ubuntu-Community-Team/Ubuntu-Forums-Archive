---
title: "Epson Stylus Photo R800 - does anyone have it working?"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by chrisccoulson on 2007-01-07
I have purchased an Epson Stylus Photo R800, which I am now trying to get working with Dapper (64-bit). I have the printer connected via USB. When I went to System->Administration->Printers to add a new printer, the correct printer was detected and the correct Gutenprint driver was selected.

However, I have yet to successfully print anything. I have tried printing numeous photographs on to 4"x6" paper from the Eye of GNOME and gThumb, but the images are offset such that the printer only prints a quarter of the image in to one corner of the paper. Also, all of the colours are misaligned. The print preview shows the image correctly aligned with the paper.

I have also tried printing a test page on to 4"x6" paper (as it is the only size I have at the moment). The test page doesn't align correctly with the paper either (although, I get the impression that it is trying to print the test page on to Letter size paper despite me selecting 4"x6").

Does anyone have this printer working under Ubuntu?

---

### Post by bmt on 2007-01-07
I would suggest starting off with a less ambitious project than a photo from Gimp.  Try basic text printing first, from gedit/kate in monochrome and on plain paper (full sheet -- A4 or Letter, depending on where you are).

Once you've got that reliable, progress to printing graphics (from, say, OpenOffice), again on a full sheet, so that you can more easily see if the system is working as it should.  It's cheaper to use plain than photo paper for this testing.

Good luck!

---

### Post by chrisccoulson on 2007-01-07
Thanks for the suggestion. It wasn't actually GIMP that I'd tried printing from earlier - it was gThumb and Eye of GNOME.

I've tried printing out some basic text on A4 from Openoffice, and it seems to print ok.

I've also managed to print a photo from the GIMP using the Gutenprint R800 driver. However, it did print the image off-centre - leaving uneven borders. It also took a very long time to print (approximately 20 minutes for a 4"x6" image + 5 minutes to send the image to the printer). However, the print quality looks superb. I know it shouldn't take this long to print though...

But I still can't get anything to print correctly from Eye of GNOME or gThumb :( 

I've also tried the Turboprint demo drivers. While I can get everything to print correctly, the quality is not a patch on what I've managed to get with Gutenprint.

Ideally, I need to be able to print from Eye of GNOME or gThumb with relative ease, as this is my girlfriends printer.

Cheers

---

### Post by bmt on 2007-01-08
Have a look at gtklp -- it's in the repos, so you can install it with Synaptic.

It gives easy access to all the printer settings, so you can find a better compromise between quality and speed.  You may also find something connected with the positioning (margin settings, maybe?).

Also, check out the [Linux Printing page]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R800") and the link from there to the LP Epson forum.  You may find more specialist knowledge there, too.  There have been other issues with print position on Epsons, but as it didn't affect me, I never took a lot of notice at the time.

---

### Post by catty62 on 2007-04-20
I have an Epson Stylus Photo R800 that work on a Dell Inspiron 8200 with Kubuntu Edgy Eft 6.10 with the standard driver that I found during the installation from the Kcontrol.
I have also a Dell Precision M90 (for work) with Feisty Fawn 7.04 and I am not able to install the printer, because in Kcontrol I have not been find the Epson Printer model (Epson Stylus Photo R800).
I tryed [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R800](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R800) and [http://www.avasys.jp/english/linux_e/dl_ink.html](http://www.avasys.jp/english/linux_e/dl_ink.html) that I found in forum but in any case I could not install the printer.
Could anyone suggest me a possible solution and steps to take to be able to install the printer?
Thanks in advance
Lino
:confused: :(

---

### Post by marcovaldo on 2007-04-22
It works for me (using kubuntu 07/4).
I installed all the packages related to gutenprint using Adept, and the printer simply appeared in the list of the vailable printers :))

---

### Post by catty62 on 2007-05-13
I have tried your suggestion without to be able to find the print in driver list.
Tnk anyway.:(

---

### Post by ramjet_1953 on 2007-05-13
Here's another link that may be of help.

[http://www.avasys.jp/english/linux_e/dl_ink.html](http://www.avasys.jp/english/linux_e/dl_ink.html)

The driver can only be downloaded as an RPM package or a sourcefile.

The RPM may convert OK using alien

If you are familiar with compiling your own binary from source, it would probably be the best way to go.

Regards,
Roger :cool:

---

