---
title: "apt-get remove won't remove kubunt-desktop"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by LinuxGold on 2009-07-27
I am running ubuntu server 9.04 x64 version.

I installed kubuntu using apt-get install kubuntu-desktop.

Now I am trying to remove kubuntu by using

apt-get remove --purge kubuntu-desktop
apt-get autoremove

Rebooted the machine, it is STILL running kubuntu.

Re-tried to remove it, here is the output:

```

root@motubuntu01:/home/shamm# apt-get remove --purge kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package kubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

How do I forcibly remove kubuntu-desktop?

---

### Post by nikhilk on 2009-07-27
> **LinuxGold said:**
> 
```

root@motubuntu01:/home/shamm# apt-get remove --purge kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package kubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

How do I forcibly remove kubuntu-desktop?

It has already been unistalled! kubuntu-desktop is just a meta package and does not contain anything itself. Probably
```
sudo aptitude remove kubuntu-desktop
```
might have done the trick.

Still, see if the (rather long) command shown [here]("http://www.psychocats.net/ubuntu/puregnome.php") cuts it for you.

---

### Post by LinuxGold on 2009-07-27
> **nikhilk said:**
> It has already been unistalled! kubuntu-desktop is just a meta package and does not contain anything itself. Probably
```
sudo aptitude remove kubuntu-desktop
```
might have done the trick.

Still, see if the (rather long) command shown [here]("http://www.psychocats.net/ubuntu/puregnome.php") cuts it for you.

aptitude remove didn't work either.  I will have to go through your rather long command one package by one.  I got a lot to lose on my server.  

Thanks.

---

