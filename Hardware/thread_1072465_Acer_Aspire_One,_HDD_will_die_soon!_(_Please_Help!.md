---
title: "Acer Aspire One, HDD will die soon! :( Please Help!"
date: 2009-02-17
forum: Hardware
---

### Post by Repgahroll on 2009-02-17
Hello guys.

I have an Aspire One, the Linux version with a 160GB HDD (WD1600BEVT). The Load Cycles are increasing and i don't know what to do, if i disable the power management by running the command "hdparm -B 254(or 255) /dev/sda", the Load Cycles stop increasing, but the temperature became too high (more than 45&#7506;C going up to 55&#7506;C).

I just don't know what to do, there's just 3 options here:

1-Default power management(which cames by default in Linpus) and the HD will die in 4-8 months.

2-No power management, and the HD will surely die faster because it became too hot.

3-Let the netbook turned off :) No Cycles, no hot, and no fun also :(.

The netbook cames from factory to die in a short time, i think it's a very bad thing, i thought Acer was serious, who would buy a computer knowing it will die soon?

Thanks.

---

### Post by pgatrick on 2009-02-17
I don't know what you can really do, but hey, at least hdds are fairly cheap.. And most things are made to wear fairly quickly, that's just the way the world works unfortunately. :/

---

### Post by yey365 on 2009-02-17
I had this problem with an Advent 4489 (msi wind u90) and followed the hdparm route.  I recently upgraded to the Jaunty alpha release and haven't had the hard disk clicking since.  Jaunty has proven stable for my needs.

To upgrade select alt-f2 and insert "update-manager -d" withou the quotes.

---

### Post by Repgahroll on 2009-02-17
Cheap? Man i had to work hard a year and a half to buy this netbook, and now it'll die in 6 months. :(


EDIT:

What's the hdparm parameter that Jaunty uses? I couldnt see any difference from 128 to 254.

---

### Post by Repgahroll on 2009-02-17
Just installed the recovery CD on my desktop and discovered that Linpus uses the values "1" on battery and "254" on AC, which are the same values that ubuntu(8.10) uses by default just enabling laptop-mode, so i can assume there's no better way to manage the hd power on this netbook. I should've bought an asus (Some MSI models has the same HDD) :(.

My netbook is going to die!! :( :(

---

