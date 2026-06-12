---
title: "Broken theme for cairo dock"
date: 2008-07-12
forum: General Help
---

### Post by ncanderson42 on 2008-07-12
I installed cairo dock in xubuntu, and everything was working fine until I changed the theme.  Cairo dock isn't actually shown on my desktop, I can go into my process manager and see that it's running, but it's not shown.  When I try to run it from the terminal, I get > Theme directory 256x256/emblems of theme Industrial has no size field


Anyone know of a fix for this?

---

### Post by sayakb on 2008-07-12
Try re-installing cairo dock. 
```
sudo apt-get purge cairo-dock
sudo apt-get install cairo-dock
```

---

### Post by ncanderson42 on 2008-07-12
sorry, I should have said that I've already tried that.  Thank you though.

---

### Post by ncanderson42 on 2008-07-12
> **LinuxIsInnovation said:**
> Try re-installing cairo dock. 
```
sudo apt-get purge cairo-dock
sudo apt-get install cairo-dock
```
Aaand it figures that it would work this time.  Although I didn't uninstall in the terminal.  So that was the problem, thank you.

---

### Post by sayakb on 2008-07-12
np.. What I think the problem would have been that you selected it to either: *reinstall *or *remove *and then installed it again. Did you select Remove Completely in synaptic. If you didn't, then you didn't actually purge it. Purging a package removes its config files also. So if you install it again, you begin with a fresh set of config files with default settings.

---

### Post by fabounet on 2008-07-15
"cairo-dock --maintenance"
when you have some issue like that ;-)

---

