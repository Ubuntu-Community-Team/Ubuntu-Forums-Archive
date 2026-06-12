---
title: "Samsung X420"
date: 2010-01-01
forum: Hardware
---

### Post by fforster on 2010-01-01
Hi

I have installed Ubuntu 9.10 in a Samsung X420 laptop. I am having problems with the LED brightness control and the wireless connection. The brightness control does not work with the keys indicated in the keyboard, I installed xbacklight and it does not work either. The wireless connection works really badly compared to Windows 7. I can do speed tests and they show the proper speed (4Mb/s with my connection), but too many times the connection cannot be made, or there is a big delay before any webpage starts downloading.

Any thoughts would be very welcomed! I haven´t found anything about this laptop and Ubuntu, so I presume this could be useful for other people too.

Thanks!

---

### Post by nukul on 2010-01-07
Hm, did you find out anything in the meantime? I am thinking about buying exactly this notebook and running ubuntu 9.10 on it, so it would be great to know things are working by now^^

---

### Post by fforster on 2010-01-11
Hi, I have not solved the LCD brightness problem and the wireless connection seem to work better most of the time now, although never as well as in Windows 7. Cheers.

---

### Post by nukul on 2010-01-11
I found out some stuff about this problem.
Samsung netbooks (N128, N130) seem to have the same problem,
and there exists a patch in Kernel 2.6.33: Greg Kroah-Hartman created a module that implements this functionality (if you want to have a look at it, get 2.6.33-rc3 sources and look in drivers/staging/samsung-laptop), but I'm still struggling with the darn thing to work on the X420.
If I can't get it to work till Thursday or so I'll just give the notebook back and buy an Acer or something like that^^

---

### Post by fforster on 2010-01-26
Hi, did you manage to make that work? Have you notice anything strange with your wireless card? Or you have switched to a different laptop? I have not been able to try what you suggested.
Cheers.

---

### Post by nukul on 2010-01-26
Nope, I gave back the Samsung and switched to an Asus UL30A.
For one, I like the Asus better (nicer performance, better battery), and it works great with Ubuntu, too (apart from the webcam being upside down, but there is a fix for that. I just don't use the webcam, so why should I fix it? :D). Sorry for you, though. Hopefully a new Kernel release will fix that stuff.
For the wireless card, the Asus also came with an Atheros adapter (AR9285), and connections are a lot better with backports modules installed. You need to activate them first, either in System -> Administration -> Software sources or directly uncomment the lines in you /etc/apt/sources.list for enabling the backports repo. After that, do a search for "backports" (aptitude search backports) and install the right ones for your kernel version (run "uname -r" if you don't know it). That might fix some stuff. Hope I could help^^

---

### Post by fforster on 2010-02-02
Wow! It made a huge difference on how the wireless connection works. 
Thanks a lot for the tip. :D

---

### Post by nukul on 2010-02-02
Glad I could help you! :)

---

### Post by sroschke on 2010-03-15
Hi,

did you get your touchpad to work? I have a strange problem with Ubuntu 9.10: see here: [http://ubuntuforums.org/showthread.php?t=1425719](http://ubuntuforums.org/showthread.php?t=1425719)

I encountered the brigtness problem as well as the wireless problems and will try the new kernel 2.6.33. Thanks for the tip!

Thanks a lot for your help!
sroschke

---

