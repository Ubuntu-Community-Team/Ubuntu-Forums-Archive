---
title: "Blank screen at login?"
date: 2008-04-22
forum: Hardware
---

### Post by Bertiee on 2008-04-22
Hello,

I've just installed ubuntu on my laptop however am having some problems. When I boot I see the boot screen and the loading bar, however after this I get an entirely blank screen. I plugged in an external monitor and it works fine on that, but I can't get it on the main laptop display. I googled the problem and found various things say usplash.conf may have the incorrect resolution however this appears to be right (1024x768). Along with this the external screen is 1024x768 as well!

Anyone got any ideas? I'd like to use ubuntu but don't want to drag round an external monitor every time I need the laptop!

Thanks a lot

---

### Post by Limpan on 2008-04-22
What kind of laptop is it? Make and model?

It might be the bit-depth. Try changing it in your X.org config file.
You can use CTRL + ALT + F1-F8 to change to another virtual terminal so that you can log on with a text interface and change it.

---

### Post by Bertiee on 2008-04-22
It's a samsung Vsomething - I think v200? I'll check at lunchtime but it's about 4 and a half years old. Sadly my linux knowledge is absolutely nothing, as I was planning on using ubuntu as a starting point!

---

### Post by Bertiee on 2008-04-22
Just for anyone who's interested I sorted the problem by reconfiguring xsever and chose VESA as my display. Thanks for the help!

Now I just need to work out how to speed up the loading of firefox to less than 6 seconds...

---

