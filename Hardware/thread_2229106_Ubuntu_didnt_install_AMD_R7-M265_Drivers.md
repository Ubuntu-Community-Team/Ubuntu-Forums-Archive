---
title: "Ubuntu didnt install AMD R7-M265 Drivers"
date: 2014-06-11
forum: Hardware
---

### Post by mike_ogden on 2014-06-11
Hey everyone,


Need some help here!   How do I get my AMD Radeon R7-265 2GB dedicated graphics chip working on Linux?   Right now it's using the inegrated intel Haswell graphics that is included in the i5-4200u processor that is in my laptop but if i can get my AMD dedicated graphics working that would be great!

Laptop is an acer e1-572G - Here is a link to the exact model if it will help. [http://www.futureshop.ca/en-CA/product/acer-acer-aspire-e1-15-6-laptop-black-intel-core-i5-4200u-1tb-hdd-8gb-ram-windows-8-1-e1-572g-6854/10284817.aspx](http://www.futureshop.ca/en-CA/product/acer-acer-aspire-e1-15-6-laptop-black-intel-core-i5-4200u-1tb-hdd-8gb-ram-windows-8-1-e1-572g-6854/10284817.aspx)

Any help is appreciated!

---

### Post by Mark Phelps on 2014-06-11
Sounds like, from your description, that you have Hybrid Intel/AMD graphics -- and if that is the case, forcing installation of drivers from the AMD site is not going to help because those are not written for Hybrid graphics, but for dedicated cards/chipsets.

To read more about the Hybrid graphics problem: [http://ubuntuforums.org/showthread.php?t=1930450]("http://ubuntuforums.org/showthread.php?t=1930450")

---

### Post by QIII on 2014-06-11
Which version of Ubuntu are you using?

12.04.4 and 13.10 can use hybrid graphics with the installation of fglrx-pxpress -- although this does not seem to work universally.

The fglrx-updates package in 14.04 is *supposed *to have this included already, but I don't have a machine with hybrid graphics to test on.

Of course, there is also the problem here that your GPU is a very recent one and that may be problematic.

---

### Post by mike_ogden on 2014-06-11
i got the 14.04 LTS... should i try an earlier version?

---

### Post by mike_ogden on 2014-06-11
ok, so it APPEARS that somehow I have gotten the amd to work by pressing the windows button, then going to additional drivers.    it popped up with my amd gpu and asked to use the open source, somethine else or the fglrx-updates version, i went to the updates version of fglrx and seems to have done the trick.


is there any way to truly test that it has in fact worked?

---

### Post by QIII on 2014-06-11
Open the Catalyst Control Center and see if it gives you an option to switch between the two GPUs.  It will not change dynamically like in Windows.  You have to reboot.

If you get a message when you open Catalyst to the effect that "it does not appear that you have the driver" you will know then that it hasn't worked.

---

### Post by mike_ogden on 2014-06-11
i tried going into catalyst control centre (Adminitrative), it asked me for a password which i thought was my admin password so i put that it.  then it very quickly says an error message and closes that window.  Doesnt even load catalyst control centre.

the regular catalyst control centre works perfectly.   what am i doing wrong here?

---

### Post by QIII on 2014-06-11
Sometimes it is necessary to open CCC from the terminal.  That would also let us see any error messages.

```
sudo amdcccle
```

---

### Post by armin4 on 2014-08-02
Why don't you just go to 'System Settings' -> 'Details' and check whether the AMD graphic card is being used. If so, you should see this there on the 'Overview' tap.

---

