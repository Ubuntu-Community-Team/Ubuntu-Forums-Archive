---
title: "upgrade to intrepid hangs on preconfiguring packages"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by wizzleteet on 2008-12-22
Hi All,

I 've tried a couple of times now to upgrade to Intrepid, but after download the upgrade process hangs on
"Preconfiguring packages
hotway already configured to use inetd. Leave alone."

Once I left it for the night.
didn't budge.

Tried update-manager as well as manually changing sources.list and doing a apt-get dist-upgrade

Look familiar ?
Any help ?

---

### Post by taurus on 2008-12-22
Which release are you running before you plan to upgrade to Intrepid?

Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by wizzleteet on 2008-12-22
I am running Hardy.

Sources.list (after update-manager edited it):


## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

---

### Post by taurus on 2008-12-22
Have you tried the alternate CD/DVD method?

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading](http://www.ubuntu.com/getubuntu/upgrading#Upgrading) Using the Alternate CD/DVD

---

### Post by wizzleteet on 2008-12-22
Why exactly ?

All the necessary packages have downloaded just fine.

---

