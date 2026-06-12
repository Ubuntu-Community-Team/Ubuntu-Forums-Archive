---
title: "Integrated Radeon graphics"
date: 2008-07-26
forum: Hardware
---

### Post by merrygoround on 2008-07-26
Hi, 

I have this motherboard: [http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2775](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2775)

It says it uses integrated 2100-based ATI graphics. I'm not sure what that means, and I can't really find a proprietary driver for it.  I've seen some similar questions on the forum, and one thats exactly the same as mine, but no answers. I thought, maybe some time has passed and there are now answers to this.

I should of done more research when I bought the motherboard. I have things running and it works fairly well. But it would be very nice if I could get a more appropriate driver for the integrated graphics.  

Any thoughts?

Thanks for reading.

---

### Post by argosreality on 2008-07-26
The 2100/740G chipset is just a die-shrunk 690G chipset so their standard unified driver should work without any issues on it. However it looks like its very new so the drivers might not have been updated with the the vender strings yet

---

### Post by merrygoround on 2008-07-26
If ATI does not have a proprietary driver for the 2100. How could I either find something that would work on it?

Or, perhaps how much knowledge does it take to write a driver? Perhaps I could find someone that could do it?

---

### Post by argosreality on 2008-07-27
Try installing EnvyNG through Synaptic. If it properly detects your chipset it'll auto install the driver for you. Otherwise, you'll just have to wait till its added into the July driver from ATI

---

### Post by markbuntu on 2008-07-27
I saw on another post about this 2100 that envy does not recognize it.

---

### Post by t_unix on 2009-01-11
Any updated driver info on getting this chipset to run on 8.04?

ATI prop'y DEBs(current/past 3) crash X, amdcccle says no driver to be found, fglrx refuses to load or activate, Envy only finds the one that won't load, sudo dpkg-reconfigure xserver-xorg got my keyboard working even though it didn't need fixing. Googled various combinations of 8.04 740g radeon +2100 ubuntu and tried the few ideas to no avail.

This is a flashback to 2007 of wasting days(weeks?) trying to get a ralink wireless driver to work, then to work w/ WPA/TKIP, and finally, threw in the towel b/c it couldn't handle static IP. Sad thing is, PuppyLinux did it all just fine the first time. ???????

---

