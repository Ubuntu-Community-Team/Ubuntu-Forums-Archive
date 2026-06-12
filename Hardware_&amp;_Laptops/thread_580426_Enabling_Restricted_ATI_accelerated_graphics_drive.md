---
title: "Enabling Restricted ATI accelerated graphics driver"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by MJewkes on 2007-10-18
Hello,

I recently did a fresh install of Ubuntu 7.10 on my acer Travelmate 4400 (4402 WLMI).

When I try enabling the ATI accelerated Graphics driver, I get the message 

```
The software source for the package

   xorg-driver-fglrx

 is not enabled.
```

Please help,
Thanks,
Matthew Jewkes

---

### Post by GvdM on 2007-10-18
> **MJewkes said:**
> Hello,

I recently did a fresh install of Ubuntu 7.10 on my acer Travelmate 4400 (4402 WLMI).

When I try enabling the ATI accelerated Graphics driver, I get the message 

```
The software source for the package

   xorg-driver-fglrx

 is not enabled.
```

Please help,
Thanks,
Matthew Jewkes

Ditto with the ATI mobility FireGL

---

### Post by gtkspert on 2007-10-19
i was having the same issues!
enable the proprietary drivers under preferences in add/remove programs.
then try again, works like a charm..
Have fun guys!

---

### Post by JoePits on 2007-10-19
> **gtkspert said:**
> i was having the same issues!
enable the proprietary drivers under preferences in add/remove programs.
then try again, works like a charm..
Have fun guys!

eanwhile, AMD's October Linux driver -- the much anticipated fglrx 8.42.x -- should be out within a couple of days.  :guitar:

---

### Post by TheNatealator on 2008-01-22
I have tried all of the above, and envy, to no avail. Everything but synaptic insists that there is a problem with dependencies (before I enabled proprietary drivers, it was xorg-driver-dev, and now the restricted drivers manager says a generic fix packages, and envy says the problem is module-assistant).

Any ideas?

---

### Post by Yellow Pasque on 2008-01-22
First, go to System -> Administration -> Software Sources, and make sure the first four options on the first tab are enabled/checked.
Now what is the output from the following command?:
```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by TheNatealator on 2008-01-22
Thank you very much, I didn't have any of the boxes checked. Now it should be working fine (just have to restart).

---

