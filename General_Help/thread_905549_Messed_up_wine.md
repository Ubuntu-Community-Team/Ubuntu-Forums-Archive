---
title: "Messed up wine"
date: 2008-08-30
forum: General Help
---

### Post by jcr1 on 2008-08-30
Hi,

I installed wine.

I tried to install photoshop but realised I should have installed other things first so tried to uninstall photoshop, using the wine uninstaller. This kept failing, so i just deleted ~/.wine and also did aptitude remove wine.

But wine still appears in my menus. So does bloody photoshop.

How can i get rid of ALL traces that wine and photoshop were ever on the computer so I can start afresh?

Many thanks.

---

### Post by mack27 on 2008-08-30
i have thye same problem. i've uninstalled two applications from wine but they still appear on the list. why?

---

### Post by mrtomservo on 2008-08-30
Did you try the 'purge' option with aptitude?  That might help.  Also never hurts to run 'clean' and/or 'autoclean'.

---

### Post by jcr1 on 2008-08-30
how do i use the purge option?

---

### Post by Ms_Angel_D on 2008-08-30
Right click on "Applications" and then select "Edit Menus" You can go in and delete the menu entries. Just right Click on the entry you wish to remove and select "Delete".

---

### Post by Marshal0505 on 2008-08-30
I usually solve this by manually removing the link to the program in ~/.local/share/desktop-directories

the purge option mentioned above me is done by opening a terminal and typing

```
sudo aptitude purge wine 
```

---

### Post by markharding557 on 2008-08-30
> **MetalHellsAngel said:**
> Right click on "Applications" and then select "Edit Menus" You can go in and delete the menu entries. Just right Click on the entry you wish to remove and select "Delete".

this is the way to get rid of wine menu entries use the menu editor

---

### Post by jcr1 on 2008-08-31
What's going on here?

```

jonrserv@jcrserver:~$ sudo aptitude purge wine
[sudo] password for jonrserv: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

Should I do a aptitude remove first, then purge?

---

### Post by mrtomservo on 2008-08-31
Well, I think 'purge' is essentially 'remove' with the deletion of the config files that come with the package, so no, purge should work fine.  I'd image that if wine is removed already that the purge won't work.  This is getting out of my shallow depth of knowledge. :(  I'm just pulling this out of my rear, but perhaps you need to reinstall wine, then purge it.  Sorry I can't be more help.

---

### Post by Sycron on 2008-08-31
Or try restarting X. Press *Ctrl+Alt+Backspace* .

---

