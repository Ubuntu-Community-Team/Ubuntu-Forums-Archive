---
title: "Battery calibration tool?"
date: 2011-11-02
forum: Hardware
---

### Post by BazookaAce on 2011-11-02
Hi, 

I'm currently dual-booting Win7 and Ubuntu 11.10 but i mostly use Ubuntu at the moment. The one major problem i got is the battery life. I get about 2 hours of battery in Windows, but i get around 20-30 minutes in Ubuntu. Why? 

And is it possible to use a calibration tool for calibrating the battery? If you're using Android the calibration method there is to just delete the file "batterystats.bin" and you're good to go. Does Ubuntu/Linux have a similar file?

---

### Post by 2F4U on 2011-11-02
Batteries are vendor specific, so depending on your computer vendor, you may find something approprieate. For example, for IBM ThinkPads, there is a custom tool available. However, it doesn't really matter from what OS you do the calibration since the battery doesn't know which OS you are currently using. So, if there is an appropriate tool available for Windows, you can use that.
  Possible reasons why you get less battery life under Linux are
- kernel since 2.6.38 have a power management bug (see Phoronix)
- there is something running in the background that prevents the processor from getting into sleep mode

---

### Post by BazookaAce on 2011-11-02
Thanks for the reply. I'm using the new kernel (3.0) and nothing is running in the background. It goes to sleep without any problems. 

But if i unplug it now it will say that i have 100% battery left. 30 seconds after i'll get the "low battery" notification which will state that i have around 20% battery left. Again after 30 seconds it'll say i have 70% left and so it goes on and on until it say 0% and my computer shuts down without any warning. 

I remember this also happened when i used Ubuntu on a different computer a couple of years ago. It also ruined the battery and it only lasted for 15 minutes in Win7 after uninstalling Ubuntu. I don't want that to happen again!

---

### Post by BazookaAce on 2011-11-02
I suspect that it's something very wrong with the "battery-meter" in Ubuntu. It really can't be anything else? Like i said, it works just fine in Windows but not in Ubuntu, and the low battery notifications and the battery percentage is running wild. So it's not the battery, but the software. 

What's your thoughts on this?

---

### Post by BazookaAce on 2011-11-03
Well **** me. I just got the "battery capacity very low" message at boot up. **** this, i'm going back to Windows. This is the second battery Ubuntu messes up. Get it fixed and i'll think about coming back.

---

