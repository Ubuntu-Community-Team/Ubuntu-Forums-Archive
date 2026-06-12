---
title: "Fresh Feisty Install, USB devices randomly fail"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by skyhopper88 on 2007-05-25
Every so often, my USB mouse stops responding, and the light goes off. My external drive nor mp3 player will mount at this time. Replugging devices in does nothing. I normally use a usb keyboard, but right now I'm using a ps/2 one and it responds and I can navigate with it. My entire system froze up once, but that hadn't happened since. I kinda solved the problem by using a kernal without USB_suspend from this topic.
[http://ubuntuforums.org/showthread.php?t=432130](http://ubuntuforums.org/showthread.php?t=432130)
But went back since I couldn't use restricted video drivers. I've been trying to fix it by adding options in my menu.lst from this topic
[http://ubuntuforums.org/showthread.php?t=406893&page=1](http://ubuntuforums.org/showthread.php?t=406893&page=1)

But none worked. Any ideas?

---

### Post by skyhopper88 on 2007-05-26
Oops, forgot my specs. Acer Aspire T160 (desktop) 1.5 gigs 3200 DDR Ram, Athlon 3400+ Venice SC, Ubuntu on a 60 gig hd.

---

### Post by skyhopper88 on 2007-06-06
I was hoping the 2.6.20-16 kernal would behave itself, but no luck. Is there anything else I can attempt?

---

### Post by teachop on 2007-06-06
I could use help on this too.  It happens on my Acer Aspire 3100 laptop.  I thought I had it fixed when I saw some Network Manager log messages from the same time as a USB lockup, and got rid of NM (which is not working for me anyway).  There were no USB crashes for 6 days.  But alas, it then locked up again.

---

### Post by skyhopper88 on 2007-06-07
Six days would be unheard of for me, most I've had is 6-8 hours.

---

### Post by skyhopper88 on 2007-06-09
Disabled USB 2.0 and used 1.1 instead, still froze. Didn't disable it at boot though, not sure if that makes a difference.

---

