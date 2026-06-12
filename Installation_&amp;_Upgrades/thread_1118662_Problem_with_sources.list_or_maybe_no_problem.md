---
title: "Problem with sources.list or maybe no problem?"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by RRFarFar on 2009-04-07
Hie,
I am on 9.04 beta Kubuntu. Before installing I had ubuntu 8.10, anyway my root folder is on separate partition 13G and home is on separate partion as well. Before installing 9.04 Kubuntu I formatted / partition and went through installation. I just changed the name of the first added user; in 8.10 Ubuntu (Gnome) it was RI, now it is RILX. So after having system up and running my old home folder files remained intact, so after going as root to dolphin I just cut/paste everything to my new home folder, and changed permission from RI user and group to RILX user and group. Everything is good, but when I try to edit source.list manually form terminal

sudo kate /etc/apt/sources.list

I give me some strange thing like

Error: "/var/tmp/kdecache-rilx" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-rilx" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-rilx" is owned by uid 1000 instead of uid 0.

I can access sources.list though, but I think something is wrong.
Any guess what?????

Maybe I have to assign root owner to some folders instead of user 1000 - meaning me))))

Thanks

---

### Post by miklcct on 2009-04-07
Did you copy things with '--preserve=all' ?

---

### Post by coffeecat on 2009-04-07
I can't quite follow what you describe in your first paragraph, :? but it's clear that you've managed to change ownership of some root files to yourself. What you need to do whenever you get an error like that, is:

```
sudo chown root: /name/of/file
```It'll be safer to chown files individually, rather than a recursive chown for a whole directory. The whole of /var is owned by root (I think - but don't quote me), but definitely not /tmp. You'll have files legitimately owned by yourself in there.

---

### Post by RRFarFar on 2009-04-07
> **miklcct said:**
> Did you copy things with '--preserve=all' ?

No I didn't((( What does it do? Does it preserve ownership?

To coffeecat

I know this command, but how could I touch VAR directory if it is under /, not /home. All I did is moved visible (not hidden) files from /home/ri to /home/rilx.

I will check VAR when I will get back home. It should be root owned

---

### Post by coffeecat on 2009-04-07
> **RRFarFar said:**
>  how could I touch VAR directory if it is under /, not /home.

Pass. :?

> **RRFarFar said:**
> I will check VAR when I will get back home. It should be root owned

Sure. But it'll be interesting to see whether the ownership of /var/tmp/kdecache-rilx really is uid=1000, or whether this is an odd kate bug.

By the way, I'm not a kde user so I'm not sure, isn't kate a GUI editor? If so, shouldn't you be using 'kdesudo kate /name/of/file'? I'm sure you know this link, but I'll post it anyway:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by snova on 2009-04-07
Use kdesudo for graphical programs. That should fix it.

I'm not entirely sure exactly what kdesudo does, but KDE is complaining that directories it makes use of are owned by another user- yours, when it's running as root.

---

### Post by RRFarFar on 2009-04-08
VAR is root owned, probably I did right by moving files the way I described above.

kdesudo command is working just fine, I will use it from now on.

I was using sudo just because I was always under GNOME and now it is KDE 4.2

Slightly off topic - when I browser my sources.list with kate, I can see all the repositories there, somewhere around 10 or so. But when I use KDE KPackageKit (Package Management) in the list of repositories there are only few things like archive canonical, medibuntu and one other. Do you think it is normal? Because I remember Synaptic was showing all my repositories(((

---

### Post by RRFarFar on 2009-04-09
Thanks to everybody who answered:KS

---

