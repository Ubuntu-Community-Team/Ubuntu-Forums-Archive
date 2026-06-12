---
title: "Epson Workforce Pro 4530 print quality"
date: 2013-09-15
forum: Hardware
---

### Post by rebecca3 on 2013-09-15
Hi all,

I'm working to transition my small law office to Ubuntu. So far so good except for our Workforce Pro 4530 printer. I have the Epson drivers (both of them) installed and a print queue set up with the appropriate model. However, text printouts look like crap even at the highest quality setting. I can print out a PDF from my old MacBook, and it looks gorgeous and prints fast. Printed from Ubuntu, even with fonts properly embedded, it looks awful and granular and prints slowly. Documents created in LibreOffice Write using Ubuntu system fonts are similarly granular looking. It looks like the kind of copy that would come out of a '90s home inkjet printer!

I also noticed that in the CUPS settings panel, I'm not allowed to select over 300 dpi for output quality. However, I'm not sure this is responsible for the shoddy quality.

Although I'm a lawyer, my passion is for public defense...which means the office is on a shoestring budget AND that I require my docs to look professional.

Any help will be much appreciated. This printer is my only hurdle to migrating fully to GNU/Linux.

Thanks!
Becca

---

### Post by tgalati4 on 2013-09-15
MacBooks use CUPS for printing as well, so let's compare printer drivers.  Plug the MacBook into the printer and open Safari:  [http://localhost:631/printers](http://localhost:631/printers)

What is the driver that the Mac is using?

It will look something like:

Description:	Color Injet Printer
Location:	Terry's Office
**Driver:	HP Officejet 7300 Series, hpcups 3.12.6 (color, 2-sided printing)**
Connection:	hp:/net/Officejet_7300_series?zc=Officejet7310
Defaults:	job-sheets=none, none media=na_letter_8.5x11in sides=one-sided

