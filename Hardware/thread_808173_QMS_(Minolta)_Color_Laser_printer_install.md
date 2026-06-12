---
title: "QMS (Minolta) Color Laser printer install"
date: 2008-05-26
forum: Hardware
---

### Post by oldsoundguy on 2008-05-26
I acquired an older QMS Magicolor 2 CMYK (color) laser printer from a government auction.  (the same printer made for Minolta and Konica) Looks brand new and I ran the off line tests .. works perfectly and has a beautiful print out.  (that's why I bought it for less than 10 cents on the dollar.)
These units cost nearly $1000 USD when new and newer versions are in the same price range.  Plus, this one has had less than 10,000 sheets printed and they dumped it (your tax dollars at work!)

The problem is, I can't get a computer to talk to it!

Tried to get Gutsy to see it to no avail. (no drivers in cups/foomatic/gutenprint) .. I CAN see why, as there is really not a demand to develop same for so few units out there.
The Linux hardware site calls it a "paper weight" so am curious if anyone has found a hack to get this operational.

It will not work in XP SP2 either! (even using their install hardware lizard, which claims to have the drivers!)
(on line driver download installs a "non approved" driver.)

Hate to dump this unit just because of software issues.  (could get an old PIII and put Win2000 - (the last version of their drivers for it works is for that) - on it and use it as a print server on my network, but that I would have to think about seriously because of space constraints!)

Contact has been made with the manufacturer, but they are strangely mute on the subject! LOL (think they may send me a pitch to BUY THE HOT NEW ITEM!!)

---

### Post by oldsoundguy on 2008-05-29
bump

---

### Post by prshah on 2008-05-30
> **oldsoundguy said:**
> 
Tried to get Gutsy to see it to no avail. (no drivers in cups/foomatic/gutenprint) .. 

You need to get a PPD file for it. In general, if you can get a PPD file for any printer, you can set it up in cups. See if you can find a matching PPD from [http://openprinting.org/show_driver.cgi?driver=rastertokmXXXXdl](http://openprinting.org/show_driver.cgi?driver=rastertokmXXXXdl)

> It will not work in XP SP2 either! (

I hope that does not mean that the printer interface is broken/borked!

---

### Post by oldsoundguy on 2008-05-30
Have tried that, but this printer is QMS (minus either the Konika or Minlota logo and has no numerical designation).  I get the same results when I send a test page .. (either with XP or Ubuntu)  I get an LED flash that data is incoming, but nothing happens!

Still attempting to deal with the manufacturer.  They sent me instructions for doing a total printer reset, but I could not get into where they said the Administration screens were from the menu route they cited .. awaiting a second reply from them.

But thanks for the effort.  At least SOMEBODY answered and tried!

---

### Post by prshah on 2008-05-30
> **oldsoundguy said:**
> 
Still attempting to deal with the manufacturer.  They sent me instructions for doing a total printer reset, but I could not get into where they said the Administration screens were from the menu route they cited

Rather than wait for their reply, why not just [pluck the manual off the internet?]("http://www.google.co.in/search?q=QMS+Magicolor+2+CMYK+manual+pdf&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")

Besides, I find from the manual that PPDs _are_ available for this printer.> The QMS magicolor 2+ also supports the following host operating environments by
providing a QMS Advanced Level 2 PPD (PostScript Printer Description) file to use in
conjunction with the PostScript driver supplied by the operating system manufacturer:


The PPDs are for mac, but since cups itself is mac-inspired, I think it should work.

Good luck anyhow.

---

### Post by oldsoundguy on 2008-05-30
did the PDF of the manual last week.  ...
Just got a follow up eMail, saying that apparently the printer I have is NOT Postsript as originally advertised (because it was lacking the Administrator menu), it is raster so will not WORK in Linux.

They also sent me to a DIFFERENT driver source for XP.  Will give that a shot to see if I can, at least, get the darn thing to work on a Windows box.  I can always integrate it into my home network to see if Linux will print to it through Windows.  (it does on my other printers)

Thanks again for the help, anyway.

If nothing works, since I paid VIRTUALLY NOTHING for the printer, only some time is lost and some knowledge gained.

---

### Post by oldsoundguy on 2008-05-30
Final follow up:
Using a legacy driver, the printer is now totally functional on an XP machine, but because of the (raster) driver incompatibility, even attempting to network with a Linux machine yields nothing.
At least it does not wind up in the recycle bin!!
Color is not W.Y.S.I.W.Y.G., but that can be worked on! (and I did not expect it to be so on such an old unit!)

Thanks for the answers and support.

---

