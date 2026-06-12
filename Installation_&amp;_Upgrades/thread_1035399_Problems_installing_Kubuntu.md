---
title: "Problems installing Kubuntu"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by LasseNC on 2009-01-09
Hi, I am having some problems installing Kubuntu.

I want to dual boot and have XP installed. 

I put in the Kubuntu CD, choose install, and it runs some things, one is an error, which I am too slow to pick up. 

Mentions something with X-server fail start.

Then I restart, choose the option to try Kubuntu without making any changes.

Then it shows some weird white edgdes that "Glows" toward the center of the screen, and then it switches to "Checking battery state" and it loops between those glows and "Checking battery state"

---

### Post by taurus on 2009-01-09
What is the spec of your machine?  Another option is to use the alternate CD since it's a text based but should be real easy to follow.  Don't forget to burn it at a slow speed like 4x.

---

### Post by LasseNC on 2009-01-09
Alternate CD? 

2gb ram, 1,66 Core2 Duo CPU T5450, HD2400 Mobility

---

### Post by taurus on 2009-01-09
[http://www.gtlib.gatech.edu/pub/ubuntu-releases/kubuntu/8.10/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/kubuntu/8.10/)

---

### Post by LasseNC on 2009-01-09
Sounds more tricky, is it?

---

### Post by LasseNC on 2009-01-09
Problems persist.

I then tried in recovery mode used the "Try and fix Xserver" 

Which didn't help, so now I am clueless.

---

### Post by LasseNC on 2009-01-09
I dug a bit further.

Started in recoverymode, went to root. 

Wrote: 


sudo dpkg-reconfigure xserver-xorg

Then I got to these error messages after trying to start the server.

```
XINIT: Connection refused (errno 11) Unable to connect to X server
```

```
XINIT: No such process (errno 3) Server error
```

A bit furtherer up in the code proess list I saw.

```
Saw signal 11. Server Arborting
```

---

### Post by LasseNC on 2009-01-10
I tried Ubuntu 8.10 also, same problem.

Tried Kubuntu 8.04, works fine with the Live test. 

How do I uninstall the 8.10 and change the boot loader. (Grub?)

---

### Post by LasseNC on 2009-01-10
8.04 installed, but I can't upgrade it.

[IMG]http://www.stalkerzone.dk/upload/upgradefail.jpg[/IMG]

---

