---
title: "Brother HL-1440 Laser Printer"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by jhuff on 2005-06-19
I can not get my Brother HL-1440 laser printer to work
correctly.

I can set it up and and print a test page. However if I try and print a
document that is longer than one page it locks up the printer. I can print
single pages all day long. I am using the recommended hl1250 driver.

This printer is a network printer connected to a Windows XP computer.

If anyone has any ideas?

---

### Post by David Haas on 2005-06-19
Hi jhuff--I think it's worth trying the other PPD files for the Brother HL-1440 Laser Printer that are present in Hoary. Besides the Brother-HL-1440-hl1250.ppd.gz, I see listed in /usr/share/cups/model/foomatic-ppds/Brother these two files: Brother-HL-1440-hpijs.ppd.gz; Brother-HL-1440-ljet4.ppd.gz.  
David

---

### Post by jhuff on 2005-06-21
I've tried all the HL-1440 drivers.  The one that seems to work the best is "Brother HL-1440 Foomatic/gimp-print-ijs"    However I still can only print one page at a time.  If I try anything more than that the printer locks up.

I love Linux but it sure is frustrating not being able to print.  I sure would appreciate hearing about any other ideas people may have.

---

### Post by doans on 2005-06-25
I also have a Brother HL-1440 and can print more than one page at a time with no problems.  However, if I try to print multiple pages and they have alot of graphics on them then they don't print.  It doesn't lock the printer up, but the pages simply don't print.  I think it is something to do with the printer memory.  I have extra memory installed in the printer and in WinXP you have to update the memory size in the driver settings. But I have never seen any settings for this in Linux.

Are the pages you are trying to print all graphics and pics?  Have you tried to print multiple pages of simply text?

I am using the default driver with this printer. HL-1250 driver.

---

### Post by jhuff on 2005-06-27
I just tried printing a text document and it printed both pages without any problems.  However, when I print a pdf file the printer locks up after printing the first page.  I have not added any extra memory to the printer.  Can you print pdf files without any problems?  Maybe I just need to add some extra memory to the printer.  How much memory do you have installed?

---

### Post by doans on 2005-06-28
[QUOTE=jhuff]I just tried printing a text document and it printed both pages without any problems.  However, when I print a pdf file the printer locks up after printing the first page.  I have not added any extra memory to the printer.  Can you print pdf files without any problems?  Maybe I just need to add some extra memory to the printer.  How much memory do you have installed?[/QUOTE]
 Yes, I can print pdf files without any problems. Except if the pages are mainly graphics as I mentioned earlier.

I have 34MB (the maximum) of memory installed, but I have no idea how the linux driver handles the installed memory.  Is there a way to tell the driver that the printer has more memory?

So, generally if I have to print multiple pages of graphic intensive pages I simply print them one page at a time.  This seems to work 95% of the time.  Not really a fix, but it usually gets the job done.  Hope some of this helps.

---

### Post by jhuff on 2005-06-29
Were did you get the memory chip for the printer?

---

### Post by doans on 2005-06-29
[QUOTE=jhuff]Were did you get the memory chip for the printer?[/QUOTE]
 I found the memory online I don't remember exactly where right now.  I have had the printer for quite some time now.  However, you simply need to look for [font=Verdana, Arial, Helvetica, sans-serif][size=2]72-pin SIMM they are extremely cheap.  Should be able to find them almost anywhere online.
[/size][/font]

---

### Post by jhuff on 2005-09-20
Still haven't added any memory but I'm wondering if anyone has had any luck getting the printer to work when its connected to a windows computer.

---

### Post by jhuff on 2005-10-04
I have finally got my Brother HL-1440 printer working after I installed a Linksys PrintServer PSUS4 onto my network.  It was not easy to get working with the windows computers connected to my network, but I finally did get it working.  I am connecting the server to a Belkin wireless router (this could be one of my problems).  I must have turned everything on an off a dozen times trying to get everything squared away.  I did set a static IP address for the server becuase I was getting network address conflicts.  So I am still at a loss as to how I finally got the windows computers working correctly.  As far as my linux box I did the following:
Added a new printer using "Unix Printer (LPD)"
Host = Server IP address (192.168.2.xxx)
Queue = L1
I initially tried using CUPS Printer (IPP) but whatever I printed just kept printing multiple copies until I cancled the print job.
It was easier getting my linux box working then the windows computers.
I still can't believe I got my printer working.  I have been trying for months to get the Brother HL-1440 to work.  Now I can finally move totaly away from Windows!!  I am totaly impressed with Breezy Badger.

---

### Post by GOwin on 2006-02-22
My printer works ... somewhat.

Printing regular documents from abiword and inkscape works fine. However, trying to print from landscape mode doesn't work properly.

It starts printing in the middle of the paper. I'm using the hl-1250 driver recommended by the gnome cups manager when it was auto-detected

---

