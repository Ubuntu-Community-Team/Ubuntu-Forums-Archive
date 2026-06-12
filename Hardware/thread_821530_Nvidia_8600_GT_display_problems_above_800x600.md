---
title: "Nvidia 8600 GT display problems above 800x600"
date: 2008-06-07
forum: Hardware
---

### Post by pancakelizard on 2008-06-07
I had a previous post with a geforce 8500 gt that I couldn't get to work after several days of troubleshooting. It will not show above 800x600. 
So I purchased another card, but I got a geforce 8600 gt.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814500001](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500001)

Hooked it up and since I was having so many problems before, I did a clean install of Ubuntu. After, I loaded the restricted drivers and the same problem with the previous card happened. So I unloaded the restricted drivers and installed through Envy and the same problem happened. Lastly, I uninstalled Envy and downloaded the latest drivers from nvidia and installed them, with the same problem.

The only thing I can think of is something is conflicting with my Northbridge which is a NVIDIA GeForce 6100 / nForce 430.

Here is the motherboard:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128034](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128034)

Is it wrong to think this? Any other ideas?
I tried about 25423434 things with the last card and nothing worked, I don't want to have to do the same thing with this one also just for it to fail. :(

It's the 64 bit version of Ubuntu 8.04

---

### Post by thideras on 2008-06-07
I very much doubt it is anything on the motherboard.

Open "Screens and graphics" (System<Administration) and change the screen from the default setting to a more "defined" monitor.  Example:  If you have a 1280x1024 LCD, select the "LCD Panel 1280x1024" setting, this should give you the 1280x1024 resolution option.

---

### Post by pancakelizard on 2008-06-07
There isn't a screens and options item under system/administration

---

### Post by thideras on 2008-06-07
> **pancakelizard said:**
> There isn't a screens and options item under system/administrationStrange, I have a "Screen and graphics" under mine :-/

---

### Post by hotweiss on 2008-06-17
The new Envy with 173.14.05 driver is in the repositories. Just enable the Hardy proposed repositories:

[http://albertomilone.com/wordpress/?p=210](http://albertomilone.com/wordpress/?p=210)

---

