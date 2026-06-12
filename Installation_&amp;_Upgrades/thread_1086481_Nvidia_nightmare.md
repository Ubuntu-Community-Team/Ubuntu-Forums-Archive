---
title: "Nvidia nightmare"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by triplemaya on 2009-03-04
I installed an nvidia graphics card to get better performance. ( This took about 8 hours with endless restarts with different drivers but with the help of envy I finally got the display working with the correct resolution! ) 
Unfortunately there is something hopelessly wrong with all of the versions of the driver, I can only have a few windows open, and an extra window comes up blank and unresponsive.
So, I remove the card and go back to the old xorg.conf file I carefully saved. No good. I cannot get my old setup back, there is no way to set the screen resolution to the old level. I have work to do, and I have burned up a huge amount of time on this problem and if any one can tell me a quick and simple way to get my pc working properly again I would be grateful. Failing this I am planning a reinstall of the operating system this evening! In some ways linux is so like the early days of windows!
Thanks in advance.

---

### Post by TenPlus1 on 2009-03-04
Re-install Ubuntu again but this time make 2 partitions:

30gb to /
rest to /home

This way if anything goes wrong in future your files are safely tucked away in /home while the / partition can be reformatted and re-installed...

Also, what kind of nvidia gfx card do you have, if you tell us the model maybe their is an easy way to install the drivers...

---

### Post by Sef on 2009-03-04
what graphic cards are you using?

---

### Post by triplemaya on 2009-03-04
Thanks, the partitioning is already done, I've been bitten before! But I only gave 10 gb to /, is that a problem?

The card is an Asus 7300, specifically
 Vga En7300le/td/128mb Pcie Dvi Gf7300le

It would be great to get it working right. At present I had to disable the screen saver as it locks up the pc which I have to restart by pulling the plug!

---

### Post by triplemaya on 2009-03-04
BTW I've tried all the drivers which are compatible, 177, 173, 96 and I'm now on 180.

---

### Post by triplemaya on 2009-03-04
This has been solved.

I switched the xorg.conf file for an older one, and everything started working perfectly. The toys went away, so I had the ordinary application switcher instead of the newer static application switcher, and the older workspace switcher. Suspicious I changed the xorg.conf back again, still working perfectly!!

---

