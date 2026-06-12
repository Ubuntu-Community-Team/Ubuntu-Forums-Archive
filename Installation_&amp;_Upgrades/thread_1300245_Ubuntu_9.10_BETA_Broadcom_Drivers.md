---
title: "Ubuntu 9.10 BETA Broadcom Drivers"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by NNNDaddy on 2009-10-24
Hi,

Today I wanted to put Ubuntu 9.10 on my laptop. It runs broadcom wifi drivers. When running Live CD, it listed the broadcom drivers as proprietary drivers that could be enabled, so I went along with the install.

After the install, I didn't have wifi and the drivers weren't there. It says "there are no proprietary drivers in use on this system" and there is nothing to enable.

Will this be fixed when the final release is available?

Thanks!

Ken

---

### Post by vipseixas on 2009-10-26
The proprietary drivers do not come with the default installation, you will have to establish another internet connection (via ethernet cable for instance) and them the drivers wizard will download and install the proprietary wi-fi driver.

---

### Post by Cylon on 2009-10-28
That's really ridiculous. Isn't there a deb package that can be downloaded? In my case, my computer is upstairs and router downstairs. That's why I have wireless in the first place. It seems kind of silly that the proprietary drivers show up in the live cd, even without a connection, then after install it's a completely different world.

I'm having the same issue and would really be interested in another way around this than lugging my machine downstairs just to install a driver.

---

### Post by Devi 710 on 2009-10-28
I am having the same problem on my Dell Mini 10v that I got today.

I connected to my router via Ethernet cable, and there was 2 choices for drivers, open source and proprietary (they showed up when running the OS live, but not after the install, same like OP). I've tried both with no luck.

Is there something I need to do to startup the wireless card after installing the drivers?? The network app on the top panel doesn't even have wireless networks as an option.

I would appreciate any advice if someone gets their Broadcom Wifi card to work.

Thanks,

Devi

---

### Post by Rifester on 2009-10-28
Go into Synaptic and find bcmwl-kernel-source and install it.   This will give you the driver.   If you don't see it in synaptic you can install it from the live cd of your former version of Ubuntu (which is what I think I had to do).  Hope this helps.

Mark

---

### Post by Devi 710 on 2009-10-29
Thank you so much!

After installing bcmwl-kernel-source from Synaptic my wireless is working :) Thanks for the help. I never would have figured that out. 

I'll install the final release of 9.10 tomorrow when it comes out. It will be interesting to see if I'll need that fix in the final release.

Devi

---

### Post by niite on 2009-10-29
Yeah I had the same problem.. it is kind of ridiculous to have them show up in the live cd, and then run the install, and it doesn't install them lol.  It did it for 9.04 install.  I just rolled back to 9.04 and did an upgrade vs clean install and had no problem then.

---

### Post by Xiled on 2009-10-30
is there a way to fix this driver issue without the using synaptic?

thanks

---

### Post by Devi 710 on 2009-10-30
I did a fresh install with the final 9.10 release, and once I connected to the Internet it found the hardware drivers needed. I didn't have to use synaptic. I installed the proprietary one and wifi works just fine now.

---

