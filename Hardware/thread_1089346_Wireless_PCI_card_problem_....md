---
title: "Wireless PCI card problem ..."
date: 2009-03-07
forum: Hardware
---

### Post by Mashiimaro on 2009-03-07
I just installed ubuntu 8.10 on a laptop (Toshiba Satellite) - everything else seems to be working fine (graphic card, sound, keyboard... ) but one thing that I am having trouble with is the wireless PCI card that I put in there
I've followed the guide about ndiswrapper.. I've installed everything, and it even says the driver is installed, device detected.. but internet just wouldn't work .. :(
Is there something that I am doing wrong?

by the way, the notebook adapter I am using is the Linksys WPC54G Version 1.2.. 
I would appreciate any help that could be given !

---

### Post by tommcd on 2009-03-07
Your card uses the Broadcom b43 driver. Did you try using system > administration > hardware drivers to see if you can enable the b43 driver?
Also see this thread:
[http://ubuntuforums.org/showthread.php?t=186538](http://ubuntuforums.org/showthread.php?t=186538)
Note: If you read farther down in the thread, you will see that the ndiswrpapper stuff is unnecessary. Just follow the stuff about fwcutter and bcm43xx.

And welcome to the Ubuntu forums!

---

### Post by Mashiimaro on 2009-03-08
oh my god it works now ! 
Thank you SO much for the link!
I had been miserable because I had been googling and searching for hours last night but still couldn't find any solution to the problem .. 
the internet works now !  yay ! :D

---

### Post by tommcd on 2009-03-08
> **Mashiimaro said:**
> oh my god it works now ! 
Thank you SO much for the link!
I had been miserable because I had been googling and searching for hours last night but still couldn't find any solution to the problem .. 
the internet works now !  yay ! :D
Glad you got it working!
Just curious, but could you describe what you did to get it working? Did you follow the link I gave you? Or use system > administration > hardware drivers? The info may help someone else with the same problem.

---

