---
title: "Repository help."
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by einnar on 2009-06-14
I'm trying to automate multiple installs. I have an ISO image that I'm installing from, but would like to add a script to add keys, software, and update the install.

Looks something like this : (shortened for brevity and clear example)

> # ++ ADD REPOSITORIES ++
# + WINE, UBUNTU TWEAK

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list](http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/winehq.list

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FE85409EEAB40ECCB65740816AF0E1940624A220
# maually perform : "sudo gedit /etc/apt/sources.list"
# manually add the following : deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main
# manually add the following : deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main

# ++ INSTALL SOFTWARE ++

sudo apt-get update
sudo apt-get install <software list>

# ++ UPDATE COMPUTER TO LATEST ++

sudo apt-get upgrade

I found the code to automate the Wine key and repository addition, but haven't figured out how to automate the ubuntu-tweaks repo add.

If you know how to do this, please let me know.
Thanks much!

---

