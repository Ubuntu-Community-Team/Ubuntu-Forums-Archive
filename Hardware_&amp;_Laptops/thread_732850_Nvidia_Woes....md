---
title: "Nvidia Woes..."
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by Xavieran on 2008-03-23
I have just recently installed Gutsy 7.10 on my mom's laptop (a Lenovo 3000 N100).
I did the usual enable dvd this blah blah, and then installed the nvidia restricted driver...
I rebooted and the screen flashed three times and then finally a your monitor could not be configured etc. etc. screen came up,I clicked continue and then was greeted with an extremely low res screen (800x600).So the first thing I did was remove the nvidia driver through synaptic...I rebooted but the screen res was still low...

I also edited the xorg.conf by hand,and changed the screen modes from 800x600 to 1280x800 but it didn't change anything...

Note that the screen and nvidia driver work fine on sabayon linux on the same computer...if you need any specs from my sabayon install for comparison,just ask :).

xorg.conf attached...

EDIT:I have followed Kool_Kats advice on changing "nvidia" to "nv" in this thread and my res is now normal...
I still don't have 3d effects yet though ;). Let's all hope this is fixed in Hardy :D

---

### Post by oldsoundguy on 2008-03-23
you failed to mention the display chip. (I don't do laptops, but those that do need that information to be able to help.)

---

### Post by oldsoundguy on 2008-03-23
oops .. sorry .. (read the title dummy!!! LOL) '..

they still will need the NVidat chip numbers .. but did you try to install using Envy?

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I used the program on 3 desktops and not a hitch!

---

### Post by Xavieran on 2008-03-23
It's an NVidia GEForce GO 7300.

I'll test envy out...were these on Gutsy, these three desktops?

---

### Post by oldsoundguy on 2008-03-23
yes.  It's worth a shot as most that use the program have good luck with it.

---

### Post by jimoz on 2008-03-24
I had similar problems with my laptop, also on a Go 7300... screen res still reverts to low res after using the SVIDEO out (I need to reconfigure xorg.conf), but screen is OK now. I had to reinstall envy, and switch the Monitor settings back as it was reverting to a plug-n-play monitor, and not allowing anything higher than 800x600.

---

### Post by Xavieran on 2008-03-24
Envy didn't work...
I suppose I shall just have to wait for Hardy...but if this is going to be a LTS I would suggest that they get that fixed :)

---

