---
title: "Problem With Touchpad on Toshiba Satellite L300D"
date: 2009-02-07
forum: Hardware
---

### Post by mentrix on 2009-02-07
I Have a Problem With my Touchpad on my Toshiba Satellite L300D Laptop
I Have Installed Ubuntu 9.04 Now.
I Had Ubuntu 8.10 and it worked there...

But in Ubuntu 8.10 My Network Card did not work...
In Ubuntu 9.04 it works :)

But What should i do to get the touchpad Working?
If it is Possible... Now i am Using an USB Mouse...:(

Please Help Me...

EDIT: Solved. Touchpad Works.

---

### Post by AlexBellisBrown on 2009-02-07
This is a known bug i belive: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882)

Jaunty is Alpha so there is bound to be problems, from what i can tell, this is a fix.

[http://launchpadlibrarian.net/21331801/xserver-xorg-input-synaptics_0.15.2-0ubuntu8%2Brebuild_i386.deb](http://launchpadlibrarian.net/21331801/xserver-xorg-input-synaptics_0.15.2-0ubuntu8%2Brebuild_i386.deb)

Give that a try and let us know. :)

---

### Post by mentrix on 2009-02-07
It Worked!

Thanks :KS

---

### Post by taske on 2009-03-06
Thanks, it worked for me to :) I had the scrolling problem.

This is the way a done it. Before installing the package go to Mouse preferences System > Preferences > Mouse, Touchpad tab, unmark vertical and horizontal scrolling. Now install the package. Go back to mouse preferences and mark vertical and horizontal scrolling.  

I've tried with PPA Alberto Milione package [https://launchpad.net/~albertomilone/+archive/ppa](https://launchpad.net/~albertomilone/+archive/ppa) , named in this thread [http://ubuntuforums.org/showthread.php?t=1042085&highlight=jaunty+synaptics](http://ubuntuforums.org/showthread.php?t=1042085&highlight=jaunty+synaptics) , but no results.

Thanks again. :)

---

