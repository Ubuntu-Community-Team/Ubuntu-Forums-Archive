---
title: "Hard disk going on idle WAY too quickly"
date: 2008-09-15
forum: General Help
---

### Post by mercmobily on 2008-09-15
Hi,

I have a fantastic HP Pavillion dv2000. Everything -- everything -- worked out of the box. It was fantastic...
Now: I noticed that my Load_Cycle_count was up to 22000... after about 1 week of use (!!!). So, I quickly QUICKLY quickly went through the steps here:

[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)

And the problem went away.

However! When the laptop is NOT plugged in, the problem stays -- in a different form.
Basically, the hard drive goes in idle after maybe 20 or 30 seconds of inactivity. This is surely less than healthy for my laptop -- plus, it's a pain because applications freeze for half a second, and when that happens a lot...

I tried:

hdparm -S0 /dev/sda

And:

hdparm -S200 /dev/sda

But no, my drive will stubbornly stop all the bloody time :-D

Does anybody here know what I should do to do things "right"?

Bye!

Merc.

---

### Post by mercmobily on 2008-09-16
Hi,

Anybody...?

Merc.

---

### Post by editrix on 2008-09-17
You'd probably be better off in the Laptops and Hardware forum. Or search your model of laptop using the last link in my sig.

---

