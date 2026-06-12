---
title: "Adobe-flashplugin"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by jimgeiser on 2009-11-01
I had troubles with You tube and tried to install Adobe flasplugin 10. It did not finish because it could not find archive. Now I can not install any updates. I find the partial installation in folder var/lib/dbkg/info but I can not get rid of it no mater what I do any suggestions?

---

### Post by Bao2 on 2009-11-01
Follow these steps for Ubuntu 64-bit: (for 32 bit I don't know)

  1. Download Adobe Flash 10 Pre-release for Linux 64-bit 
     to your desktop from this page (the very last link on this page, under the English word):
     [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
     and extract the .so file
  2. Create Mozilla's plugins directory if it doesn't already exist:
      In nautilus: View / Show hidden files and then create:
      .mozilla/plugins
  3. Place the flash .so file in that .mozilla/plugins folder
  4. Restart Firefox

---

### Post by St Nabi on 2009-11-01
I am having the same problem and as my system is 32 bit I am stuck once more !
Will let you know as soon as I hear anything constructive.
Regards
St

---

### Post by Fr33d0m on 2009-11-01
One of the first things many folks do after a new load is to select the fastest repository server in Synaptic (Settings-Repositories-Download From drop down.  If you don't reload and check for errors when you do then you will not be able to load new packages.  So if you've done that, try reload again and make sure there are no errors returned.  If there are, set the server back to Server for United States and reload again.

---

