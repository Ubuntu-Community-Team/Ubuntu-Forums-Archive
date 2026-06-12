---
title: "Changing computer: how to make it an easy thing."
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by polvoazul on 2009-07-21
Everybody changes computers now and then. There are certain tasks, though, that are a bit boring, installing the same pluggins for the clean firefox, reediting .bashrc re-adding the sources for apt...

I suggest 2 things, one for short term and the other for long term:


:confused:1- Does someone knows how to print a (new-line or space separated) list of mannually installed programs on apt? this would be a good way to reinstall many packages VERY conveniently. just type

 sudo apt-get install <copy list here>

:KS 2- This is my long term suggestion, maybe we couold build a small ap that would backup all of these kinds of data in a package, then we could simply open it up again on the new PC and let it do these things for you (reinstall packages, recover bookmarks, plugins, keybindings, wall paper, preferences etc...). comeback 1 hour later, and your new PC is exactly your old one but with that furious processor you dreamed:P (and payed:() for.

what do you think? Show me some comments, anything is apreciated, and PLEASE try to answer the 1st one.

Adious

---

### Post by Aearenda on 2009-07-21
For part 1, see [http://blog.hanno-stock.de/archives/50](http://blog.hanno-stock.de/archives/50)

On 2, you probably wouldn't want it to be exactly the same, because the hardware is different - think about screen resolution, for example. Many people keep their /home folder in a separate partition from the operating system so that they can retain it across new installations.

---

### Post by drs305 on 2009-07-21
> **polvoazul said:**
> 
:confused:1- Does someone knows how to print a (new-line or space separated) list of mannually installed programs on apt? this would be a good way to reinstall many packages VERY conveniently. just type

 sudo apt-get install <copy list here>



You can create a list of installed packages with:
```

sudo dpkg --get-selections | grep -v "deinstall&#8221; >$HOME/Desktop/installed-packages 

```

Transfer the file to the new computer. To restore the list:
```

sudo apt-get update
sudo dpkg --clear-selections  # Read about this in "man dpkg".
sudo dpkg --set-selections <$HOME/Desktop/installed-packages 	
sudo apt-get dselect-upgrade

```

Synaptic also now has the capability of exporting and importing installed packages under the File menu option.

---

