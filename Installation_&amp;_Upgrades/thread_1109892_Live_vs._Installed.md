---
title: "Live vs. Installed"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by BelaC on 2009-03-29
Hi lads,

It's really same are as a Live and as an Installed OS (just faster as installed)? I ask 'cos I have trouble with installed version(s). More kind of distro's running well as Live but installing on my laptop doesn't. For example my Kubuntu as Live OK and as installed I can't to change my every time fading display. I has been tried fixing this problem with install KPowersave no bother. It's normally working under moving the slider but dimming back when do nothing with. (I switched off auto fading func as well!)

Please give advice.

---

### Post by cariboo on 2009-03-29
I would suggest running the LiveCD and then doing a listing of the installed drivers. Open a terminal and type:

```
lsmod > modules.txt
```

the above command will list all the installed modules in a text file, save the file to your hard drive, then boot to your regular install. Run the same command and compare the two files to see if there are any differences.

Jim

---

### Post by BelaC on 2009-03-30
> **cariboo907 said:**
> I would suggest running the LiveCD and then doing a listing of the installed drivers. Open a terminal and type:

```
lsmod > modules.txt
```

the above command will list all the installed modules in a text file, save the file to your hard drive, then boot to your regular install. Run the same command and compare the two files to see if there are any differences.

Jim

Thanks for advice. I'll try this out today.
(I agree many things are in handbooks but for a novice some like chinese language)
I hope with Jim can solving (only?) my problem. 

Bela

---

