---
title: "Uninstalling program + &quot;other packages&quot;"
date: 2008-08-31
forum: General Help
---

### Post by fungihead on 2008-08-31
ive had ubuntu for a few days now and im confused by the installing/uninstalling of programs.

when i install something through the synaptic package manager, i pick what i want and it installs a load of other packages necessary for the program to work. fair enough.

but if i uninstall something through the synaptic pacman (lol) it says nothing about removing the other packages.

do these just go without it mentioning or do the stay and clog up space on my hdd? and if they do stay, is their a way to remove them all? does it even matter if i just leave them?

thanks

---

### Post by quibbler on 2008-09-01
> **fungihead said:**
> ive had ubuntu for a few days now and im confused by the installing/uninstalling of programs.

when i install something through the synaptic package manager, i pick what i want and it installs a load of other packages necessary for the program to work. fair enough.

but if i uninstall something through the synaptic pacman (lol) it says nothing about removing the other packages.

do these just go without it mentioning or do the stay and clog up space on my hdd? and if they do stay, is their a way to remove them all? does it even matter if i just leave them?

thanks
Synaptic will normaly uninstall everything unless the program is
used for something else. You can check for orphan libraries in synaptic
and delete these part. (look under the custom filter.

Regards quibbler

---

### Post by Cheesehead on 2008-09-01
My Synaptic doesn't have a filter to find orphaned packages.

If yours doesn't, 
then open a Terminal window (Accessories --> Terminal) and use the command:
```
sudo apt-get autoremove
```
The system will prompt you for your password
The system will then show you the orphaned packages it wants to remove.
If you want to get rid of them (why not? You're not using them) hit 'Y'
When the autoremove is finished, close the terminal window.

---

### Post by bigbrovar on 2008-09-01
> **Cheesehead said:**
> My Synaptic doesn't have a filter to find orphaned packages.

If yours doesn't, 
then open a Terminal window (Accessories --> Terminal) and use the command:
```
sudo apt-get autoremove
```
The system will prompt you for your password
The system will then show you the orphaned packages it wants to remove.
If you want to get rid of them (why not? You're not using them) hit 'Y'
When the autoremove is finished, close the terminal window.

he is right

---

### Post by quibbler on 2008-09-01
> **Cheesehead said:**
> My Synaptic doesn't have a filter to find orphaned packages.

If yours doesn't, 
then open a Terminal window (Accessories --> Terminal) and use the command:
```
sudo apt-get autoremove
```
The system will prompt you for your password
The system will then show you the orphaned packages it wants to remove.
If you want to get rid of them (why not? You're not using them) hit 'Y'
When the autoremove is finished, close the terminal window.
Open synaptic-go to setting-filters=make a new filter-call it Orphaned-tick the 
only the orphaned under other. 

regards quibbler

---

