---
title: "Different versions of Pidgin in Hardy"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by DavidS on 2009-01-09
A friend and I both run Hardy, and both of us install all the available software updates as soon as Update Manager shows them.

We communicate a lot using Pidgin.  Today I was trying to adjust some settings for her, but discovered that there were a few differences in the options available.  When I looked further, I discovered that her version of Pidgin is 2.5.2, but mine is 2.4.1.

If I select "pidgin" in Synaptic Package Manager, right-click and then select Properties, it tells me that my version is 1:2.4.1-1ubuntu2.2 and that this is the latest available version.

So why have my friend and I got an older version of Pidgin from the one my friend has, when we are both running continually updated versions of Hardy?  And how would I persuade my computer to look for and find the newer version?

David

---

### Post by Hooya on 2009-01-09
In Synaptic, Settings > Repositories > Updates tab

Check the Unsupported Updates box (backports)

That will give you access, through synaptic/aptitude/apt-get, to much more current versions of software that isn't just a security update.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) for more info (have to read this myself!)

---

### Post by DavidS on 2009-01-09
Thank you very much for that reply - it worked a treat.  I hadn't ticked "Backports" before, because I assumed that it would give access to older versions of software, rather than newer ones.

And I apologise for mistake in the final paragraph of my original message: the words "my friend and" near the beginning should not be there, although you seem to have understood what I meant! :D

---

