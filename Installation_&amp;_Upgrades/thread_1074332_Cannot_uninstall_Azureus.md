---
title: "Cannot uninstall Azureus"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by LobbyDizzle on 2009-02-19
I screwed up bad, I think. I used the instructions here [http://www.ubuntugeek.com/howto-install-vuzeazureus-4004-in-810.html](http://www.ubuntugeek.com/howto-install-vuzeazureus-4004-in-810.html) to try to instal Vuze and Azureus. 

I screwed up the installation and couldn't figure out how to fix it. I then couldn't find a way to uninstall it, and deleted almost all of the files in /usr/share/vuze using sudo rm...  

Now I cannot install using add/remove, my previous method, or synaptic. I'm guessing I need to somehow uninstall all of the associated files. How screwed am I?

---

### Post by halovivek on 2009-02-19
try using this. 
sudo nautilus 
then navigate the where you have moved the Azureus or vuze folder and delete that folder.

---

### Post by LobbyDizzle on 2009-02-19
I've deleted every fold that has either vuze or azurues in it, that command you told me kicks ***. 

I still can't install it, in add/remove, when I try to install vuze it says

[B]Cannot install 'azureus'

This application conflicts with other installed software. To install 'azureus' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/B]

And any other method of installing it still doesn't work.

---

### Post by spike_naples on 2009-03-27
I hate Vuze for Ubuntu.

I would recommend KTorrent or Deluge.

Vuze doesnt even uninstall correctly. To uninstall go to SPM and search for Azureus then choose to completely uninstall all packages to get rid of the remnants of Vuze.

---

