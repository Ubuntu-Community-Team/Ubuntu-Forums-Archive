---
title: "How much memory does ubuntu require&#65311;"
date: 2020-08-06
forum: Hardware
---

### Post by zys1233 on 2020-08-06
Is 512MB OK?

---

### Post by CatKiller on 2020-08-06
> **zys1233 said:**
> Is 512MB OK?

Not really. 

Sure, there are lightweight environments (or no environment) that mean you can run the OS in that little, but applications - and particularly web browsers - will eat that up in seconds.

---

### Post by guiverc on 2020-08-07
To run a GUI I'd suggest no.

If you only want to boot the OS and use a rather simple GUI (like `openbox`, `icewm` etc), text based (ncurses) music player, (ncurses) text editor, lynx web browser & like tools on something like then most probably yes. You may even be able to use some GUI tools as long as only one thing is running at a time. However I'd not expect to have a nice experience with a normal graphical browser like `firefox` etc. Your needs/requirements will really set the minimum.

I used 1GB memory machines in testing 18.04, 18.10 & 19.04 (Lubuntu, Xubuntu primarily, but other flavors too), however for all  later releases I've increased memory (as 1GB is smaller than 99% of users have these days unless VMs without a GUI).

The minimum suggestions on the Ubuntu wiki can be found at [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by maglin2 on 2020-08-07
You could give this debian based distro a try [http://torios.top/about/](http://torios.top/about/)  - I saw it referred to in another thread somewhere on the forum.

It reads like it should install and run on pretty much anything. Applications will be very basic I imagine (Links 2 browser etc).

---

### Post by guiverc on 2020-08-08
FYI:   

I've got an old Nokia box on my desk which stills runs, and until somewhat recently had only 384MB of RAM.  It runs Debian *old-old-*stable, including GUI (multiple are installed but I don't have a favorite on it, usually using something different (icewm etc)  to my main desktop, but LXDE is default).  I can use browsers fine, however I use it to access local (non-web) appliances, switches & routers (so no heavy website processing is done locally). 

I'd not recommend *old-old-stable* Debian as it's nearing the end of it's LTS support period; but I'd recommend a more modern Debian too (though I've not tested *stable* Debian on anything less than 1GB of RAM either.  It has Ubuntu Server installed too, but I never used it with a desktop with Ubuntu)

(*the box remains where it is because it's 4U height is perfect for the monitor sitting on it so it aligns with the two beside it, plus the box has multiple NICs where as my newer boxes have only one*. *Until recently I also liked it's white-noise capability in standby being intended for rack-mount*)

---

### Post by zys1233 on 2020-08-09
yes&#65292;don't GUI&#65292;and if 8GBDISK&#65311;&#65311;&#65311;

---

