---
title: "HP LaserJet 4 Plus not working (did work with Hoary)"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by DFreeze on 2005-11-14
Does anyone of you have such a printer going with Breezy? Hoary did a perfect job with it, but Breezy does not. I've tried all four options under the printer-driver section, but no luck...

Any suggestions?

---

### Post by DFreeze on 2005-11-22
Sorry to bump myself up like this, but I can't find help elsewhere. Nobody here know how to get the ol' dynosaur working again?

---

### Post by ed_d on 2005-11-22
Have one working on my breezy. Its on the network though here at work. I had no issues at all setting it up.

---

### Post by ubuntolog on 2005-11-23
I have HP LaserJet 2100 working fine on my breezy
Start gnome-cups-manager and try to use driver ljet4.

---

### Post by DFreeze on 2005-12-04
I found a cure to the problem, so I'll post it here for anyone else having a similar problem. 

The thing was that Ubuntu didn't 'sense' a printer on my LPT port. So whatever driver I used, didn't matter, because there was no recognised target to send it to. Maybe it's a bug that Ubuntu doesn't give an error like: printing failed, no printer found. It just fired up the printer icon, and let me wait indefinately. 

After recognising that Ubuntu didn't see my LaserJet, I set the option 'send to LPT1'. So actually telling Ubuntu: it doesn't matter what printer you see or don't see, that's the port you have to send the instructions to. Then the printer started working...

Should I file a bug-report? And if so, how do I do that?

---

### Post by madmaxx on 2006-01-14
Hello everbody

@DFreeze: Thanks for the tip! Assigning it to lpt1 did work. :D 

Now, the only interesting problem remaining is that I get an empty sheet of paper
at the end of each print job. Does anyboy have an idea what that could be?
(Happens with both the ljet4 and hijs driver...)

TIA,
madmaxx

---

### Post by _simon_ on 2006-01-14
how do you assign it to LPT1?

---

### Post by DFreeze on 2006-01-16
I'm not sure which menu it is, since I'm not on my Ubuntu-machine right now. But there's an option on the lower-half of the printer settings, a sort of pull-down menu. There is a whole list of options, one of which is the LPT1 port. 

Hope this helps!

---

### Post by lsiden on 2006-02-12
I have been having a similar problem, but my HP Laserjet 4-Plus is connected through my local network (tcp/ip).  I tried to send a test page with three different drivers: Postscript, hpijs, and ljet4, but not worked satisfactorily.  One causes the printer to spew page after page of garbage, another causes it to complain about insufficient memory on the printer display, and yet another causes the printer to ask for A4 paper even though I told both the printer and the printer config dialog to use Letter.

BTW - What is LPT1?

---

### Post by CobraKai87 on 2007-09-01
I have the same problem, though mine is connected through LPT1:.  I have tried all of the drivers, including LJ4, 4 Plus and 4 Plus v2031(?).  I either get mem overflows, garbage, or load A4.  I also have the 500 sheet bottom tray.


:confused:  :(
Chris

---

