---
title: "[SOLVED] Install freezes at &amp;quot;booting Kernal&amp;quot;"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by Nicepen on 2005-12-22
My computer, Acer TravelMate 4650 with a Pentium M proc.

I have downloaded the X86 iso and burned it with ISOburner.  I thought I needed the I386 but that is only available through bittorrent.  I started that download and decided to post here and find out for sure before I waited a day and a half for that to finish.  

When I boot from the x86 disc I start the installation it gets to the point where it says "uncompressing linux... Ok, booting Kernal" then it does not go any further.  

I am very new to linux and have no idea what is happening.  Help is appreciated and I thank you in advance.  

Aaron.

---

### Post by yaddoshi on 2005-12-22
I am also a bit of a newbie, but I just had the exact same problem with a notebook that has a Pentium M processor and I believe the processor is the issue.  Here's a link to my thread on the subject: [http://ubuntuforums.org/showthread.php?t=105460](http://ubuntuforums.org/showthread.php?t=105460)

Try putting "linux noapic" (without the quotation marks) next to next to the Boot: prompt and I bet you'll get further.  If not try the other Boot: options listed on the above thread.

Good luck!

---

### Post by Nicepen on 2005-12-22
That did it, thank you very much.  And thank you for the relaxed response.

---

### Post by yaddoshi on 2005-12-23
Woot! :smile:

---

