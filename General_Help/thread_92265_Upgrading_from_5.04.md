---
title: "Upgrading from 5.04"
date: 2005-11-19
forum: General Help
---

### Post by zoqaeski on 2005-11-19
I haven't been here for a while, but during my absence it seems that Ubuntu 5.10 is now up and going and it has become the current stable release. I've got a few questions about it: 

- Is there a simple sort of way to upgrade from 5.04?
- How should I go about backing up and protecting all of my existing data (I've got a backup disk, etc; could it be affected if I decide to do a full upgrade?)

EDIT: On the [Ubuntu Guide]("http://www.frankandjacq.com/ubuntuguide/5.04/#upgradingubuntu") it says to just modify the sources list; is this the recommended way of doing an upgrade?

cheers
Robbie

---

### Post by matthewv on 2005-11-19
The usual way is to edit your sources.list (/etc/apt/sources.list) and replace all instances of "hoary" with "breezy". Then do ```
sudo apt-get update
sudo apt-get dist-upgrade
``` wait, reboot, and you should be all set

---

### Post by frodon on 2005-11-19
BE CAREFUL, you may have some problems if you don't re-install the ubuntu-desktop metapackages before the upgrade.
So to avoid many problems, follow these instructions (i advice to use synaptic since it's easier to solve conflicts with than with the terminal) : [https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29](https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29)

---

### Post by Denis on 2005-11-19
Maybe this is a good opportunity to ask my question: 

I am using Hoary and I was wondering: when Dapper is released in the future, will I be able to update straight to Dapper? Or do I have to update to breezy first?

---

### Post by frodon on 2005-11-19
I think you will be able to update to drapper directly but the breezy update works really well, i ran the update since breezy was released and all worked as in hoary after the first reboot. I just needed to re-instll nvidia drivers.
So if you're really scared by breezy you can wait drapper but the breezy update will not destroy you configuration ... up to you ;)

---

### Post by missmoondog on 2005-11-19
I just went through this process on 5 machines this past week. only been using ubuntu a month! my dad is making me do it. i tried a different way everytime and the best/only way it worked right the the first time was to upgrade from a cd. i did lose my desktop everytime and had to update it from the text mode type screen (i hate that!). wasn't to tough though. i did follow the instructions for making sure about that part everytime too. at least i thought i did? i now have 5 perfectly running, xp pro/ubuntu 5.10, dual boot machines up and running now though!! i'm a happy camper!! :) hardest part for me on any of the updates/upgrades has been the stupid audio/video codecs. no matter what set of directions i've followed that are posted around here, it takes many, many attempts to get that to work. just now got machine #5 all fixed up on that. REAL happy camper now!! :) :) :)

---

### Post by Wide on 2005-11-19
The CD upgrade is nice due to you can watch it being done quite swiftly, plus you dont need to tie up your bandwidth not to mention if it burps.

Only issue I had was to re-install firefox, everyuthing went just peachy;)

---

