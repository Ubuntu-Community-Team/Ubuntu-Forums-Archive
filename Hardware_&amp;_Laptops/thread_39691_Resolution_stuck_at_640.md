---
title: "Resolution stuck at 640"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by flurdy on 2005-06-06
Hi,
Ive been running ubuntu hoarty since the week it got released.

The puta has been happily running in 1600x1200 since then, however last week it got stuck in 640x480 resolution. The problem happened when i logged out for the weekend.

Now I know that means my xorg.conf setup is wrong. But I have not changed that for over a month when I changed the nvidia driver. 

So i think one of the updates has made some of my xorg.conf settings invalid.

Ive been applying the updates that come out however I dont log out very often hence, 
dont restart x server particularry often, so im not sure which update is at fault.

I ran the xorg reconfigure script to create  a new xorg.conf, which worked fine, then by trial and error narrowed the issue down to the monitor section. It appears xorg does not like my Iiyama monitor anymore.

This is the old section

Section "Monitor"
   Identifier     "HM903DB/DTB"
   Option         "DPMS"
EndSection

And this is the new default one.

Section "Monitor"
   Identifier      "Generic Monitor"
   Option          "DPMS"
   HorizSync       28-49
   VertRefresh     43-72
EndSection

Anyone got any idea what could have caused this and what i should check?

---

### Post by flurdy on 2005-06-06
Setting better refresh rates helps though.

HorizSync   30-132
VertRefresh 50-200

Still doesnt explain, why on earth xorg no longer accepts the iiyama monitor?
It certainly would confuse n00bs.

---

### Post by flurdy on 2005-06-07
Got the same problem on my other ubuntu desktop.

Definetly a generic bug in ubuntu upgrade.

Easily fixed , if you know the timing of your monitor, but not everyone does.

---

