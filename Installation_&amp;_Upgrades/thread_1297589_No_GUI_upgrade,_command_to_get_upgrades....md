---
title: "No GUI upgrade, command to get upgrades..."
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by scooterkool on 2009-10-21
I mistakenly upgraded to 9.10 alpha and there is no working video driver for my thinkpad r40. I boot into 9.10 but without a GUI, No X server.
What is the command to upgrade my system without the gui, I have done this before and recovered from it...
The command "sudo apt-get dist-upgrade" tries to launch APT and that fails since there is no GUI....
Thanks!!!

---

### Post by merlinblack on 2009-10-21
"sudo apt-get dist-upgrade" should work with out the GUI system.  What error do you get when you try it?

---

### Post by scooterkool on 2009-10-25
:confused: I must have had the syntax wrong, it does work!
Thanks merlinblack! cool avatar!!
But it does not connect to my wireless network....

When 9.10 final is released I would like to upgrade using the alternate CD, Is there a link to the correct screens and how to upgrade my 9.10 alpha to 9.10 final without wiping my HD?
I've tried an alternate CD and I always end up at the partitioner and it looks like it will overwrite my data, I would like to see a link with screen caps of an alternate install.

---

### Post by merlinblack on 2009-10-26
I guess what you are wanting to do, is upgrade via a CD rather than re-install, thus keeping all your list of install software intact.  Then you don't have to reload and reconfigure everything. You would think this would be possible ( I can imagine lots of people would want to do this), but I'm unsure about how you would go about it.

At a GUESS, perhaps in the partitioner screen, don't change the partitioning, and de-select the option to format?  If that doesn't work as expected you might end up with a big mess however.  I haven't used the alternate CD myself.  Perhaps someone who has could comment.

---

### Post by jarl on 2009-11-12
> **merlinblack said:**
> "sudo apt-get dist-upgrade" should work with out the GUI system.  What error do you get when you try it?

I have tried this (on my Jaunty server installation), it just finishes with
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Any ideas ?

Jarl

---

### Post by i.r.id10t on 2009-11-12
apt-get update 

first to get a list of new software available.  if apt-get upgrade still says no updates, then check your /etc/apt/sources.list file

---

### Post by jarl on 2009-11-12
> **i.r.id10t said:**
> apt-get update 

first to get a list of new software available.  if apt-get upgrade still says no updates, then check your /etc/apt/sources.list file

I already did an apt-get update. what should I check for in /etc/apt/sources.list ?

Jarl

---

### Post by jarl on 2009-11-12
> **jarl said:**
> I already did an apt-get update. what should I check for in /etc/apt/sources.list ?


I found [https://help.ubuntu.com/community/KarmicUpgrades#Network Upgrade for Ubuntu Servers (Recommended)]("https://help.ubuntu.com/community/KarmicUpgrades#Network Upgrade for Ubuntu Servers (Recommended)")

And apparantly the command
```

sudo do-release-upgrade

```

does it, even without GUI.

Jarl

---

