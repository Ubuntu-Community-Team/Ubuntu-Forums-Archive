---
title: "Upgrade always fails $#!@"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by Reggie on 2006-01-25
I had updated my Breezy version to a Dapper version of ubuntu without any problems. Now, all worked fine .. until synaptics recommended some updates .. I hadn't been online with the pc for a while .. so he wanted me to update 512 packages. I tried smart-upgrade, and he succeeded it exept for 1 package. No biggy, I restarted.

Now I can't access X anymore ! :( So I tried to fix it using dpkg-reconfigure xfree-xorg .. without success. Then I tried to upgrade some packages using apt-get, now whenever I try that another package fails. Now I have NO idea what's installed and what not, and worst of all I still can't access my X.

I still can go on the internet :D

What did I do wrong ? How can I fix this ? I tried apt-get ugrade (fails), dist-upgrade (fails), apt-get -f install (fails) ..

---

### Post by MJN on 2006-01-25
I'm afraid my crystal ball is out of batteries... ;)
 
What do you mean by 'fail'? What errors do you get?
 
Mathew

---

### Post by Reggie on 2006-01-25
apt always wants to upgrade like 200 packages .. but everytime some package gives an error, wich makes apt just stop working. Just errors like "the package couldn't be installed (--configure) exit 1;

---

### Post by Reggie on 2006-01-25
Never mind, I'm going to install the whole thing again ;)

---

### Post by Sokraates on 2006-01-25
Try

```
apt-get check
``` 
to see, which, if any, packages are broken. Then you might want to try 

```
apt-get -f check
```

**Edit:** Forgot to recommend the "-m" option: fix missing

---

### Post by Reggie on 2006-01-25
When I do apt-get check. he says:
> E: Unmet dependencies. Try using -f.

When I use -f
> Reading packages lists... Done
Building dependency tree... Done
Correcting dependencies... Done

When I try -m he says the same as when I use it without any options.

---

