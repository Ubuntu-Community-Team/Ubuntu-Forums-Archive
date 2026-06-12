---
title: "Repository doesn't have packages?"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by FraggedLocust on 2009-03-06
I want to get CDemu, so I added the intrepid repository from the launchpad page. upon reloading the packages, I see no mention of anything relating to CDemu.

---

### Post by Partyboi2 on 2009-03-06
What PPA are you using? Are you using this one?
```
deb [http://ppa.launchpad.net/cdemu/ppa/ubuntu](http://ppa.launchpad.net/cdemu/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/cdemu/ppa/ubuntu](http://ppa.launchpad.net/cdemu/ppa/ubuntu) intrepid main
```

---

### Post by FraggedLocust on 2009-03-06
Looks to be so. I've made sure I'd added the key and checked the source code box (it has a dash in it instead of a check) and closed the box and reloaded when it prompted me to. Still no luck in searching for CDemu in Synaptic.

---

### Post by FraggedLocust on 2009-03-06
And yet, when i try to use the deb from launchpad, it says the same version is available in a software channel.

When I use this deb, I get an error relating to when i unsuccessfully tried to install a printer driver.
```
Errors were encountered while processing:
  cnijfilter-ip1800series
gdebi-gtk: fatal I/O error 9 (bad file descriptor) on X server :0.0
```

How would I get rid of this unused driver?

Edit: used sudo dpkg --remove, i'll see if that worked. it's installed now, but I still can't see it through synaptic.

---

