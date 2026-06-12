---
title: "A little help, Intel vs. i810..."
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by spotdog14 on 2008-01-09
Ok, so i have been rocking Gusty since the beta, and its to much work to go back to Edgy now. Everything worked in Edgy, hibernate, standby graphics, etc.

First i updated for Edgy and it kept the i810 driver, then i updated the system and restarted and the black screen came up, and i had to switch over to the intel driver. Thats fine, i did a fresh install of gusty a few weeks later and it installed intel by default. 

Under i810 the monitor out options all worked to hook up an external monitor, but under intel they dont. Anyone have any ideas on if we can now swtich back to i810?

---

### Post by ceronman on 2008-01-16
I have a Dell Latitude D620. I'm with Ubuntu 7.10 and I have experienced some problems with the intel driver so I decided to chage it back to i810.

When I'm using the intel driver and close the lid, the screen gets off for a second and the gets on again. That's annoying because there is some light leak.

I'm using the i810 driver and it seems that everything is working fine now. I don't know exactly what is the difference between these two drivers, but I have seen "intel" marked as experimental.

---

### Post by dannyboy79 on 2008-01-17
i have a question for you guys. my friend has this same onboard card in his desktop. he notices that when he's playing music sometimes and his SkyRocket screensaver starts up, the screensaver is blotchy and isn't running optimally. I checked his xorg.conf and he's running the intel driver. I also noticed that he doesn't have a "module" section. should he have one and which ones should he have in there? 

He's driving an HP 19" Widescreen that has an optimal res of 1440x900. His machine has 512mb of RAM so you would think that that would be enough to process music and display a screensaver so I am thinking it's something with xorg.conf optimization. 

Any suggestions? Yes, I have already made sure the vert and horiz sync rates are correct.

---

