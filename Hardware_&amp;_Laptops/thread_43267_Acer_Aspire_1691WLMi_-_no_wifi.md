---
title: "Acer Aspire 1691WLMi - no wifi"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by J2R on 2005-06-21
I recently bought an Acer Aspire 1691WLMi notebook and have installed Ubuntu 5.04 (Hoary) on it with general success. I've had no joy so far, though, in getting the internal IntelPro2200 wifi to work. It works absolutely fine in Windows XP, but in Ubuntu I get the message (in dmesg) that the 'Radio Frequency Kill Switch is On'. Pressing the led/switch on the front of the machine makes no difference - I've never been able to switch it on such that Ubuntu can use it. There is no option in the BIOS to control this, either. 

I've played around with installing ipw2200 1.0.0 (in place of the existing driver), as well as upgrading the firmware, trying acerhk, etc. but have drawn a complete blank.

Has anyone got this machine or v. similar and got the internal wifi working?

---

### Post by stonecrest on 2005-06-21
I'm pretty sure that you can use RFSwitch on the ipw2200. The homepage is here:
[http://rfswitch.sourceforge.net/](http://rfswitch.sourceforge.net/)

---

### Post by J2R on 2005-06-21
[QUOTE=stonecrest]I'm pretty sure that you can use RFSwitch on the ipw2200. The homepage is here:
[http://rfswitch.sourceforge.net/](http://rfswitch.sourceforge.net/)[/QUOTE]

I did what they suggest there for the 1690, using acerhk, and I get the message in dmesg

ipw2200: Unknown parameter 'led'

What have I missed?

---

