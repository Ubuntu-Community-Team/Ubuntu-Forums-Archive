---
title: "Can i try a fresh upgrade?"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by mebigfatguy on 2009-11-05
I am trying to upgrade from 9.04 to 9.10.

The dialog is 'Getting new packages' and is stuck at

Fetching file 1726 of 1729

I can cancel, and it will revert back to 9.04 just fine, but next time i try to upgrade, it immediately starts where it stopped (which normally would be good)..

But still it makes no progress. 

Can i delete all the downloaded files so that it will try to do a fresh upgrade, and maybe get past this point?

---

### Post by mebigfatguy on 2009-11-06
> **mebigfatguy said:**
> 
Can i delete all the downloaded files so that it will try to do a fresh upgrade, and maybe get past this point?

This:

sudo apt-get autoremove && sudo apt-get clean

does it, but i still get stuck next time.... Bummer i guess upgrade is busted for me.

---

### Post by samh785 on 2009-11-06
> **mebigfatguy said:**
> This:

sudo apt-get autoremove && sudo apt-get clean

does it, but i still get stuck next time.... Bummer i guess upgrade is busted for me.
It doesn't exactly help you with upgrading, but you could always back up your pictures/videos/music and your home folder, and do a fresh install. :P

---

