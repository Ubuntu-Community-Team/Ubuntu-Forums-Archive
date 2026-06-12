---
title: "Won't install packages?"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by flummoxed on 2006-01-07
Hey, I just got a new 80GB SATA western digital hard drive to install Ubuntu 5.10 on. I already have an IDE 80gb drive with XP professional installed on my computer. So I formatted and installed Ubuntu on the new drive, and all seemed to be going well. But once I rebooted and it was installing more of the packages, it gave me an error at 17% and said that not all of the packages could be properly installed. I had nothing else to hit but continue, so continue I did. Now Ubuntu will boot, but I can't get to the GUI. All I get is a prompt to enter my username and password, then a command line.

Here are my system specs:
AMD Sempron 2400+
1 GB dual Channel DDR-400 
Sapphire Radeon 9800 pro
Western Digital 80GB IDE
Western Digital 80GB S-ATA
Nf7-S2 motherboard

Any help would be appreciated. :D

EDIT

Hmm, I just came back to the computer, and it's somehow made it into the GUI. I'm still not sure what happened, but apparently it's at least halfway installed. I'm posting from Ubuntu right now. What should I do to make sure everythings installed?

---

### Post by dsjas297 on 2006-01-07
If you want a GUI, at the command line, type 

```
sudo apt-get install gnome
```

That should install GNOME display manager (and all packages it requires) on your computer.

---

### Post by imranj on 2006-01-07
Try KDE too;)

---

### Post by flummoxed on 2006-01-07
When I tired your command to install Gnome, it told me it couldn't find anything to install it from. I think my whole problem is all the packages didn't install correctly. What should I do? Should I reinstall Ubuntu?

I can't get past the prompt again. I don't know what appened before to get me into the GUI...

---

### Post by az on 2006-01-07
From the command line, tell it to fix any broken or half-installed packags:

sudo apt-get -f install

it may tell you to 

sudo dpkg --configure -a

If, do , do that.

If it cannot install the packages because they are corrupted (unlikely) You can just use the online repositories instead of the cdrom

You need to edit the /etc/apt/sources.list file and comment out the first line.

(Add a # at the beginning)

sudo nano /etc/apt/sources.list
or
sudo gedit (from gnome)

and then


sudo apt-get update
sudo apt-get install ubuntu-desktop

---

### Post by flummoxed on 2006-01-07
Finally, Ubuntu is working right. :D

I downloaded a new .ISO file, this time for the CD. Before I was trying to install off the live DVD. I reformatted and reinstalled, but then the Grub Setup froze. So I restarted, and tried again. Lo and behold, it installed! 

The lesson here is perserverance... It might not seem like it's going to work, but if you just keep trying, you just might get lucky! :D

---

