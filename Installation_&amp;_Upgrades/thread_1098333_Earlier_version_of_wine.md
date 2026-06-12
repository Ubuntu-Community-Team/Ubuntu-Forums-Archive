---
title: "Earlier version of wine?"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by comradejanus on 2009-03-16
Hi, im trying to return to an earlier version of wine. I currently have version 1.1.1.7 of wine installed and have just downloaded version 1.1.1.5 and want to install it, as I hear it runs steam apps like CSS better. I've opened the folder but don't quite know what to do.

Might be a very stupid question, but im very new to linux, but how to I install it? I'm guessing I have to uninstall it first. 

I'm running ubuntu 8.10.

Thanks in advance.

---

### Post by Partyboi2 on 2009-03-17
Remove your current version of wine either by Add/remove (Applications>Add/Remove) or from the terminal (Applications Accessories>Terminal)
```
sudo apt-get remove wine
```
Then download the [[COLOR=Blue]wine 1.1.1.5 deb[/COLOR]]("http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.15%7Ewinehq0%7Eubuntu%7E8.10-0ubuntu4_i386.deb") then double click on it to install it. Once it is installed you may need to go to Synaptic (System>Admin>Synaptic Package Manager) and search for 'wine' then use the lock version option (Package>Lock Version) so that it will not get upgraded.

---

