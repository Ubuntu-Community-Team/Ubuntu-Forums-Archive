---
title: "Graphic Card Drivers will not install (n00b here)"
date: 2009-04-05
forum: Hardware
---

### Post by Illuminise on 2009-04-05
Hey there everyone.

I just installed Ubuntu 8.10 (I have never used linux before) and nearly everything went awesome. So far, I have even managed to get the internet running :D

I have a problem though, when I go to System > Administration > Hardware Drivers I get ATI/AMD proprietary FGLRX graphics driver showing up. When I click on Activate it says its downloading and then about one second later it returns to the screen without any change. I rebooted the machine but it did not change anything.

Now, I am a complete noob at this, and have almost no idea what I am doing. I am just wondering if there are Step-By-Step instructions to fix this (perhaps through Terminal)?

I have looked on these  forums and around the net and tried everything but to no avail. Any help will be greatly appreciated.

Thanks.

---

### Post by Sam Lars on 2009-04-07
I would suggest installing envy-ng and trying that.

---

### Post by divague on 2009-04-07
Try this:

Open synaptic and install xorg-driver-fglrx then go to System > Administration > Hardware Drivers and activate the driver.

That worked for me.

---

