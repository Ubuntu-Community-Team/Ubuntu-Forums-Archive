---
title: "scanner support for HP all-in-one multifunction devices"
date: 2009-04-20
forum: Hardware
---

### Post by bob12564 on 2009-04-20
My Canon MP540 multifunction unit has developed the (in)famous grinding noise problem and I'm thinking of replacing it. Too bad because the Canon works very well with Intrepid and it worked out of the box.  Great printer and scanner support.

HP seems to have the best printer support but I can't find anything about how compatible the HP all-in-ones are with SANE and Ubuntu 8.10.  I need to use it as a scanner as well as a printer.

I'm looking for an HP all-in-one (print/fax/scan/fax) that will work out of the box with Intrepid, both as a printer and as a scanner.  Anyone know where I can find a list of current models that work?

Thanks!

---

### Post by ajgreeny on 2009-04-20
I know that several including the Deskjet F2180 work well, as I have that model.  The hplip and its toolbox software is just brilliant for it, and controls it at least as well as in windows if not better.  Also I know that the 6180 and 4180 ar e good, but are now older models and nay not even be available.

Two sites:-
[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp)
[http://www.ubuntuhcl.org/browse/search](http://www.ubuntuhcl.org/browse/search)

---

### Post by greenfrog on 2009-04-20
The Deskjet F2210 works great.

---

### Post by bob12564 on 2009-04-20
Just so I understand this, does the HPLIP driver also control the scanner or just print functions?  That's where I'm getting confused.  I'm under the impression that scanning is controlled by SANE and I don't see too many HP all-in-ones listed as supported by SANE.

---

### Post by ajgreeny on 2009-04-20
You are correct, hplip is printer control only, however, sane seems to work vert well with many hp scanners and all-in-ones, including those mentioned above.

---

### Post by bob12564 on 2009-04-20
Thanks for clarifying.  

The HP models mentioned in this thread seem to be discontinued.  I looked at the lists on the two websites mentioned and most of those are also obsolete.  There's a 6500 series that just came out but it's not in the HPLIP collection yet.  There's an 8000 Pro series that also seems new.  And there's a 4680 that has been out for a while but has bad reviews and it's not on the SANE list.

I wish someone (like Canon) would come up with a fix for my Canon MP540!  It would be so much easier.

---

### Post by nah40 on 2009-04-20
I have a 4680 and it works just fine, print, fax, scan, no problems with hplip 2.8.10

---

### Post by Gemnoc on 2009-04-22
I've got a C7280 wireless All-in-One with top automatic feeder. The HPLIP Device Manager brings up a windows with multiple action choices, including Scan. It brings up the XSane scanning program, and it works well. I like this combination better than the huge and bloated software suite you have to install on Windows. But one thing I'm unhappy with is that there is no real automatic multipage scanning. I have to press the OK button on the machine between each page. Which is rather tedious when there are 24 pages to scan.

Borderless photo printing used to work well with HPLIP driver 2.8.7. Although I had a really hard time finding the right app and settings (I use GNOME Photo Printer). I recently upgraded HPLIP to the latest 3.9.2 driver, and now I can't print borderless anymore. I may revert to the old driver when I have time to take care of this.

---

### Post by StuartN on 2009-04-22
I have an HP M1120n MFP (a network laserprinter all-in-one). I had to get the latest hplip, but it installed without any hitches. It prints and scans faultlessly over the network.

My only gripe is that hplip seems to take over cups, so non-HP printers can be a pain once hplip is installed.

---

### Post by bob12564 on 2009-04-23
Thanks for all the suggestions.  I actually found the HP F2210 and it appears to be a custom model only sold by WalMart.  The reviews are overwhelmingly good and it costs less than $30.  That might be my choice.  It's a basic multifunction but it has many features and it seems to be perfect for home use.  It seems to be fully compatible with Linux and Windows and should work "out of the box" in Intrepid/8.10.  

The Canon cost me almost $200 and the grinding noise problem is making it unusable even though it's a decent machine otherwise.  It looks like the design defect was on a few of the MP models and Canon opted to reduce the prices to get rid of them rather than trying to fix them.  At least if the F2210 breaks I won't shed too many tears.

The WalMart website says that it might be hard to find in stores but there's one store 20 minutes away that is supposed to stock them.  I may take a look at it this weekend and decide.

I'm a Windows refuge and I've been learning to appreciate Ubuntu Linux over the past year.  One problem is the lack of hardware support by manufacturers and I think that causes many people to stay with Windows.  Buying a multifunction printer is a good example of the difficulty because the printer drivers are separate from the scanner drivers and one may work and the other may not.

If I can't find the F2210 I'll look for a similar HP machine and have some confidence that everything will work.  Thanks for all the suggestions and for clarifying the technical details.

---

