---
title: "Frostwire deb package after installation"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by blues2use on 2009-06-13
How do I delete the Frostwire deb package from my Desktop after installation? 

If I move it to the trash and delete it or run Computer Janitor and delete it, that breaks Frostwire. 

If I download and reinstall the package, the GDebi Package Installer runs and then reports that Frostwire is already installed.

This happens with the other 2 or 3 apps that I've installed with GDebi as well so I am hanging on to the packages until I know what to do with them.

Your suggestions are most welcome...

Thanks for the help

Incidentally, everything I have installed (whether through Add/Remove, Synaptic, terminal session using apt commands, manual install from archived pacakages or GDebi package installation) and tried (so far) has worked just fine. Had to hunt around the forums and do a little Google work, but, all-in-all, I will only need to run XP for just a couple of software programs that will not run under Wine and for all of my online Poker sites other than Absolute Poker. I actually downloaded and installed Gutenprint from the BZ2 package, followed the directions I found and all went well and fixed a couple of printer issues I was having. So far, I am quite please with ubuntu Jaunty 9.04 all the way around. Still looking at themes and other (not really necessary) things. I'm just 3 weeks in as a noob and I'm keeping a lot of notes for reference.

I've decided that I'm going to go with a dual boot system rather than a Vbox install of XP as soon as my new (and MUCH BIGGER) laptop drive gets here.

---

### Post by zvacet on 2009-06-13
You can make folder inside your home directory and there keep downloaded packages.

---

### Post by bigred562 on 2009-06-16
Maybe I am wrong, but it doesn't matter if you installed it with GDebi. You can still uninstall it with terminal. Just use "sudo apt-get remove frostwire". You can use "sudo apt-get autoremove" to clean up files no longer needed.

I don't know why it would matter if you delete the deb package from your desktop unless it is being installed incorrectly (not necessarily incorrectly by you). The frostwire is seemingly having problems with the new frostwire. The way around this is to use the terminal to install by downloading the file and then typing into your terminal "**sudo dpkg -i frostwire-4.18.0.i586.deb"**

---

