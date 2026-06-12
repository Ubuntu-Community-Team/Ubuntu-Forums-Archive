---
title: "Flash Player Crash is Killing My System"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Tinieblas on 2009-11-01
Installed flash player the other day from the Adobe website. It was working fine and then for some reason one site said that it wasn't working properly. I went back to the Adobe site and downloaded it again and told it to reinstall. It popped up with an error and now it's killing my whole system. I have a big red error sign up by my wireless signal indicator. When I click on it, it opens the synaptic package manager and pops up this error message:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

My only option is to close the window. I tried to run the update manager and I get this error:

Package in inconsistent state
The package 'adobe-flashplugin' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.

Again, the only option is to close the window.

I found a forum that says you're supposed to install flash using this command in the terminal
sudo apt-get install flashplugin-nonfree So I tried that to see if it would fix it and it gives me this:

alan@Alan-Laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

I'm completely out of ideas... If I try to reinstall it from Adobe's site it says that the package is corrupted and can't be opened... HELP!!!

---

### Post by ak331 on 2009-11-01
I have exactly the same errors and I tried every which way and no luck yet.

we do need help in this/ This happened after I upgraded to 9.10. 

I tried looking for cache (1) and could not find it.

---

### Post by Tinieblas on 2009-11-01
> **ak331 said:**
> I have exactly the same errors and I tried every which way and no luck yet.

we do need help in this/ This happened after I upgraded to 9.10. 

I tried looking for cache (1) and could not find it.

Just found someone else with the same problem that fixed it. Try this:

sudo dpkg --configure -a
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
 sudo dpkg-reconfigure adobe-flashplugin --force
 sudo dpkg --purge --force-all adobe-flashplugin
sudo apt-get remove --purge adobe-flashplugin

I haven't tried to reinstall flash player yet, but package manager and everything else works now!

---

### Post by ak331 on 2009-11-01
Thanks a lot. It did help and no more errohttp://ubuntuforums.org/images/smilies/icon_razz.gifrs.:D

---

