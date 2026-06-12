---
title: "Synaptic Does NOT List All Third-party Packages"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by chensamurai on 2009-04-14
Alright, I've seen this problem in Januty 9.04 many times now.

Basically, I used the Software Sources manager to add the sources.list entries for the [[PPA of Bogdan Butnaru]("https://edge.launchpad.net/~bogdanb/+archive/ppa")] in addition to the complimentary OpenGPG key for this listed repository. 

Afterwards, I updated the repository list from both the Software Sources menu and from that of the Synaptic Package Manager. However, when I search for Amarok14, the package provided through this PPA, in Synaptic, it is not there. Yet, when I use the Terminal with "apt-cache search amarok" amarok14 clearly shows in the list of packages found.

Now, this is not the first time that I've seen this. I've had a similar problem with finding third-party packages in Synaptic with other PPA repositories, such as the one for Gnome-globalmenu.


So does anyone have any idea what's up with my Synaptic Package Manager? Why is it not listing packages from repositories clearly listed in my sources.list and clearly found through apt-cache search??? ](*,)
So odd... o_O

---

### Post by chensamurai on 2009-04-15
Meh, I found the solution to my own problem from here:
[http://ubuntuforums.org/showthread.php?t=1015138](http://ubuntuforums.org/showthread.php?t=1015138)

Apparently, the cached list of packages that Synpatic uses does not always get updated with repository-add updates. Bug is reported here:
[https://bugs.launchpad.net/ubuntu/+s...ic/+bug/288797](https://bugs.launchpad.net/ubuntu/+s...ic/+bug/288797)

Must run this "sudo update-apt-xapian-index" to re-index the package lists for the quick search feature of Synaptic Package Manager. :lolflag:

---

