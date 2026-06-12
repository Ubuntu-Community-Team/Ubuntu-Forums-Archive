---
title: "Non destructive install?"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by maxina on 2009-09-09
Hi, 

I am trying to fixed a completely hosed 9.04 installation. Can I re-install using an install disk w/o blowing away the data? Does the installer give this option? I did an in-place upgrade to 9.04 and when I rebooted, I had no UI. My command line skills are a bit poor, but I would like to salvage this thing without having to scrape off the data first.

Any Ideas where I can go from here?

Thanks, 

Andrew

---

### Post by earthpigg on 2009-09-10
what, exactly, would you like to recover?

your data, such as mucic and pictures? boot from the live-cd and copy them to an external hard drive or somewhere else.

your settings for programs such as firefox and pidgin? from the live-cd, navigate to your /home on that hard drive and copy all the hidden files and folders that start with a period over to an external hard drive. copy them back to your new home folder once ubuntu is reinstalled.

when you reinstall stuff on your fresh install, the programs will find those hidden dotfiles and use those settings.

an exact image of that install... well, this would bring your unfortunate problems along with it, so i assume this is not what you want.

---

### Post by QIII on 2009-09-10
First -- Do you have an Intel graphics chipset?

Answer that first.  If not, we'll go to the following.  If you do, this will take a sharp right turn.

The virtual gremlins may have interfered with the transmission from the server and some packet errors may have been unrecoverable.  In that case you might have been left with a number of broken packages.  Were you watching the details of the upgrade, or did you have a cup of coffee?  I'd think the upgrade would have puked, but you never know.

Heed earthpigg's advice above about saving your data files.  (And, although it goes without saying, next time remember to back up your really important files before you do anything radical...)  Earthpigg sounds like a Marine that learned** not** to pee on his hands.  Old joke.
 
 Although a clean install is always preferable to an update, here's a possible alternative.  You might (and I say "might") be able to use the command line to try to clean things up.
 
 At the command line, type
 
 ```
sudo apt-get update && apt-get upgrade
``` DO NOT DO NOT DO NOT use "dist-upgrade" because you may end up going from a botched Jaunty upgrade to an even more botched upgrade to the Karmic Alpha.

---

