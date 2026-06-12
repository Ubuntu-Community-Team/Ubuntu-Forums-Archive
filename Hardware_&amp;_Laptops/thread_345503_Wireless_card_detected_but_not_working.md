---
title: "Wireless card detected but not working"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by bprof on 2007-01-24
I have installed Ubuntu on my Dell E1405 laptop, it has an Intel PRO/Wireless 3945ABG. In Ubuntu device manager I'm able to see the card there with its name and other things. Also in the System-->Administration-->Networking I'm able to configure the wireless settings.

But still I don't have a connection, when I ran iwconfig it showed three cards

eth0 nothing there

eth1 with ESSID name but no IP or anything.

sit0 no wireless connection

There is nothing called ath0

Could you please help me figure out what is going wrong here? And how can I make use of Ubuntu device manager recognizing the card to make that card work?

Thanks,

---

### Post by Yerknutz on 2007-01-24
Most likely you need to install the "linux-restricted-modules" for your kernel.  At least that is how I got my wireless card to activate in Edgy.  Be warned though, that package contains nvidia-kernel-common which basically hoses my newer video driver and I am stuck without 3d acceleration.  I'm still trying to get both working correctly, but for the time being I am stuck with either no wireless and kick *** video or sub standard video and working wireless.

---

### Post by bprof on 2007-01-24
Thank you for your response Yerknutz. I have one more question: Did you try to install it using the steps on [http://ipw3945.sourceforge.net/?](http://ipw3945.sourceforge.net/?) Or you used another way?

Thank you,

---

