---
title: "Problem with Upgrade Manager"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by fysikprinsessan on 2009-10-01
Hi,

I'm running Ubuntu 8.04. When I run the Upgrade Manager I get the following error:

***********

Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.

***********

It's been like this for a week or so now, so it does not seem to be very transient. It claims to want to upgrade the following packages:

* libnewt0.52
* whiptail
* linux-ubuntu-module-2.6.24-24-generic

It also says that it can only do a partial upgrade, and it is when I hit "Partial Upgrade" that it complains. I have been in this partial upgrade mode for a very long time (many months), never bothering to try to find out which package is not possible to upgrade, but it never caused me any problems (before at least).

Any idea what is going on? Which logfiles can give me a hint of the problem?

Thanks!

---

### Post by zvacet on 2009-10-01
Do you have any unofficial repository in your source list?If you do comment it in source list.You will do that by typing in applications>accessories>terminal

```
gksudo gedit /etc/apt/sources.list
```

and then find line with unofficial repo (like medibuntu or something else you added) and put # sign in front of that line.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by fysikprinsessan on 2009-10-01
Thank you, that did the trick!

---

