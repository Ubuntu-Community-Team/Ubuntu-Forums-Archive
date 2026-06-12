---
title: "apt-get error I can't fix! HELP!"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by markskerr on 2009-10-03
When I run the Package manager I get the following error:

Remove package in bad state

The package 'ubuntu-tweak' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?

I have tried everything I could think of to rid my system of the "Ubuntu-tweak" with no success

sudo apt-get purge -f ubuntu-tweak_0.4.9-1~intrepid1_i386.deb

apt-get clean

sudo apt-get check ubuntu-tweak*

No matter how I try to get rid of this package I get the following error while using the terminal:

E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.

I do not understand why Ubuntu cannot find the archive. It is still in my download directory. Please HELP. I need to clean my system of this problem.

Thanks

Mark

---

### Post by Partyboi2 on 2009-10-03
Hi, open a terminal and try
```
sudo dpkg --remove --force-remove-reinstreq ubuntu-tweak
```

---

