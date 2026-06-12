---
title: "Update Manager doesn't find updates - still on 8.04 =( plz help."
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by Danish989 on 2009-04-23
I have ubuntu 8.04 installed using Wubi, on my laptop, and I wanted to upgrade to the new Ubuntu 9.04.

I figured update manager would've upgraded my ubuntu to 8.10 already, and I could simply use update manager to get to 9.04 on it's release. But I just used cat /etc/issue to find out what ubuntu version I am running right now, and I was disappointed to see it's still 8.04.

And on top of that, Update manager won't pick up any new upgrades. 

I have selected "Normal Release" in Release Upgrade in Software Sources, but I still can't pick up any new upgrades. And this is probably not just with the new release, but apparently update manager couldn't even find the 8.10 upgrade.

What is the problem, and how do I upgrade? I know I'll have to upgrade to 8.10 first, and then 9.04, but how do I do it if update manager doesn't even detect any new upgrades?

Is it because I installed Ubuntu 8.04 using Wubi?

Any help will be much appreciated, thanks in advance.

---

### Post by barney385 on 2009-04-23
sudo apt-get update

---

### Post by m_2009 on 2009-04-23
Have you tried running
 
```
sudo update-manager -d
```
 
That shoudl force the update manager to offer a distribution update...
 
Does that giev you any results?

---

### Post by James- on 2009-04-23
or you can force it to upgrade:
1st:
```

sudo apt-get update

```

then:

```

sudo update-manager --dist-upgrade

```

---

### Post by Danish989 on 2009-04-24
"sudo update-manager -d"  Did it for me, thanks a lot everyone for the help! =) I've successfully upgraded to 8.10 and then 9.04.

However, now I can't use the Extra Visual Effects =(

Ever since I restarted after the upgrade, no more wobbly windows or anything.

I right-clicked desktop>>change desktop background>>Visual Effects and tried clicking on Extra to turn it on, but each time I get the message that says:

Searching for available drivers...
Desktop effects can not be enabled.

I'm going to put this question up at the right thread, but can any of you help? Thanks again.

---

### Post by dronkula on 2009-04-28
Hi,

I've got the same problem with Update Manager saying that my system is up to date but I'm only on 8.04

I tried sudo update-manager -d and that didn't make a difference

I also tried 'sudo apt-get update' but that couldn't connect up to the servers.  Basically, I'm on a Uni network and have to use their proxy servers to get out.  I've setup Synaptic so that it's got the proxy servers and that runs fine (and update manager itself connects up, downloads stuff and then tells me there's no updates).

So, how to I setup a 'command line' process like apt-get to use the proxy server?

Any thoughts?

---

