---
title: "fn + Fx keys"
date: 2012-12-29
forum: Hardware
---

### Post by carega on 2012-12-29
Hi there.

I have a TOSHIBA Satellite C845 and some of the fn + Fx keys (ie fn + F1, fn +F2 and so on) are not working. I request help on this.

Keys Fn + F6/F7/F8/F9/F10/F11 are working fine. 

The problem is with the keys for the brightness functions, screen output and touchpad lock. Can anyone help me with this? Please...

---

### Post by gnush on 2012-12-29
Hmm. Are you sure it's not a software problem? Many keyboards and mice with extra buttons tend not to work because there isn't any driver software available for Linux.

Other than that, I have no idea. You could fire up either xev or showkey and see if the buttons are registered at all.

---

### Post by carega on 2012-12-29
Nay, I don't think it's a software problem. They actually worked fine but then stopped working around a month ago, after I performed an update.

I don't know how xev works but showkey shows all the buttons I said were working plus Fn + F2.

---

### Post by ahallubuntu on 2012-12-29
Problems with the brightness keys (Fn or otherwise) in Linux are extremely common.  There's usually an easy fix involving adding a line to your Grub configuration file.  I don't know the exact fix for your Toshiba, but it should be very easy to find a solution by searching this forum (or just googling) for "ubuntu brightness keys" or "ubuntu toshiba brightness keys."

I'm not sure how you fix the touchpad enable/disable key, but I'd get the brightness keys working first.  If you're lucky, that will fix the others as well.

---

### Post by carega on 2012-12-29
already tried that. there are solutions for toshiba laptops with no control over brightness which is not the case (i can control it using brightness adjustment). i googled my laptop model but couldn't find a solution...

---

### Post by carega on 2012-12-30
Recently tried this solution and it didn't work:

[http://ubuntuforums.org/showpost.php?p=11966072&postcount=2](http://ubuntuforums.org/showpost.php?p=11966072&postcount=2)

Can anyone help me?

---

### Post by ahallubuntu on 2012-12-30
Did you change the default setting in the BIOS Setup so you need to hold down Fn?  It seems these laptops (like some Dells) now default to NOT needing to hold down Fn.  In other words, just hold down the function key without Fn.

You can change it back to needing Fn with a change in BIOS Setup:

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/bulletinDetail.jsp?soid=3431945&pf=true](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/bulletinDetail.jsp?soid=3431945&pf=true)

---

### Post by carega on 2013-01-02
> **ahallubuntu said:**
> Did you change the default setting in the BIOS Setup so you need to hold down Fn?  It seems these laptops (like some Dells) now default to NOT needing to hold down Fn.  In other words, just hold down the function key without Fn.

You can change it back to needing Fn with a change in BIOS Setup:

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/bulletinDetail.jsp?soid=3431945&pf=true](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/bulletinDetail.jsp?soid=3431945&pf=true)
Yes, I did that as well. Went into BIOS and changed the setup to needing to hold down Fn. The thing is some Fn + Fx functions do work (volume control and playback) and resetting the BIOS didn't change anything, even the keys that worked are behaving the same way.

Recently though it seems the solution I tried earlier now allows me to lock/unlock my touchpad. But there is no notification or anything showing that the touchpad is locked...

---

