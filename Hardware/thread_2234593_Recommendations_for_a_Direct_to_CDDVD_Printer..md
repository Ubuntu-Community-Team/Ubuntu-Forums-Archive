---
title: "Recommendations for a Direct to CD/DVD Printer."
date: 2014-07-15
forum: Hardware
---

### Post by tellah on 2014-07-15
Hi Everyone.

A little back hsitory...
I had a HP Photosmart D5160 that I bought for printing 4x6 photos and CD/DVDs.  The printer has developed and error and refuses to do anything but blink at me now, so I am forced to replace it.  I bought a Canon PIXMA MG7120 which I kind of got working but cannot print on CD/DVDs with it.  Regular paper and 4"x6" photos print fine but the CD/DVD printing alignment is screwwd up.  I use gLabels 3.0.x and it start the printing half way down the CD.  I can move the image farther down but not up to the top of the CD.

My question...
1)  Has anyone had success printing direct to a CD using gLabels and this printer (Canon PIXMA MG7120)?
2)  Has anyone successfully printed to a CD using any software and this printer?
-or-
3)  Can anybody recommend a direct-to-CD printer that works.  (Preferably with gLabels and less than $250.)
     Other models I have looked at:
[LIST]
[*]Canon PIXMA iP7220 or iP8720 
[*]Canon PIXMA MG5420 or MG6320 (I assume I will encounter the same problem.) 
[*]Canon PIXMA PRO-100 (A little expensive but does do 11"x17" so maybe I could be convinced.) 
[*]Epson XP-610, XP-810, XP-850 ot XP-950 
[*]Epson Artisan 1430 (Again, a little expensive but does do 11"x17" so maybe I could be convinced.) 
[/LIST]
I know there are dedicated CD/DVD printers, but they seem generally very expensive for a home environment considering they only have one function.

I look forward to everyone's suggestions.

Thanks.
-Brian

---

### Post by Mark Phelps on 2014-07-15
> 2) Has anyone successfully printed to a CD using any software and this printer?

Well ... yes and no.  Let me explain.

I used to have an Epson 200 cd/dvd printer and I printed to it in Linux using Gutenprint, after I installed the Epson printer using CUPS.  That installation used a CUPS driver that gave me extra settings for the Epson printer such that I could define things like the CD hub size and set small offsets to perfectly align the cd/dvd disks for label printing.

I didn't use glabels because I have used an excellent Windows app that produced the labels.  I saved those lablels as .jpg files and printed them in Linux.  Later, I learned how to use Gimp and .xcf files to recreate the same lables, and Gutenprint provided the option to print to the Epson from Gimp.

Now, I have an Epson Artisan 730 CD/DVD printer -- and have repeated much the same process -- installing it using CUPS to get the more refined settings made available by the CUPS driver. 

The Epson Artisan 730 is much the same printer as the 1430 but it can't print to oversized paper -- but for CD/DVD labels, is the same printer.

---

### Post by jmail5242 on 2014-08-11
Thanks for the reply Mark.  I got caught up with a few other things and wasn't able to get back to the printer issue right away.

I sort of got the printer working with CDs/DVDs.  I got it working with gLabels but I had to set the paper size to 8.5"x11" and place the CD "area" against the left border, half way down the page.  This yields acceptable results although about 1/8" on the left size of the CD is always blank.

Thanks for your help.
-Brian

---

### Post by pdc on 2014-08-11
I was wondering if you were using the drivers that Canon supply Brian: if you click here [http://localhost:631/printers/](http://localhost:631/printers/) it opens the CUPS page and in the right-hand column; I wonder if the printer driver is gutenprint;

If so, you could install the drivers Canon supply; it comes from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100551202.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100551202.html) and comes down as [COLOR="#008000"]cnijfilter-mg7100series-4.00-1-deb.tar.gz
[/COLOR]
if saved to Downloads directory, install commands are:

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mg7100series-4.00-1-deb.tar.gz
cd cnijfilter-mg7100series-4.00-1-deb
./install.sh[/COLOR]

............that should create Canon MG7100 series 4.0 install ..........and needs to be identified from the gutenprint so you can see which is which ........

---

