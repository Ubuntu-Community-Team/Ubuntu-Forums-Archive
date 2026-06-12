---
title: "What exactly is a partial upgrade?"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by PacSci on 2009-04-21
Upon running Update Manager, I get the message, "Not all updates can be installed - Run a partial upgrade to install as many updates as possible." This happened shortly after I added the intrepid-backports repository. I'm wondering, though: what exactly is this? Is it something related to the Jaunty launch, or is it just a list of packages that it needs extra permission to install?

---

### Post by tamas305 on 2009-04-21
> Windows is to Linux as a straw house is to a brick house. The bricks are harder to get started with, but they're higher quality and won't crash as easily.

I can't help you with your problem but I love that quote.

Hope you can resolve your problems
-tamas

---

### Post by dtoronto on 2009-04-21
I had a similar problem yesterday.  It seemed that some of my upgrades were video related.  I uninstalled my video drivers and did a 
```
sudo apt-get update
sudo apt-get upgrade
``` from the CLI and it worked.  Not sure which updates you're having problems with. You might want to post them on here.

---

### Post by PacSci on 2009-04-21
It's mostly KDE upgrades - pretty much every KDE package I have on my system. The exceptions are brasero, lintian, and ubuntu-dev-tools.

Any suggestions? (BTW, I mostly use GNOME and Xfce.)

---

### Post by cariboo on 2009-04-21
If you are presented with a partial update, please wait a couple of days for the dependancies catch up. Doing a partial update leads to problems in some cases. If you absolutely need the update, open an Applications-->Accessories-->Terminal and type:

```
sudo aptitude safe-upgrade
```

This will hold back the packages with missing dependancies.

Jim

---

### Post by steveg944 on 2009-04-25
Thank you cariboo907, that helped me in my 8.04 to 8.10 upgrade.

---

