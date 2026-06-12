---
title: "New installation - no &quot;root&quot; option - help??"
date: 2006-01-01
forum: Installation &amp; Upgrades
---

### Post by andyfg on 2006-01-01
I've just downloaded the latest Ubuntu version and installed it on a spare partition to try it out. Looks a really good system - but I've hit on a snag which I can't get round.

Any help from the Ubuntu Linux Community would be greatfully appreciated!

Need to set "root" password to enable me to do routine admin, configuration and load new packages, etc. However no "set root password" option came up during the entire installation, so I repeated the process again - re-formatting the entire partition and re-installing. Same problem I'm afraid.

Any ideas how to remedy the situation? (I already run Suse Linux 10.0 on another partition so can access the Ubuntu files if I need to in order to correct configuration files.)

Seems a pretty basic problem, but am curious why the installer hasn't offered the "root" password option in the first place.

---

### Post by Susana on 2006-01-01
The root password is, by default, the same password of the first user you created. Also, if you're new to ubuntu here is a great guide to get you started: [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

---

### Post by snellgrove on 2006-01-01
Ubuntu doesn't really use 'root' 

you dont SU, do your root stuff etc etc

what you do is if you need to access a root thing, it'll pop up a password box. stick the one of your main account in there, and you can do the root stuff and when your done your back as anormal user.

in terminals, you use the "sudo" command, like

sudo hdparm -d1 /dev/hdd

it'll ask for the password, you type it in.. it does the command, and your dropped back to a normal account again

promotes good security as your only root for as long as you need to do that command :)

---

### Post by Sutekh on 2006-01-01
[QUOTE=Susana]The root password is, by default, the same password of the first user you created. Also, if you're new to ubuntu here is a great guide to get you started: [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)[/QUOTE]

Not quite true, the first password is the 'sudo' password that you should use for administration.  The root account has not been enabled/activated.
```
sudo passwd root
```
Will accomplish this.  The password you set here is the root password, but you should *never* need it, and you should *never* need to enable the root account, just use sudo.

---

### Post by andyfg on 2006-01-01
Thanks very much - works a real treat!

Kind regards. Andyfg.:D

---

### Post by Jeff12088 on 2006-01-01
Yup, you should never need to use it, but if you want

sudo -s

and enter password and you'll be in root

---

