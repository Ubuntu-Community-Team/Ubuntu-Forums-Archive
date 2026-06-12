---
title: "Wireless Scanning?"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by CarlosinFL on 2006-10-29
Is there a tool available (GUI) that I can use to see the available access points and also display the current WAP I am connected to?

Thanks!

---

### Post by sam81 on 2006-10-29
You might try

network-manager-gnome

or

kwifimanager

---

### Post by kno712 on 2006-10-29
wifi-radar is a good tool

sudo aptitude install wifi-radar

you can check it at [http://www.gnomefiles.org/]("http://www.gnomefiles.org/")

Best Regards

---

### Post by JacobRogers on 2006-10-29
This thread was most useful to me, I added wi-fi radar through the add/remove programs menu, and I've been a happy camper.

---

### Post by CarlosinFL on 2006-10-29
I think I am looking for wifi-radar as that rings a bell!

Only problem is this is a fresh install of Ubuntu and it is not in the default vanilla source repo.

I have added my source list below to show you what I may be missing - any suggestions.

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

---