Open up a browser on your Ubuntu machine and check [http://localhost:631/printers](http://localhost:631/printers)

What driver are you using?

---

### Post by rebecca3 on 2013-09-17
Thanks for taking the time to reply, tgalati4. 

The driver on the Mac is: EPSON WP-4530 series (color, 2-sided printing)

On Ubuntu, it's: Epson WP-4530 Series - epson-inkjet-printer 1.0.2-1lsb3.2 (Seiko Epson Corporation LSB 3.2) (color, 2-sided printing)

---

### Post by tgalati4 on 2013-09-17
Well, you have at least confirmed that you are using two different drivers.  On the Ubuntu machine, try adding a new printer in the browser, under Administration, Add Printer.  Look through the printer drivers and see if there is a driver called **EPSON WP-4530 series (color, 2-sided printing)**.  Do not select the driver *epson-inkjet-printer 1.0.2-1lsb3.2*.

What is the difference in CUPS versions?  [http://localhost:631/](http://localhost:631/)

It's possible that they are really the same driver.  Look in the job options for a print quality setting.  Set it to high and then select 600 dpi.  It's possible that you can't select above 300dpi because print quality is set to Normal by default.  Normal is really draft or fast printing.

---

### Post by rebecca3 on 2013-09-17
Thanks for your time--on the Mac, it's CUPS 1.4.7, and on Ubuntu it's 1.6.2. Unfortunately, the only other driver option is epson-inkjet-printer-escpr 1.2.3-1lsb3.2, which gives the same results. With either driver, the only way to increase  the default print quality on the CUPS "default options" page  is to also change the paper to heavy matte, glossy, etc. options that require using a separate, low-capacity rear tray.  

Maybe the drivers are just inadequate? I see there are gutenprint driver options for most Epson models, but not this one.

---

### Post by tgalati4 on 2013-09-17
A quick google search brings up this:  [http://download.ebz.epson.net/faq/linux/faq_li_00001.html](http://download.ebz.epson.net/faq/linux/faq_li_00001.html)

Although inconvenient, do you get high quality printing using the alternate tray?  In other words, does the printer driver produce high-quality output when using the rear tray?

You might consider taking the PPD file from the Macintosh and copying it over to the Ubuntu machine and then selecting it when creating a new Printer in CUPS in Ubuntu.  It's an involved process, but one worth pursuing.

For instance, I found epson printer PPD files here:

tgalati4@tpad-Gloria7 /usr/share/ppd/openprinting/Epson $ ls -la
total 352
drwxr-xr-x  2 root root  4096 2009-04-20 07:04 .
drwxr-xr-x 11 root root  4096 2009-04-20 07:04 ..
-rw-r--r--  1 root root  8234 2009-03-27 03:06 epal2600.ppd.gz
-rw-r--r--  1 root root  9990 2009-03-27 03:06 epalc190.ppd.gz
-rw-r--r--  1 root root  9124 2009-03-27 03:06 epalc200.ppd.gz
-rw-r--r--  1 root root  8222 2009-03-27 03:06 epalc260.ppd.gz
-rw-r--r--  1 root root  8402 2009-03-27 03:06 epalc280.ppd.gz
-rw-r--r--  1 root root  8504 2009-03-27 03:06 epalc380.ppd.gz
-rw-r--r--  1 root root 10402 2009-03-27 03:06 epalc400.ppd.gz
-rw-r--r--  1 root root 10330 2009-03-27 03:06 epalc410.ppd.gz
-rw-r--r--  1 root root  8114 2009-03-27 03:06 epalc420.ppd.gz
-rw-r--r--  1 root root 11055 2009-03-27 03:06 epalc860.ppd.gz
-rw-r--r--  1 root root 11544 2009-03-27 03:06 epalc910.ppd.gz
-rw-r--r--  1 root root  7505 2009-03-27 03:06 epalcx21.ppd.gz
-rw-r--r--  1 root root  8357 2009-03-27 03:06 epalm200.ppd.gz
-rw-r--r--  1 root root  8360 2009-03-27 03:06 epalm201.ppd.gz
-rw-r--r--  1 root root  7522 2009-03-27 03:06 epalm400.ppd.gz
-rw-r--r--  1 root root  8031 2009-03-27 03:06 epl5900.ppd.gz
-rw-r--r--  1 root root  8039 2009-03-27 03:06 epl6100.ppd.gz
-rw-r--r--  1 root root  7653 2009-03-27 03:06 epl6200.ppd.gz
-rw-r--r--  1 root root  9237 2009-03-27 03:06 epln2500.ppd.gz
-rw-r--r--  1 root root  8162 2009-03-27 03:06 epln2550.ppd.gz
-rw-r--r--  1 root root 11211 2009-03-27 03:06 epln2700.ppd.gz
-rw-r--r--  1 root root  8022 2009-03-27 03:06 epln3000.ppd.gz
-rw-r--r--  1 root root  8945 2009-03-27 03:06 epln7000.ppd.gz
-rw-r--r--  1 root root 11069 2009-03-27 03:06 eplp830c.ppd.gz
-rw-r--r--  1 root root 11059 2009-03-27 03:06 eplp850c.ppd.gz
-rw-r--r--  1 root root 11924 2009-03-27 03:06 eplp880c.ppd.gz
-rw-r--r--  1 root root 10259 2009-03-27 03:06 eplp9100.ppd.gz
-rw-r--r--  1 root root 10632 2009-03-27 03:06 eplp920c.ppd.gz
-rw-r--r--  1 root root 11260 2009-03-27 03:06 eplp950c.ppd.gz
-rw-r--r--  1 root root 12441 2009-03-27 03:06 eplp960s.ppd.gz
-rw-r--r--  1 root root 11551 2009-03-27 03:06 eplp980c.ppd.gz

So compare the PPD files between the Mac and Ubuntu.  Even try coping the Mac PPD file to Ubuntu, giving it a unique name.

I think I found the issue:  [http://www.linuxfoundation.org/collaborate/workgroups/openprinting](http://www.linuxfoundation.org/collaborate/workgroups/openprinting)

CUPS 1.6.X now uses PDF for all printing.  Previous CUPS used a mixture of Postscript and PDF  for printing.

So, I presume that your Mac uses a Postscript file that gets sent to the printer and produces high-quality output that you expect.  Ubuntu runs the print job through a filter that converts your print (from Postscript-to-PDF) and then sends to the printer.  Something gets lost in the translation, resulting in a low-quality print.  I don't know if there is a setting or a filter that can get the CUPS 1.4.X behavior on Ubuntu, but there must be a work-around.  So keep searching.

I would try to find someone on this working group and send them a link to this thread: 

[http://www.linuxfoundation.org/collaborate/workgroups/openprinting/pdf_as_standard_print_job_format](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/pdf_as_standard_print_job_format)

---

### Post by Christina_Stephens on 2013-09-22
So, basically there is no solution to this problem yet from what I've read above.  Printing to my Epson WP-4530 is also my last hang up to converting my school room to Ubuntu. =/

Thank you tgalati4 for trying to help and to Rebecca for asking.

Edit: 

I got it working!  I initially downloaded the driver from the Epson website and I also tried the one from open printing link from above.  Instead of using those, Rebecca4, try using the driver from the Software Center called EPSON WP-4015/4525 Series - Epson Inkjet Printer Driver  (file name is: epson-inkjet-printer-201113w).  After I installed it through the software center, I added the printer through the system settings>printers>add>Network Printer dropdown>Espon WP-4530 (ip address)> and then it was there and prints graphics and text beautifully.  

I hope this helps.  I tried much more complicated methods before this, but I guess I should just try to keep it simple.
Chris

---

### Post by tgalati4 on 2013-09-22
Are there settings on the printer front panel that allow you to change its personality from Postscript to PDF?  Perhaps check the advanced settings or look in the manual for such settings.  Perhaps you just need to change the printer's personality to get it to work with the default CUPS driver.

---

