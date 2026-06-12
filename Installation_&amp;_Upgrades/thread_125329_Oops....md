---
title: "Oops..."
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by thepocketdrummer on 2006-02-03
So, I had this great idea that I'd install the 32-bit Ubuntu instead of the 64-bit because it was giving me a lot of trouble. Now that I've finally got it up and running, installed the KDE desktop, and everything... I can't get my video card drivers to work again...

I tried the steps I did before, but it's not working.

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-'uname -r' build-essential gcc-3.4
```

I get that far and it seems to have run into an error. Help!

---

### Post by thepocketdrummer on 2006-02-03
Wait, I think I might have gotten it working now...

---

### Post by thepocketdrummer on 2006-02-03
ok, this is what I did...

```
sudo apt-get update

sudo apt-get dist-upgrade

sudo apt-get install linux-headers-`uname -r` build-essential gcc-3.4

sudo apt-get remove --purge nvidia*

sudo /etc/init.d/kdm stop (and gdm stop... one of the two didn't work)

sudo -s

export CC=gcc-3.4

sh NVIDIA (hit tab and enter)
```

Then rebooted, just like I did before... and it goes through the check list... then goes into the console (like you hit ctrl+alt+F1) and sits there... and does nothing.

I'm running Ubuntu 5.10 32-bit. I did ```
sudo apt-get install kubuntu-desktop
``` to get KDE. I searched for restricted and uninstalled the packages there... then did all that code up there... now the OS is dead. Please help

---

### Post by thepocketdrummer on 2006-02-06
I seriously killed it I think. Please Help!
:cry:

---

