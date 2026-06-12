---
title: "Want to upgrade to 9.10 but got Ati."
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by spatman on 2009-11-10
The thing is that i have a ati x1950xt card on my pc and ther are no working drivers what i have found. all of the drivers i have used i get black screen. so are ther any why around this becouse i like to play some games some times to. and just love the new look on 9.10.

---

### Post by Dimarchi on 2009-11-10
With that card do not use the restricted drivers (fglrx, either from the repos or Ati's web site) - they do not support your card anymore...use the one that is automatically installed. That should not give you a black screen. You do not mention the games you would like to play. That should provide even more accurate advice.

---

### Post by MelDJ on 2009-11-10
to a fresh install and get the driver from the ati site

---

### Post by spatman on 2009-11-10
Okej, becouse i did try run wow but it was lagging as hell when i did try. Well will Cs 1.6 and Day of dedeat:source

---

### Post by snakep on 2009-11-10
> **MelDJ said:**
> to a fresh install and get the driver from the ati site

Can I do a fresh install and retain /home?

---

### Post by Mark Phelps on 2009-11-11
> **MelDJ said:**
> to a fresh install and get the driver from the ati site

This will NOT help you because there is no current ATI restricted driver that works with your card and Ubuntu versions newer than 8.10!!

If you force the install of the latest ATI driver, you will simply corrupt your display and then, you'll have to boot into a console to remove that driver and replace it with the open source drivers.

---

### Post by Dimarchi on 2009-11-11
> **snakep said:**
> Can I do a fresh install and retain /home?

That is possible, as long as you have a separate /home partition and remember to set it as such when formatting partitions. Otherwise if you are looking to preserve some settings or files/documents (such as Firefox, Thunderbird, Skype, etc., copy them from your /home folder to somewhere safe and put them back once you have finished your fresh install). Is it to get rid of fglrx, or why do you ask (considering the thread topic)?

---

