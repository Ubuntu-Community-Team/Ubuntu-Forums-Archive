---
title: "Ubuntuzilla versus update manager"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by potatan on 2009-07-23
Hi,

I've used the excellent Ubuntuzilla to install Firefox 3.5.1 and Thunderbird 2.0.0.22, and I have told it to keep me up to date with notifications of new versions etc.  I am running Jaunty.  

Just now though, Update Manager has offered me a few fixes for Firefox 3.0, which I was able to uncheck in the Update Manager window before allowing it to install the other unrelated fixes.

Is there a way to prevent Update Manager from checking for Firefox updates?  I'd hate to click "Install" when there is a big list of updates, and find out that I've screwed my Firefox installation by trying to use some 3.0 components with my 3.5 installation.

Many thanks in advance.

---

### Post by x33a on 2009-07-23
```
apt-get hold firefox-3.0
```works for the command line.

but, i don't know if it'll hold packages for update manager, too.

---

### Post by potatan on 2009-07-23
Didn't work for me:

```
paul@antec:~$ sudo apt-get hold firefox-3.0
[sudo] password for paul: 
E: Invalid operation hold
paul@antec:~$
```

---

### Post by potatan on 2009-07-23
Okay it worked, (well did something) with "-hold" rather than "hold", but it still doesn't seem to have worked:

```
paul@antec:~$ sudo apt-get -hold firefox-3.0
E: Option -hold: Configuration item specification must have an =<val>.
paul@antec:~$ 
```

---

### Post by x33a on 2009-07-23
sorry actually i tried it with aptitude rather than apt, so try
```
sudo aptitude hold firefox-3.0
```

---

### Post by nanotube on 2009-07-24
hi
you don't need to worry about that - just go ahead and let it upgrade ff3.0. it will not affect the ubuntuzilla ff3.5 in any way.

for more info, see the faq on the ubuntuzilla website.

---

