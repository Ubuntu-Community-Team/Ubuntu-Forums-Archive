---
title: "Problems installing Lexmark z35 printer/ benq scanner"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by weemikey on 2006-08-31
I have never been able to get my Lexmark z35 to print at all.
I'm using Ubuntu 6.06, and have the Lexmark3299-tweaked.ppd installed in /usr/share/ppd/linuxprinting.org-gs-builtin/Lexmark/Lexmark-3200-lxm3200
-tweaked.ppd and /usr/share/ppd/custom/Lexmark-z32-lxm3200-tweaked.ppd
Do I have to do anything with these files to get things to work? I have virtually NO experience with Linux/Ubuntu, but like what I have.

Also my scanner, a Benq, which did work prior to the latest release of Ubuntu, now refuses to work. the Xsane Image Scanner recognizes that I have a  webcam and the Benq (even gives me the model number) scanner, but when I click the button for the scanner I get an error message.
Please, please help me.
I will need not just Chapter and Verse, but probably Word and Letter also to go through the commands needed.  :confused:
Wee Mikey

---

### Post by DoctorMO on 2006-08-31
Lets try and get your printer working first, the scanner should be easy after that:

the ppd is a discription file for the driver, it isn't the driver. so are you using the guten-print driver of something else?

---

### Post by weemikey on 2006-08-31
Doctor Mo, where would I look to find out if I'm using a gutenprint driver (told you I'm a true newbie - at the age of 68)?

I've found, in /usr/share/ppd/gutenprint/5.0/en the following files:
   stp-lexmark-4076.5.0.ppd.gz
         ditto-z42.5.0.ppd.gz
         ditto-z43.5.0.ppd.gz
         ditto-z52.5.0.ppd.gz
         ditto-z53.5.0.ppd.gz

When installing the printer (System/Administration/Printing) and it asks me;
Install driver (with the lexmark-z3200-tweaked as the suggested driver), and I go to /usr/share/ppd/lexmark and highlight the lexmarkz3200.ppd file and <Open>, I get the <lexmarkz3200 driver already installed> message.
Very confused.:confused: 
Wee Mikey

---

### Post by weemikey on 2006-09-04
I've done it!!  Thanks to <black hole sun> at:

    [http://www.ubuntuforums.org/showthread.php?t=49714&highlight=installing+lexmark+printers](http://www.ubuntuforums.org/showthread.php?t=49714&highlight=installing+lexmark+printers)

and his script I've installed my Lexmark 'paperweight' Z35 and she works like a charm.

There were a couple of additions I had to make to the script, and if you go to the thread above I have mentioned them in my response.

---

