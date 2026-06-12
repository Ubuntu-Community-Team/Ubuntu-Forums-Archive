---
title: "kisak/turtle  video drivers"
date: 2020-12-26
forum: Hardware
---

### Post by dome78 on 2020-12-26
Hi,
I installed the video drivers kisak/turtle.
Are they more reliable than oibaf, padoka, ecc... ?

Moreover, after i added the ppa, i installed them with 
sudo apt update
sudo apt upgrade

Is this correct? 
(According to the guide at 
[https://launchpad.net/~kisak/+archive/ubuntu/turtle](https://launchpad.net/~kisak/+archive/ubuntu/turtle)
the correct method is
sudo add-apt-repository ppa:kisak/turtle
sudo apt-get update
but it did not work for me)
Thanks!

---

### Post by Yellow Pasque on 2020-12-26
> **dome78 said:**
> I installed the video drivers kisak/turtle.
Are they more reliable than oibaf, padoka, etc... ?

It's hard to give a simple yes or no answer here. Theoretically, they could be more stable. But then, for very new hardware, more bleeding edge mesa like oibaf might work better. Note that depending on what version of Ubuntu you are using, you may not get updated mesa packages from this PPA, as it is actually running behind stock Ubuntu repos in some cases. At first glance, it's not a PPA I'd use, but then maybe they are running behind because of holidays.

---

### Post by CelticWarrior on 2020-12-26
Let's make something clear before you go down the rabbit hole: There's nothing you can do to improve the performance of that old graphics. The drivers any current Ubuntu release comes with are what you should be using. Adding any PPA will NOT change an yota. The PPAs you've benn trying may give some newer and better versions for NEW AMD hardware.

---

### Post by dome78 on 2020-12-27
> **CelticWarrior said:**
> Let's make something clear before you go down the rabbit hole: There's nothing you can do to improve the performance of that old graphics. The drivers any current Ubuntu release comes with are what you should be using. Adding any PPA will NOT change an yota. The PPAs you've benn trying may give some newer and better versions for NEW AMD hardware.

The updated drivers fix a graphic problem in a game.

---

