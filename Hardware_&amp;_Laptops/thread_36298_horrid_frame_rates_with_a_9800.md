---
title: "horrid frame rates with a 9800"
date: 2005-05-22
forum: Hardware &amp; Laptops
---

### Post by dust on 2005-05-22
Alo. New to ubuntu, and I must say a good piece of work. 

Now with the pleasantries done with, I'm in a bit of a tiz. I have an ati 9800 radeon card, and I have fglrx drivers installed and seeming to work properly. flglrx_info reads ati instead of mesa and flglrxgears runs, but I'm stuck with icky 400 fps frame rates. Anywhere from 420-425 was the highest I saw for a bit. Anything I haven't done that's giving me such horrid performance? 

Full specs on the box are:
amd 3200 xp
768mb pc333 ram
ati 9800 radeon 256mb ddr
20gb 7200rpm HDD

As a comparison, on the windows partition, eq2 runs hella smooth at high quality settings with shadows turned off. Thanks ahead of time :) .

---

### Post by dust on 2005-05-23
No one?

---

### Post by Stealth on 2005-05-23
You need to install binary drivers for your Radeon card...

[http://ubuntuforums.org/showthread.php?t=24557&](http://ubuntuforums.org/showthread.php?t=24557&)

Or search for others...get ready for a heck of a lot of work, Radeon drivers can be a massive pain if done wrong. One good thing came out of my installation, I learned how to compile a kernel... :roll: Good luck  ;-)

---

### Post by dust on 2005-05-24
I have the radeon drivers installed and working. I wouldn't be getting any frame rate counts if they weren't, fglx_gears wouldn't run :) .

---

### Post by poofyhairguy on 2005-05-24
Those gears are a bad benchmark. So just try a game and see if it works good enough for you. If not, the problem is ATI's crappy drivers for Linux. Can't help you on that, my personal way to solve that problem was to sell my ATI card on ebay and get a n Nvidia one.

Another thing you might try is installing the newest drivers from ATI's site. Use alien to turn the RPM file into a deb.....

---

### Post by Stealth on 2005-05-24
Without the drivers I would get 400ish fps. WIth them properly install, I would get 6000+. Its not a good benchmark, but it lets you know if you've installed your stuff right, and yours apparently aren't. Believe me, Radeon drivers are a huge pain, its ATI's fault though. Do some searching and find out whats wrong...

---

