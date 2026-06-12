---
title: "Ubuntu 9.04 and Synaptic not working well together!"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by vickoxy on 2009-07-12
Hi,
I added some repositories in synaptic (with keys...), but ubuntu 9.04 does not recognize/find their programms (Blueman, acroread...). I noticed that it want show many apps in Synaptic, although i added their packages in Synaptic. Does anyone knows what it is? And yes, i am newbie...
Thanks

---

### Post by vickoxy on 2009-07-12
Ok, i find that this is helping:
sudo update-apt-xapian-index

([https://bugs.launchpad.net/ubuntu/jaunty/+source/synaptic/+bug/288797](https://bugs.launchpad.net/ubuntu/jaunty/+source/synaptic/+bug/288797))

Should i do it every time i add something in Synaptic, or?

---

### Post by oldos2er on 2009-07-12
Usually you can just click 'Reload' in Synaptic, or run **sudo apt-get update** in a terminal.

---

### Post by cariboo on 2009-07-12
I had the same problem the other day, I'm running Karmic, but that shouldn't make any difference. I used the first option:

> Any Ubuntu Release and keyring:

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

When I tried the Jaunty repositories, acroread was not available.

---

### Post by vickoxy on 2009-07-12
> **oldos2er said:**
> Usually you can just click 'Reload' in Synaptic, or run **sudo apt-get update** in a terminal.

I did that, but only xapian-index helped. After that, i am pretty sure that reload and synaptic are working well.

Still, i don´t know what that xapian is-i openned one thread asking that question...i am newbie eager to learn more

---

