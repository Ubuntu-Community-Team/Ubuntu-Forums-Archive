---
title: "New HP Photosmart 5720 printer experience on Ubuntu Lucid"
date: 2012-12-22
forum: Hardware
---

### Post by OrangeVixen on 2012-12-22
I wrote these notes while installing a new HP Photosmart 5720 printer I got:

It's an All-In-One printer that has Scanning and FAX, which both features work with Linux under Ubuntu (I'm using Lucid 10.04 btw). The printer cann also scan and FAX independent of any computer too.

It took about an hour to actually get the printer out of the box, put it together (install ink and remove a bunch of packing tape*) and just connect it to the computer, it does not come with any instructions aside from a diagram on how to connect the power cable and warrenty. I used a USB connection since I was not comfortable with wireless in my area.

*You need to make sure that you remove ALL the physical blue packaging tape that was on the actual printer, there are a lot and if you miss one or two it can cause things to jam.


Installing:

First, make sure that you upgrade hplip, I needed to upgrade to hplip version 3.12.10a for things to work. [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

Once I connected the printer to the computer (via USB) and powered on the printer everything was auto-detected. But in case it did not auto detect this is what you need to do:

Run: hp-toolbox
Go to: Device->Setup Device...
Select your connection type (I used the USB connection), then HP as the manufacturer. It should then auto-detect and give you two listings;  Photosmart_7520 and Photosmart_7520_fax, one is for the printer and the other is for the FAX.

I suggest that you set the verbose description to include "Printer" to distinquish that from the "FAX", e.g. "HP Photosmart 7520 Printer" and "HP Photosmart 7520 FAX", and the identifier name should be "Photosmart-7520" and "Photosmart-7520-FAX" (respectively). That will really help when you are looking for the right one in an application's printers list.

There is no entry for the scanner, it's handled differently (see scanning section below).

Remember to set the printer (not the FAX) as the default, for some reason it sets the FAX as the default sometimes. In hp-toolbox select the printer ("Photosmart-7520") in the list and go to Printer Control->Set As Default.

You may also need to log out and log in again for the "Actions->Print Test Page" and other things to work (I'm not sure why).


Print from computer to printer:

Testing with GEdit and GIMP both print without any major problems.

Some of the things you might run into is that you need to make sure that the correct printer is selected (make sure that you select the printer and not the FAX, seems like a silly thing to point out but having the wrong one selected happens more often than you think).

You may also need to set EACH OF YOUR application's Printer Properties or Printer Setup and make sure that "Paper Type" and "Paper Source" are set to some value OTHER than Automatic. Typically this is under Print...->Page Setup. If you do not set this then you may get some kind of "conflict error". For the Paper Source, the Main Tray refers to the lower (lowest) physical tray on the printer and the "Photo Tray" refers to the removable tray just above it (where smaller photo paper is placed).

Also, be sure to go through every setting just to be extra sure you have everything set correctly before you click on Print.


Borderless printing using GIMP:

This works too, but requires a lot of steps and things to check.

First open your image in GIMP and then go to File->Page Setup, set Format For to "Photosmart-7520" and the Paper Size, if you want to print (for example) on 4x6 inch photo paper select "Photo Borderless 4x6in". Note that it will say 4.22 inches wide and 6.2 inches height (I think this is for the full bleed/borderless effect, and not that the paper is actually that size). Click Apply.

Then make sure that the image you are printing is the correct size and resolution by going to Image->Print Size... make sure it is set to 4 INCHES in width and 6 INCHES in height (double check the units). You may need to adjust/resize/crop your image in order to get the right size.

Once you have double-checked everything, go to File->Print... and make sure Page Setup->Paper Size (it may be insensitive/greyed out) says "Photo Borderless 4x6in" (you can change this in File->Page Setup as mentioned above).

Now physically load the 4x6 inch photo paper in the upper tray (the long 6 inch end goes into the printer) face down. Set Page Setup->Paper Source to "Photo Tray".

Under Image Settings you can visually see if everything is correct, check "Ignore Page Margins" and make sure that the Width and Height are set to the highest value (about 4.131 and 6.196 respectively), Center should be set to "Both".

Also check all the other options as well (Color, Image Quality, etc). Image Quality needs to be set to "Normal" or better.

Click on Print.

NOTE: sometimes the printer will give you an error saying there is a paper size "mismatch" (on the printer's display), I think this is a bug with the printer itself as it never reports it to the computer/Linux. Just reload the paper and click Ok. I had to retry 3 times to get it to finally recognize it. If you press the red X it will report to Linux that it finished printing but never actually print.


Scan from printer to USB memory stick:

Just a quick note, you need to have your USB memory stick to be formatted to FAT/VFAT in order for the printer to be able to write the scanned images to (it will not accept NTFS, HFS, EXT#, etc).


Scan from printer to computer via USB:

You can only initiate a scan from your computer under Ubuntu and HPLIP (not from the printer to the computer). I have tested it and it works using simple-scan and XSane.

Using simple-scan, you need to go to Document->Preferences to make sure everything is set up correctly as the application's settings override the scan settings you last set on the printer. For some reason there are two listings for the scanner, I think it's because there is a printer and a FAX, but selecting either one works the same.

You can safely set the Page Size to Automatic for scanning.

If you want to scan in color then make sure that you set Document->Scan->Photo.

You can place the document in either the document feeder (the small lid that you flip open to the left that is on TOP of the printer) or the single page scanner (the lid that opens away from you). If you place the document(s) in the document feeder then make sure that you to go Document->Scan->All Pages From Feeder. If you place the document in the single page scanner then go to Document->Scan->Single Page.

---

### Post by BarryM on 2013-01-13
Thanks for this posting, I have jsut got a 6520 (same as the 7520 except no fax), and have problems getting it to scan. HPLIP does not find the printer on a wireless connection (pity they dropped the wired network port I had on my C5180), but I managed to get it conencted using the Ubuntu printer setup facility.

Has anyone managed to get one to work wirelessly through HPLIP, and if so some tips would be most welcome, as I do not really want to use the USB unless I really have to!

---

### Post by offgridguy on 2013-01-13
OrangeVixen;  Thank you for sharing this.:D

---

### Post by BarryM on 2013-01-17
Well, I managed to get everythign up and running relatively painlessly. I followed OrnaggeVixen's advice and downloaded the latest HPLIP (3.12.11) but the first installation attempt failed as I was missing Python bits. Once I had those installed the second installation attempt sailed through with no problems.

The setup stage had a slight hickup as the detection software did not find my printer until I entered the ip address, but once that was in, it all set itself up happily.

Only problem is that I neglected to remove my earlier installation of the printer using the Ubuntu native printer setup, so I have two instances of the printer showing in the Ubuntu printer dialog, and am not sure which one I need to delete! So, to anyone else trying to do this, if you have already got the printer installed by some means other than HPLIP, don't forget to delete it before you start the HPLIP setup!

Printing and Scan both work well, so altogether I am rather pleased with the whole operation, and the printer (especially the duplex printing facility, which works very well).

The only issue I now have is that a folder has appeared on my desktop called hplip-3.12.11, and I am not sure whether this is just the installaton files and can be deleted or not. Does anyone know?

---

### Post by OrangeVixen on 2013-01-17
> **BarryM said:**
> 
The only issue I now have is that a folder has appeared on my desktop called hplip-3.12.11, and I am not sure whether this is just the installaton files and can be deleted or not. Does anyone know?

I had problems of multiple instances too, but with the scanners (Simple Scan and XSANE), I think it's because there is a fax and one is a printer instance that it gets its configuration from.

You definitly should try a restart, espessially if you had to remove old packages.

The folder on the desktop is probably harmless, I did not have a copy of it. Try renaming it and then run hplip again to see if there are any problems, do a test print too.

If everything is normal then you can probably remove it.

---

### Post by BarryM on 2013-01-21
O dear, I thought everything was going well until I tried to scan today (I have previously tested the scanner and it worked fine, using gscan2pdf). All I got was Communications Error! I ran up the HP Device Manager and it showed my printer disconnected with an error 5012, despite the fact that I had printed using it a short while previously. What now? I wonder if I should reinstall HPLIP? I have not done anything to that folder on my desktop. Any thoughts?

---

### Post by OrangeVixen on 2013-01-21
> **BarryM said:**
> (I have previously tested the scanner and it worked fine, using gscan2pdf). All I got was Communications Error!


I've got that "communications error" a couple of times but with HPLIP when I open the toolbox while the printer is idle, it usually takes a while for it to start up if the printer went into idle mode and then a refresh works.

But for scanning I'm afraid I'm not sure, if you are using it via wireless then you may need to try and restart the printer. I am using USB though, I have tried printing wireless before it a simple bit of static will cause bizzare printed output.

---

### Post by BarryM on 2013-01-22
Problem solved: it was all down to the IP address, which, for some reason I cannot fathom, changed from xxx.xxx.1.3 to xxx.xxx.1.4. So, uninstall and reinstall and it works. It is all rather anoying, and I hope it does not decide to keep changing its IP. I think the root of the problem is that HPLIP does not auto detect the printer, so I had to use the Manual Discovery option in the Advanced Options dialog and enter the IP manually. I don't know if there is any way round this. If it keeps happening, I think I will probably have to resort to USB.

I wonder it it would be worth signing up to the HPLIP support site and seeing if there are any tips there?

---

### Post by OrangeVixen on 2013-01-22
> **BarryM said:**
> Problem solved: it was all down to the IP address, which, for some reason I cannot fathom, changed from xxx.xxx.1.3 to xxx.xxx.1.4.

Do you know if you use Network Manager? Check by running Synaptic and see if it's installed, select Installed software on the category list and type in "network manager" in the search box.

Sometimes when the printer goes offline or idle, and reconnects, the IP will change if it's on a network.

---

### Post by BarryM on 2013-01-23
Yes I have got network manager installed. I supppose it is just one of the quirks of wireless networking. I wonder if I can get an ethernet adapter to plug into the USB on the printer, so I can use a wired connection.

I also found, since doing the reinstall, that I have lost duplex printing, which is a nuisance to say the least, since that is the reason I opted for this printer. I think it may be easies in the end to switch to USB connection, although that does limit me to printing from my desk-top PC. Not a problem now, but, if I get a laptop it would be a nuisance.

I did find, when I switched my old printer (HP C5180) from USB to wired network cinnection, HPLIP seamlessly set it up for me. Perhaps I could try setting it up as USB then changing to wireless and seeing if it sets itself up automatically.

---

### Post by OrangeVixen on 2013-01-23
If you reinstalled HPLIP, you might want to update the print settings between
the removal and (re)install.

Because HPLIP claims to set up printers for you and works alongside CUPS or whatever native printing system you are using. It may not sync all the printer instances.

Try running:

system-config-printer

Or for CUPS:

firefox [http://127.0.0.1:631/admin](http://127.0.0.1:631/admin)

Check if everything is setup correctly there.

---

