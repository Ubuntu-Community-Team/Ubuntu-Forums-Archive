---
title: "Update manager not showing new distro release"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by DavidS on 2009-01-09
I am running Hardy, and when I open the Update Manager, I see a line announcing "New distribution release '8.10' is available".

However, a friend who is also running Hardy does not get this message.  When she bought her computer it had Dapper on it, and she was recommended not to change to Edgy (which was the latest release at the time).  Update Manager on her computer *did* show the message announcing the release of Hardy, so I conclude that there is some setting that only tells her about LTS releases.

How can I change this so that she sees the announcement of all new releases?

David

---

### Post by Tim Sharitt on 2009-01-09
Open Software Sources and click the Update tab. At the bottom there is a setting for Release upgrade. It can be set to LTS only, normal release, or never. Her's is probably set to Long Term support only.

---

### Post by tuxxy on 2009-01-09
Open **system > admin > software sources > updates**, at the bottom there may be a dropdown menu called show new distribution releases, tell them to select the option of normal releases here and not LTS releases only.

---

### Post by DavidS on 2009-01-09
Thanks for the replies.  Unfortunately the menu does not include "Software Sources".  I opened the menu editor, expecting to find that the item needed the box to be ticked, but it was not there at all.

On my computer "Software Sources" gives the commmand
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

However, neither of those files exists on my friend's computer, although there is a software-properties.desktop file in /usr/share/app-install/desktop .

On my computer, when I click on Settings-Repositories in Synaptic Package Manager I get the Software Sources window with its five tabs including the "Updates" one you mentioned.  However, on my friend's computer a different window comes up, listing the repositories selected but with no tabs at all.

David

---

### Post by avtolle on 2009-01-09
Things were different back in 6.06, a/k/a Dapper. There was no separate "Software Sources". FWIW, it is my suggestion that your friend either update to 8.04 (see [http://www.ubuntu.com/getubuntu/upgrading-8.04#head-db224ea9add28760e373240f8239afb9b817f197](http://www.ubuntu.com/getubuntu/upgrading-8.04#head-db224ea9add28760e373240f8239afb9b817f197) for one way to do it) or 7.10 or 8.10;  for the latter two, she would need to do either a sequential network upgrade, or do a fresh install from an iso burned to CD.

---

### Post by DavidS on 2009-01-09
Thanks for the suggestion, but, as I mentioned in my original post (though rather hidden away, I now see!), she has already upgraded to 8.04, Hardy.

David

---

