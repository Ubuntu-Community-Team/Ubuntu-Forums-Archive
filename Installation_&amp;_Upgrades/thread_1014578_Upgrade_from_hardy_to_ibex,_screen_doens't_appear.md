---
title: "Upgrade from hardy to ibex, screen doens't appear"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by statusquo on 2008-12-18
I'm trying to upgrade from Hardy to Ibex following the directions on the main web site:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I've gotten to step 5 without any problem, but after that the screen that is supposed to inform me that there is an upgrade available doesn't appear. I also tried "sudo apt-get dist-upgrade" and that didn't work either. Both times I'm being told my system is completely upgraded.

Anyone have any idea what's wrong?

---

### Post by luoenzhen on 2008-12-18
Are you sure you're online? check the /etc/apt/sources.list

---

### Post by statusquo on 2008-12-18
Yes, I am online, but I'm behind a proxy. I've set the proxy information in the Synaptic package manager's "network" tab, and I've been having no problem updating my existing packages.

I'm not sure what you wanted me to check in /apt/sources.list, but I've attached it for reference. I haven't touched it so it should be the default settings.

---

### Post by appier on 2009-04-10
> **statusquo said:**
> Yes, I am online, but I'm behind a proxy. I've set the proxy information in the Synaptic package manager's "network" tab, and I've been having no problem updating my existing packages.

Experiencing the same problem here.  Did anyone ever find a solution?

Mark

---

### Post by david_kt on 2009-06-06
> **appier said:**
> Experiencing the same problem here.  Did anyone ever find a solution?

Mark

What I do is:

```
gksudo gedit /etc/apt/sources.list
```

Replace all hardy to intrepid and save it.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

I have not finished upgrading yet, but looks like I will need to troubleshoot the upgrade afterward. It is better to do clean install if you could.

DK

---

