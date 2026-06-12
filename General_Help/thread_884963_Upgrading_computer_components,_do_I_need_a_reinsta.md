---
title: "Upgrading computer components, do I need a reinstall?"
date: 2008-08-09
forum: General Help
---

### Post by lobsteri on 2008-08-09
I'm planning to upgrade my Ubuntu box with new hardware and only the old hard drive will survive. Processor will go amd 1800+ to 2400+, memory will increase from 700meg to 1gb and the video card will go from accent nvidia mxsomething to ati radeon 9800pro. Obviously also the motherboard will be changed.

The question is, that do I need to make some preparations before chancing the parts or do the Ubuntu work fine after changing the parts? Of course I have to install new video card drivers, but other than that? Or should I backup my home-directories and reinstall everything? If yes, is there anything other to backup before?

---

### Post by jerome1232 on 2008-08-09
I would backup my /home directories and try it. It should work but if there are wrinkles (massive hardware changes you never know) you can fall back to reinstall and restore from backups.

---

### Post by Kevbert on 2008-08-09
A re-install would be the best bet.  If you want to save a list of all installed packages, use the terminal command
```
sudo dpkg --get-selections > packback.txt
```
This will save a list of all packages in the file 'packback.txt' in your current directory (normally home).
When you want to re-install all packages run the following
```
sudo dpkg --clear-selections
dpkg --set-selections < packback.txt
sudo aptitude install dselect-upgrade

```
Hopefully the PC will then download and install all your old packages.

---

### Post by silkstone on 2008-08-09
I'd do a new install. Also perhaps look at an Nvidia card instead of ATI - I think they do generally work better with Linux although ATI have improved their support.

---

### Post by prshah on 2008-08-09
> **lobsteri said:**
> I'm planning to upgrade my Ubuntu box with new hardware 
 do I need to make some preparations before chancing the parts

Nope, ubuntu should work fine with these hardware changes. However, to be on the safe side, make a backup of your entire system using remastersys; it can also create a live CD from your system setup, which you can use to test the new system before you commit your hard drive to it!

---

