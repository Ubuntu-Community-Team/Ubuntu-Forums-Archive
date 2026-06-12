---
title: "video card recommendations"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by SpottedOwl on 2007-04-03
Greetings all,

I hope this is a valid (and not overly popular) question for here:

I have a Dell desktop with ubuntu dapper drake -- not the best, but okay.
I was just handed an Acer AL1916W monitor to replace a bad, but non-wide screen monitor.

I am running dual monitor, but I don't believe that the graphics card in here is of recent enough vintage to support it.  

Question 1:  can ubuntu support dual monitors with different resolutions on each?

what type of cheap video card do you suggest that will run this.  I don't do graphics or play games, I just do software development on it.  I don't need anything fancy, or too nice.  Just functional.

Thanks!

-spottedowl.

---

### Post by garlik42 on 2007-04-03
I have a similar setup, a 20" wide lcd and a 19" standard lcd. The configuration works in XP, but I have not been able to get it to work properly with X, and it's not just with ubuntu, I can't get dual different rez screens to work with gentoo either. 
The best I was able to get, was the same 1280x1024 resolution on both monitors using nvidia twinview.

---

### Post by jjordan on 2007-04-04
Short answer: yes, Linux will support two monitors of diffrent resolutions.  I am using a laptop with an internal 1024X600 and an external 1680X1050.  I use a dualmonitor layout which means I have different desktops on each monitor, the mouse pointer will move from screen to screen and keyboard input goes to either screen but you cannot drag windows from one screen to the other.  Look at Ximerama, that will provide you a large desktop across two (or more) monitors.  There are many ways to set this up you can use two graphics cards or a single graphics card with two outputs.  If there is a built in graphics card on your mother board you can probably run one monitor with a reasonable color depth on that and then use an addin card for the second monitor.  You should be able to find an **Nvidia** card a few generations old with dual outputs and good support under Linux at a very reasonable price.  If the board has a DVI output a very simple (cheep) adapter will allow you to hook up a VGA cable.

This is not always easy to get working so I would recommend reading the forums and looking other places on the Net for success stories.

-j

---

### Post by SpottedOwl on 2007-04-04
Thanks for the info -- I'm off to the store.
If I can get this <expletive> thing working, I'll post methods/results/amount of analgesics required.

---

### Post by garlik42 on 2007-04-10
Well thanks to jjordan I decided to poke around a bit more and found this thread 

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

Which then pointed me to this thread

[http://www.ubuntuforums.org/showthread.php?p=1773584](http://www.ubuntuforums.org/showthread.php?p=1773584)

And I now have a dual monitor setup, not only in ubuntu but also in gentoo, using the exact same xorg.conf. My setup is a 1280x1024 on the left and a 1680x1050 on the right, and witht the help of these threads, I was able to get the machine working fine with both distros. I was also able to get the nvidia driver working on my work system (only a single 1280x1024) which I have had trouble in the past.

---

