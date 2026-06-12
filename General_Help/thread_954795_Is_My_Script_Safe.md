---
title: "Is My Script Safe?"
date: 2008-10-21
forum: General Help
---

### Post by fundamental on 2008-10-21
I have been using Ubuntu for over a year now and have found it to be very stable.  I wrote a script to keep my computer updated and want to know if it is safe to run?  So far I have never encountered an error with apt-get, but could anything bad happen? Here is my script:

#!/bin/sh
deborphan | xargs apt-get -y remove --purge
apt-get -y update
apt-get -y upgrade
apt-get -y autoclean
apt-get -y purge
apt-get -y autoremove
apt-get -y dist-upgrade

---

### Post by shawnrgr on 2008-10-21
you need to be carefull when running apps like deborphan, if it cleans the wrong package (which IS possible) you could be in trouble. Also running a distro upgrade is dangerous if maybe a new kernel or somthing kills your drivers.  I like to wait a few days before diving into the newest distro to make sure nothing goes wrong ;) its really preference. its your workstation not mine. Its just not something I would do personally.

---

### Post by cicatrix1 on 2008-10-21
What's wrong with just letting the auto-update feature do it's thing?

---

### Post by sethvath on 2008-10-21
Avoid deborphan especially if its an automated script on your main workstation, it might cause you lots of time trying to remedy the error when you should be working on more important stuff. If its a spare machine by all means do what you want. 

For instance if I have a class lecture to write for my student the next day I do not give in to the urge to do the 58 updates ubuntu-update shows me on gnome-panel, I would wait till I have time to fix some unexpected errors before I go ahead with it. An automated script like yours could potentially cause you unwanted trouble when you have work to complete. 

Some of the commands can be further consolidated like so:
sudo apt-get update && safe-upgrade

That would be the only command in your script, you dont need to autoclean and autoremove after every update.

---

### Post by kerry_s on 2008-10-21
i would lose the "-y" so you get asked before it does something.

i just use alias's:

```

alias s='apt-cache search'
alias i='sudo apt-get install'
alias r='sudo apt-get --purge remove'
alias upd='sudo apt-get update;sudo apt-get dist-upgrade'
alias old='sudo apt-get clean;sudo orphaner'

```

---

