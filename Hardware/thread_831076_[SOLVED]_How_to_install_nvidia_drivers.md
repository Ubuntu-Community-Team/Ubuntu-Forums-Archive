---
title: "[SOLVED] How to install nvidia drivers"
date: 2008-06-16
forum: Hardware
---

### Post by ramadan on 2008-06-16
am using Ubuntu 7.1 or at least am trying, my video card is nvidia geforce 8800 gt, the system didn't recognize my video card( detected it as vesa) so i downloaded the drivers from nvidia site, the problem is i cant install them,
so please how to install them i am really have no clue. every help is appreciated and thanks in advance:confused:

---

### Post by Nepherte on 2008-06-16
Does system > management > restricted hardware drivers list the nvidia package? That would be the easiest way to install.

---

### Post by ramadan on 2008-06-16
I tried the restricted drivers manager it told me there is no restricted driver, my problem is that the ubuntu didnt recognize the card( Gigabyte 
GV-NX88T512HP) i downloaded the drivers but( due to me) simply i cant install them so how to install them ( i dont know)

---

### Post by DJ_Peng on 2008-06-16
You may want to give [Envy Legacy]("http://albertomilone.com/nvidia_scripts1.html") a go at the drivers. It worked like a charm for me on Ubuntu 7.10. Just an FYI it's 7.10, not 7.1. It stands for 2007, 10th month (October), the general date Gutsy was released.

---

### Post by stchman on 2008-06-16
> **ramadan said:**
> am using Ubuntu 7.1 or at least am trying, my video card is nvidia geforce 8800 gt, the system didn't recognize my video card( detected it as vesa) so i downloaded the drivers from nvidia site, the problem is i cant install them,
so please how to install them i am really have no clue. every help is appreciated and thanks in advance:confused:

You are going to need Envy.  The nvidia-glx-new is only up to 100.xx for Gutsy.  For Hardy the nvidia-glx-new is up to 169.12 and that supports the 8800GT.

Download and install Envy 0.9.10 and select remove the nvidia driver (sounds like you tried to install and it did not work).  After that select manual install and there should be the 169.12 driver.  Select it and let it do it's thing and it will work.

You could also do a clean install of Hardy and the 8800GT will work awesome.

---

### Post by stchman on 2008-06-16
> **DJ_Peng said:**
> You may want to give [Envy Legacy]("http://albertomilone.com/nvidia_scripts1.html") a go at the drivers. It worked like a charm for me on Ubuntu 7.10. Just an FYI it's 7.10, not 7.1. It stands for 2007, 10th month (October), the general date Gutsy was released.

The envy legacy drivers are for older cards like GF2, GF3, GFMX. etc.  The 8800GT needs at least the 169.12 drivers.

---

### Post by ramadan on 2008-06-16
thanks alot guys, i did install envy tool, it is very handy and everything is  OK
thanks again
:lolflag
the advanced effects are amazing

---

### Post by DJ_Peng on 2008-06-17
> **stchman said:**
> The envy legacy drivers are for older cards like GF2, GF3, GFMX. etc.  The 8800GT needs at least the 169.12 drivers.
Actually the qualifier for Envy Legacy/NG is the version of Ubuntu being used, not the card being supported. The OP said he was on Gutsy, which is why I suggested Envy Legacy.

This has been a point of confusion since Alberto made the announcement of the dual versions of Envy, but a simple glance at the chart of that page will show the OS version as the basis of what version of Envy supports what. It's easy to misunderstand

---

