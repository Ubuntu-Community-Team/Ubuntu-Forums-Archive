---
title: "nVidia: how do I get better drivers?"
date: 2015-03-26
forum: Hardware
---

### Post by PenguinLust on 2015-03-26
I'm having some trouble with a few graphical things and a couple of people have thrown buzzwords around like "proprietary driver". What is that and how do I change the drivers I have for something that might work better? I run "dpkg -l | grep -i nvidia" and it reveals nothing.
I'm running Ubuntu 14.04.02 and an nVidia GeForce GTS 250

---

### Post by Vladlenin5000 on 2015-03-26
System settings > Software & Updates

Find the rightmost tab "Additional drivers", wait a few moments and you should see a list. The driver currently in use, *nouveau*, is the default open source driver. Select and apply the recommend nvidia driver if you want to try the proprietary driver.

---

### Post by oldfred on 2015-03-26
Ubuntu repository does not always have the newest driver.
But your card should work with whatever is the newest in the repository. My 14.04 install shows 331.xx as newest it offers.

And you card now has a legacy driver as 340.xx is the newest you can use, the newer drivers are only for newer cards.

 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

If you accidentally install incorrect driver you must totally purge all traces of old driver before installing the correct one. They conflict and cause major issues otherwise.

---

