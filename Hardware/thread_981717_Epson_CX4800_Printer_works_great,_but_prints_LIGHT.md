---
title: "Epson CX4800 Printer works great, but prints LIGHT."
date: 2008-11-14
forum: Hardware
---

### Post by murderslastcrow on 2008-11-14
K, I've looked all over the internet and these forums and still haven't found a solution for this issue.

I'm running 8.10 Ubuntu on a very speedy machine, and installed the printer manually. This happened when I wanted to print a page in Firefox and it asked me to set up a printer- I chose the driver for this exact printer and it installed without a hitch.

However, whenever I print something off, the ink is very light on the page, making it appear that about half of the ink required is there. However, when we print the very same file from my Win-Vista laptop, it prints out with the perfect clarity. No need to even restart the printer.

I did find a help post somewhere that changed the resolution to a different DPI, but of all those options none fixed the issue.

^w^ Could someone please kindly assist me?

---

### Post by newburghmark on 2009-01-06
Try the following:
0. Click Main Menu on Deskbar
1. Click System
2. Click Administration
3.  Click Printing
4. Click the name of the printer at at issue
5. Click Printer Options
6. Click Printout Mode
Change mode to a higher resolution, such as move from everyday printing to High quality.  This might not perfectly resolve the issue.  I think that my HP 1341 might be printing lighter with Linux than it was with Windows, but I can't be sure because I no longer dual boot.  I am Ubuntu only.

---

### Post by newburghmark on 2009-01-06
Better answer than I gave an hour or so ago.

I am sure that I have the problem now.  Your DPI is set too low.

This I am sure will solve your problem.  
0. Click Main Menu on Deskbar
1. Click System
2. Click Administration
3. Click Printing
4. Click the name of the printer at at issue
5. Click Printer Options
6. Click Printout Mode
7.  Resolution, quality, ink type, media type.  Raise the setting to a higher number.  The print will be both darker and sharper.

Remember, most of the drivers that we use are not supplied by the manufacturers, they are reverse engineered by other users.  The reverse engineer might have set it lower either to be on the safe side or because he wrote the driver for an earlier model printer with more limited capabilities and when the driver worked with a newer printer, people just started using it without rewriting it.

---

### Post by GiveLove on 2009-03-17
Hello, 

I'd like to add to this thread, as it is the only one I could find that had the same problem as me, although with a different printer. 

I use an HP LaserJet 1100 that's connected to a Zonet ZPS3603 wired ethernet print server. Ever since Ubuntu 8.04 I've noticed that the printing is really light. I'm on 8.10 now, and same problem. I did not have this problem with Ubuntu 6.10, 7.04, and Fedora 5 and 6. And this printer currently also prints normally from Windows XP.


Generally the kind of stuff I print is text from web sites on Firefox, and documents from OpenOffice. In each case, it's as if the printer is trying to print the text in grayscale, rather than black and white. And even more than that, it's like it's printing a draft copy where it does not use enough toner to fill out the text characters. 

With the default printer settings, which does set it to the max DPI of 600. If you print a web page, you can barely read the text. I've been able to make it a little better by increasing the quality type, REt setting, toner density, and Halftoning Algorithm to maximum. But it is still not correct. This laser printer normally prints clean, crisp, and easy to read text. 

What's changed since 7.04 to cause this problem?
And is there a fix?
I hope somebody has answer. 
Thank you. :)

---

### Post by Merovius on 2009-03-17
I had the same thing with my epson multifunction I just bought. Turned out that when it auto installed, Ubuntu used a compatible driver, but, not the right driver. When I looked at the driver I realized this and set the driver manually. Boom, printed perfectly. The driver I used was a Guttenprint driver I believe.

I would manually set the driver. Good Luck.

---

### Post by GiveLove on 2009-10-20
Hello Merovius, :)

You came to the same conclusion that I did just this last week! Bravo! Thank you for posting. I only wish I'd had remembered to check this thread a long time ago. 

So while I cannot verify for sure that this is the answer, as my HP LaserJet 1100 just recently died and I opted to replace it. But my understanding is that the recommended driver that Ubuntu 9.04 lists after entering the make and model is the hpijs driver that HP makes. (Now called HPLIP)

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1100.html#note11]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1100.html#note11")

When I checked to see if my LaserJet 1100 printer is supported in the above direct link, this driver, under the field "Recommended?", says "No". Now the interesting thing is, that changing the driver to the guttenprint or foomatic had the same results. The only other idea that I picked up from somewhere was that I tell Ubuntu that I am installing a LaserJet 4/4L. As that is a basic postscript driver that just works. And if I recall correctly, in Fedora 5 and 6, and older versions of Ubuntu below 8.04, this is the driver that was recommended and worked correctly. But it's too late now for me to test this hypothesis. 

One step forward, two steps back. Bleh!

---

