---
title: "Update-manager not offering Jaunty"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Diskdoc on 2009-04-24
I'm running an Edubuntu 8.10 server (amd64) with the latest updates. I  would like to upgrade to Jaunty but the update-box in Update-manager doesn't come up!

I've downloaded the latest packade-info and also changed the server..nothing.

On my laptop running Ubuntu I get the box in Update-manager for upgrading to Jaunty.

[I]root@eduserver:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
[/I]

What's wrong?

---

### Post by Partyboi2 on 2009-04-24
If you are using a server version open a terminal and try
```
sudo apt-get install update-manager-core
```
```
sudo do-release-upgrade
```

---

### Post by Diskdoc on 2009-04-24
Well, it is used a server but runs with a desktop. I've used the GUI to upgrade sometime before. update-manager-core is installed.

If there is no other solution, I will try to upgrade using the Jaunty CD first, after that the commandline option you suggest.

---

### Post by Partyboi2 on 2009-04-24
What happens when you try and start update-manager from the terminal
```
sudo update-manager -d
```

---

### Post by okenobu on 2009-04-25
I had the same problem. I fixed it by modiying **/etc/update-manager/release-upgrades**. 

Change the line

```
prompt=never
```

to
```

prompt=normal
```

Then run update-manager -d and you should see the upgrade button.

---

### Post by Liquidity_C on 2009-04-25
To do what okenubu mentioned graphically, open the update manager click settings and in the release dropdownbox select normal releases.

Ubuntu 8.10 is a longterm support thus it will only pay attention to other LTS releases and not the regular ones.

Maybe a bit overzealous to mention this since it is solved but now you can do it either way.

---

### Post by Diskdoc on 2009-04-25
I finally got to the bottom of this: apparently, all machines that were set (through apt.conf and Synaptic) to use our apt-proxy for package downloading did not offer the Jaunty upgrade!

Disabling the proxy solved the issue.. I'll take a closer look at it and see if there is someway to upgrade with the proxy enabled. Would save loads of time and traffic with our twenty or so machines.

Looks like there's a bug for this? [https://bugs.launchpad.net/ubuntu/+source/apt-cacher-ng/+bug/334761](https://bugs.launchpad.net/ubuntu/+source/apt-cacher-ng/+bug/334761)

---

### Post by phazon. on 2009-04-30
I have the same problem, and having done what partyboi2 suggested, still have the issue - the update manager only offers me 8.10 as an upgrade. I am running 8.04

I have no idea what diskdoc or the link he pointed at is talking about, so don't know if that is the problem. But I don't have a proxy set. Please help

This is my release-upgrades file
  GNU nano 2.0.7     File: /etc/update-manager/release-upgrades                 

# default behavior for the release upgrader
#

[DEFAULT]
# default prompting behavior, valid options:
#  never  - never prompt for a new distribution version
#  normal - prompt if a new version of the distribution is available
#  lts    - prompt only if a LTS version of the distribution is available
prompt=normal

---

### Post by Partyboi2 on 2009-04-30
> **phazon. said:**
> I have the same problem, and having done what partyboi2 suggested, still have the issue - the update manager only offers me 8.10 as an upgrade. I am running 8.04

I have no idea what diskdoc or the link he pointed at is talking about, so don't know if that is the problem. But I don't have a proxy set. Please help

This is my release-upgrades file
  GNU nano 2.0.7     File: /etc/update-manager/release-upgrades                 

# default behavior for the release upgrader
#

[DEFAULT]
# default prompting behavior, valid options:
#  never  - never prompt for a new distribution version
#  normal - prompt if a new version of the distribution is available
#  lts    - prompt only if a LTS version of the distribution is available
prompt=normal
You can not skip releases so you will need to first upgrade to 8.10 before trying to upgrade to 9.04

---

### Post by phazon. on 2009-04-30
> **Partyboi2 said:**
> You can not skip releases so you will need to first upgrade to 8.10 before trying to upgrade to 9.04

:oops::oops: OK well that was a pretty simple resolution!

I had no idea about that. So what is the best practice - online upgrade to 8.10 then again to 9.04, or download the CD and upgrade myself?

Thanks

---

### Post by Partyboi2 on 2009-04-30
> **phazon. said:**
> :oops::oops: OK well that was a pretty simple resolution!

I had no idea about that. So what is the best practice - online upgrade to 8.10 then again to 9.04, or download the CD and upgrade myself?

Thanks
I prefer to do a online upgrade but if you have a slow internet connection like dial up then I would suggest downloading the alternate cd from a faster internet connection and upgrading.

---

