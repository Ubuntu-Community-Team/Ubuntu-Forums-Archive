---
title: "RAM not recognized"
date: 2009-04-29
forum: Hardware
---

### Post by Atlantix on 2009-04-29
I bought two 256 MB PC133 RAM sticks to upgrade my Dell Inspiron 5000e vintage laptop - hoping to be able to install Ubuntu on it (800MHz P3, runs fine with WinXP Pro).
 
If I replaced both sticks, the laptop would attempt to start, then the hard would stop spinning, and starts again... and so on - I have to pull the power cord and the battery to stop it. 
 
If I put both original memory sticks back (2x64 MB) the laptop runs as expected. 
 
If I leave one original and one new RAM stick, I get the error message: Serial presence detect (SPD) unavailable - memory speed unknown. Makes sense, since the original RAM is 100MHz, the new one is 133MHz...
 
Googling around I found that I should be able to disable the memory check, but entering setup with F2 does not give me this option... or I can't find the option.
 
Your expert help is much appreciated,
Atlantix

---

### Post by Atlantix on 2009-04-30
Anyone?
 
Any ideas please?

---

### Post by HankB on 2009-04-30
> **Atlantix said:**
> Anyone?
 
Any ideas please?

Doesn't seem to be a Linux problem at all. You might have better luck at a forum devoted to Dell laptops. You might have a look at [http://forum.notebookreview.com/forumdisplay.php?f=4](http://forum.notebookreview.com/forumdisplay.php?f=4).

---

### Post by Atlantix on 2009-04-30
Sure, I know it's not a Linux issue; I just thought someone has seen it before and knows the answer.

---

### Post by Barry Carroll on 2009-04-30
Some things you might try would be:

* See if there is a BIOS update for your laptop from DELL.

Seems like your laptop can support 512MB according to the crucial memory checker.  Does the ram that you bought match the follows specs?

> # Module Size: 256MB
# Package: 144-pin SODIMM
# Feature: SDRAM, PC133
# Specs: SDRAM, PC133 • CL=2 • Non-parity • 133MHz • 3.3V • 32Meg x 64 • 

This might seem like a silly thing to recommend but you must be sure that you are putting them in right and that they are seated properly.  One of my friends had a laptop with badly seated ram and it had problems booting too.

---

### Post by Atlantix on 2009-04-30
Yes, I took the specs for the RAM from Crucial, then bought this:
 
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWNX:IT&item=110374089095](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWNX:IT&item=110374089095) 
 
Thank you,
Atlantix

---

### Post by Barry Carroll on 2009-04-30
Unfortunately it might down to your laptop being picky at the end of the day but maybe you can try a few things. Another scenario is that one or more of the sticks are bad although that's only happened to me once or twice in the past.

If you were going by the book you'd need to get PC100 but in my experience PC133 has usually worked in PC100 mode.

Have you tried placing each of the new sticks in each slot individually?  So stick one in slot 1, test, stick 1 in slot 2, test, stick 2 in slot one, test, stick 2 in slot 2, test.

---

### Post by Atlantix on 2009-04-30
Yes, tried all of that.
 
I have one other option - I have a Sony Vaio which also has 2x256MB or RAM, I will test them in the Sony.
 
But I don't know yet if they are the same type. Have to go home and see...
 
Atlantix

---

