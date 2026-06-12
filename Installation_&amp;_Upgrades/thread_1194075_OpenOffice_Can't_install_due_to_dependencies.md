---
title: "OpenOffice: Can't install due to dependencies"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by roadrawts on 2009-06-22
I did an apt-get remove openoffice.org because it had problems with the intention of reinstalling it.  But now I can't get it to install because of dependencies that will not install.  Is there a way that I can force the install of a complete OpenOffice suite?  On Ubuntu 7.10.

---

### Post by BbUiDgZ on 2009-06-22
after the failed install try
```
sudo apt-get install -f
```

---

### Post by roadrawts on 2009-06-22
Thanks.  I'll try that tonight.

---

### Post by ugm6hr on 2009-06-22
Ubuntu 7.10 is not supported anymore.

Hence apt-get will not work (the repositories have been moved).

I would recommend reinstalling 9.04 (or upgrading to 8.04LTS).

---

### Post by roadrawts on 2009-06-24
You are correct that the -f switch did not help with the apt-get install on 7.10.  I have to get a new graphics card before I install either 8.04lts or 9.04 because mine is no longer supported.  

Thanks for the input.  9.04 is probably my best bet.

---

### Post by ugm6hr on 2009-06-25
> **roadrawts said:**
> I have to get a new graphics card before I install either 8.04lts or 9.04 because mine is no longer supported.  

Really?  I am surprised.

I know there have been occasional regressions in Ubuntu, but it would be bizarre for a card not to be supported at all.

Out of interest, what card is it?  Perhaps post the output from:
```
lspci
lshw -class display
```

Oh, and the Gutsy repositories still exist somewhere, if you want to persevere with it.  Try googling old-releases and ubuntu - there are lots of posts in this forum about it.  Just can't remember the address.

---

