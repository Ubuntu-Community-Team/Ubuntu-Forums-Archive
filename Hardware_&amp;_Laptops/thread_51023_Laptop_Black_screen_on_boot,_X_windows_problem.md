---
title: "Laptop Black screen on boot, X windows problem?"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by mbmonk on 2005-07-22
Ok i have a Dell Inspiron laptop (model number slips my mind)

When I boot up normally on my laptop I get a black screen. I plugged in my CRT Monitor to the laptop and instead of a black screen I get the ubuntu GUI login screen.  So how can I config ubuntu to display on my laptop?


Any clues? Any way I can give you more information? Should I post this to another forum? Should I take my shoes off and do an African tribal dance to the laptop gods?

Thanks,
mike

---

### Post by adwait on 2005-07-22
I would reccoment the dance........or if that doesn't work, I have this recipe for a potion which might work ;)

Anyway, this probably is a problem with the xorg-config. Why don't you boot into text mode and try running
sudo dpkg-reconfigure xserver-xorg

---

### Post by mbmonk on 2005-07-22
Are there any settingings inside reconfigure xserver-xorg that are generally compatible with almost any hardware?

I ran through the config using default settings and it didn't resolve the problem. I tried using vega and vga but to no availe. 

Any other suggestions :).


The dance has not worked yet obviously :P

---

### Post by damonw5 on 2005-07-22
[QUOTE=mbmonk]Are there any settingings inside reconfigure xserver-xorg that are generally compatible with almost any hardware?

I ran through the config using default settings and it didn't resolve the problem. I tried using vega and vga but to no availe. 

Any other suggestions :).


The dance has not worked yet obviously :P[/QUOTE]
 What is the model number? Often you can google "Linux on Inspiron [model#] laptop" and get web pages that include people's working config files. In particular, look for references to "xorg.conf".

Any other ideas?

---

### Post by jdkron on 2005-07-22
I've run into some problems with X becuase I had the wrong version of BIOS on my Dell.  I actually had to go from version A11 back to A08 on my Inspiron 2600 to resolve the problem.

I'm new at this so I can't say that is the problem, but it may be worth considering/researching.

Good luck.

---

### Post by mbmonk on 2005-07-23
Just for the record it is a Dell Inspiron 6000.  As a side not I JUST upgraded my BOIS before installing Ubuntu. But I will research it. Thanks guys :)

---

