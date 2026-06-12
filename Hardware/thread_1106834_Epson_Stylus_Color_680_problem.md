---
title: "Epson Stylus Color 680 problem"
date: 2009-03-26
forum: Hardware
---

### Post by Extreedoc on 2009-03-26
Hi, complete newbie to Ubuntu, (8.10) here, I have a problem with the above printer: I am printing out the Ubuntu pocket guide and am printing odd pages and then even pages to save paper. All was going well until the printer refuses to print, error message: "Failed to print document" "Too many failed attempts". What? What failed attempts? HELP!!

I could get it to print a range of sides by turning the printer off for a while and starting over but I soon got the same message again.

PS. I hope this is the right forum for this problem, apologies if it isn't.

An Update: I gave the printer an hour or so off for bad behaviour and tried it again; this time it wouldn't print at all, same message.

---

### Post by Mark Phelps on 2009-03-26
I have an Epson R200 and encountered the same problems trying to print just about anything.  

I installed GIMP-gutenprint and now, I can print just fine from it -- selecting print with Gutenprint, instead of just Print.

My guess is that it has something to do with the default Epson drivers that is fixed in the gutenprint drivers.

---

### Post by Extreedoc on 2009-03-26
> **Mark Phelps said:**
> I have an Epson R200 and encountered the same problems trying to print just about anything.  

I installed GIMP-gutenprint and now, I can print just fine from it -- selecting print with Gutenprint, instead of just Print.

My guess is that it has something to do with the default Epson drivers that is fixed in the gutenprint drivers.

Interesting, I was just asking in the beginners forum, about alternative drivers to that which comes with Ubuntu; I was warned not to mess with it. I asked if the Linux driver supplied by Epson was ok and I also asked about Gutenprint. Can you, Mark (or anyone else), offer any insights? I looked at the Gutenprint release notes and they sure made it look complicated, do you find it so? There are also many different options, I am assuming it is the Debian option I should choose?

---

### Post by Mark Phelps on 2009-03-26
Just install cups-driver-gutenprint from synaptic.

Then, open a browser, enter "localhost:631" in the URL bar.  This will start CUPS print manager.  Click on manage printers.  You should see your printer. Select Modify the Printer.

Select Continue until you get to the Make and Model screen. Select EPSON. Click Continue.  Selectc the CUPS + Gutenprint for your model printer.

When done, you will have the Gutenprint driver installed.

When you then go back into Manage Printers, you should see a LOT of options for your printer under Set Printer Options.

---

### Post by Extreedoc on 2009-03-27
Thanks Mark, I have done all you suggested and I'm still getting the "Too many failed attempts" message. Do you have any other ideas?
John.

PS. I don't get a "Print with Gutenprint" option, just the "Print" one.

---

### Post by Mark Phelps on 2009-03-27
Sorry, I was getting the two packages confused: cups-gutenprint and gimp-gutenprint. The second supplies a Print using Gutenprint option.

I installed the second as well because I was getting exactly the same problem printing CDs or pictures, so I needed a way to print graphical images that wouldn't hang up.  After I installed gimp-gutenprint, I was able to print with it.

---

### Post by Extreedoc on 2009-03-27
Never mind, I have the Gimp Gutenprint package installed. Same problem except now the printer has gone completely nuts. The red ink light has told me that the ink cartridge is empty despite the fact that it cannot be. I have removed it anyway and reset the chip. I managed to run a nozzle test satisfactorily but the green power light is still flashing and the ink light is still on. The printer is printing page after page of gibberish. I can't shut it up! I have been forced to switch off despite the power light flashing as I have important things to do today. Desperation is setting in!
John
Update: I switched to windows, check the printers status, all fine, went back to Ubuntu and found five print jobs pending, purged them and now printer working almost without fault. Just the occasional "Too many failed attempts" message which I bypass by going back to the "Print" dialogue window and clicking "Print Preview" and printing from there.

---

### Post by MentalOxide on 2009-04-07
I've spent all afternoon with my new Epson Office t33, (after buying a lexmark z1420 yesterday and discovering it doesn't work with ubuntu) trying to get it to work, but to no avail. Online I cannot find a driver for it. I went to [http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Office_T33](http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Office_T33) and got the deb file for 32 bit systems and double clicked on it. in the /usr/share/ppd/openprinting/ folder there are a range of ppd.gz files but none for the t33 model. Am I just meant to use a file for another printer model? If so, which one?
Even the epson website doesn't list the t33 as a model in the driver section. Did I buy this printer from another dimension?

---

