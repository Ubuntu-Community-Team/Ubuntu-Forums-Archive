---
title: "no xserver installed!"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by styven on 2006-10-23
Hi all,

I have tried in vain to install dapper onto a HP NX 6310 laptop, celeronM, 256mb, intel 945gm chipset.

So i installed breezy with a view to dist-upgrading later on.

I only get a text screen after boot, and when i type startx, i get a screen of various errors such as "no screens found", X10 fatal IO error.

So i try "sudo dpkg-recongigure xserver-org" and get told that package 
xserver-org is not installed and no info is available.

Any ideas anyone?

Bit frustrated as i researched and read reviews saying Ubuntu installed straight onto this laptop.

Steve

---

### Post by taurus on 2006-10-23
If you plan to use Dapper, why not instead it directly instead of Breezy and then dist-ugrade later.  Use the alternate CD if you can't get the desktop CD (LiveCD) to run.  Otherwise, wait for a few days and you will get a change to play with the latest one, Edgy Elf, which happens to come out on Thursday...

---

### Post by styven on 2006-10-23
Hi,

Thanks for that.

Tried the alternate cd, install would not complete, went to scren with two white blocks on and then did nothing. This happens at about 60% of software install, maybe a bad disc burn, so tried breezy instead, which has installed, but i have no graphical desktop :( 

Steve

---

### Post by taurus on 2006-10-23
Try not to burn the iso image too fast.  You want to set the speed to be about 4x...

---

### Post by CatKiller on 2006-10-23
> **styven said:**
> So i try "sudo dpkg-recongigure xserver-org" and get told that package 
xserver-org is not installed and no info is available.

It's ```
sudo dpkg-reconfigure xserver-**x**org
```

---

### Post by proleterijat on 2007-01-09
after that black screen with 2 blocks, allow it to finish i had the same problem... later on reconfigure x , and log in through recovery mod into x as a root and add a new user and group it as a users -- and off you go

---

