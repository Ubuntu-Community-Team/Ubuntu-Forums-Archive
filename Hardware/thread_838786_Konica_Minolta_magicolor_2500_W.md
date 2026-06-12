---
title: "Konica Minolta magicolor 2500 W"
date: 2008-06-23
forum: Hardware
---

### Post by BlueMonkMN on 2008-06-23
So I was going to great lengths to look up info on getting and installing a driver for a magicolor 2500 W printer and found one site suggesting trying the 2400 W driver. So I was trying to figure out how to download, compile, install, and use the driver when I realized (before getting to the compile step) that the package cache already has a m2300w package which includes the 2300 W and 2400 W drivers.  Yay.  So I did sudo apt-get install m2300w and that seemed to run well.  That's the good news.

I went to the printer configuration application and managed to find the driver "Minolta magicolor 2400W Foomatic/m2400w (recommended)" so I selected that for the existing mc2500W printer, which was using a  generic driver before (never tested that).  After changing the driver, I tried to print a test page a few times, but nothing happened on the printer.  The configuration program just kept telling me that the job was sent and increasing the job number each time I tried.  It can detect when the printer is on or not (it'll be Stopped when the printer is off, or Idle when the printer is on).  Other than that, I can't find much that indicates that it's talking to the printer (the ready light is on steady and I don't see any indication that it's receiving data or having an error).  I tried running foomatic-printjob -Q and it says:
```
mc2500W is ready
no entries

```

I also tried printing from OpenOffice writer with similar results.  When I print a test page, I see print icons in the status area of the desktop momentarily (do Ubuntu folks call this the system tray or have they come up with a more distinctive anti-MS name? :) ) if that means anything.

Does this driver simply not work for the 2500 W or am I missing something?

---

### Post by stchman on 2008-06-23
That printer is reported to work "partially" according to the open printing database.

[http://openprinting.org/show_printer.cgi?recnum=KONICA_MINOLTA-magicolor_2500W](http://openprinting.org/show_printer.cgi?recnum=KONICA_MINOLTA-magicolor_2500W)

HP printers are far more compatible with Linux.

---

### Post by BlueMonkMN on 2008-06-23
Any idea why I wouldn't be getting any results whatsoever?  Do I have to change the DPI to get something?  Shouldn't I at least get an error or garbage out of the printer?

---

### Post by splarryl on 2008-10-03
Well, that's a pretty discouraging post - since I have exactly the same printer, and exactly the same problem. Just spent 2 unproductive hours trying to get it to work, and another half hour carefully collecting all the doc. 

I also note the PDF printer does not appear to work - have installed several addtional CUPS and FOOMATIC packages, but no dice.  I did come a cross a comment - somewhere out there in the ether, that this printer did work with a version of SUSE - don't remember much more.

I like Ubuntu, but - no printer is a showstopper.

I believe a complaint to Minolta is in order ... for whatever it's worth.

Good luck!

-Larry

---

### Post by oldsoundguy on 2008-10-04
I have a Konika-Minolta QMS Magicolor2 desk/laser. (CMYK color) which was given to me.

That one will NOT work in Linux.
Because it is a RASTER based printer, not Post Script.  Works fine on a Mac .. with a bunch of work I managed to get it to work on a Windows machine BUT still have been unable to calibrate the color.  So check the driver base for that printer .. if Raster, it is a lost cause at present.

Oh, and AS IF Minolta gives a da*n. (I found out mine was a Raster on a PHOTOGRAPHY forum!)

---

### Post by splarryl on 2008-10-04
Hmmm.  

Well, I guess I'm not sure if this is a "QMS" printer or not.  I am sure that model tag says only "Konica Minlota Magicolor 2500W".  Also don't know if it's raster-based or not.

I actually bought a Magicolor 2400W, which did not work out of the box.  It took one phone call to Konica, for the tech to tell me the printer was n/g, and to get a replacement - which turned out to be this "lovely" upgrade to the 2500W.

I have no problems printing in Windows (but endless other irritations with Windows).

At this point, I'm thinking the best fix - at least conceptually - is to install VMware, which I believe would alow me to switch between OSes, just long enough to print.

Thanks,

-Larry

---

