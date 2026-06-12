---
title: "upgrade problems"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by DrScum on 2009-01-06
I was still on Ubuntu 7.04 and figured that I have to bite the bullet and upgrade. Followed the GutsyUpgrade recommendations and first upgraded to 7.10 when trying to do so via Network Upgrade I got error messages saying that some archives couldn't be downloaded (not the ones I added to sources.list as recommended.

Then I tried upgrading to 7.10 via the alternate CD, following the instructions after inserting the CD I had the choice to download the most recent packages from the internet. When saying yes, again error messages that some archives couldnt be reached and stop. When saying no the upgrade runs but after restarting the system the lsb_release -a output is still 7.04

What now?

(I'd like to avoid a clean install)

---

### Post by Pumalite on 2009-01-06
To upgrade a system, your OS has to be fully updated first. Next; remove all third parties from /etc/apt/sources.list. Including Medibuntu and it's folder and the lines for Avant-Windows-Navigator (tuxfamily I think it is)
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
Feisty might no longer be supported. I'm not sure.

---

### Post by DrScum on 2009-01-06
I did completely update 7.04 as recommended here [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)
and proceeded just like recommended.

---

### Post by zvacet on 2009-01-06
In your source list do you still have these lines

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

If you do put # sign in front of them.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by DrScum on 2009-01-07
Thanks for the advice,
I did all that and was able to upgrade to 7.10. Thereafter I upgraded to 8.04.1. The upgrade went well until I was ready to reboot. The new boot screen shows several boot options, the top most being the most recent kernel. When selecting that one the boot hung with a black screen saying nothing but Starting up...
When selecting an older Kernel (2 lines down) the boot went ok but a HD check was forced. After that the most recent kernel would boot normal as well.
The only thing I am missing now is the option to boot the WinXP partition, which was available before upgrading. 
Is there a way to get that one back?

By the way, I am using GRUB bootloader.

---

