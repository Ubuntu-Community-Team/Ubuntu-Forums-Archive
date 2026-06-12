---
title: "Where does the list of installed apps (from the &quot;Applications&quot; menu) live?"
date: 2008-07-23
forum: General Help
---

### Post by mjpatey on 2008-07-23
Hi,

Just blew up the Ubuntu install I've had for about a year and a half (due to power outage in a storm) and have tried fscking to no avail.  Most of the data is accessible from a live CD, and I've copied it to an external HDD.

Once the new install is up and running, I'm going to want to install a lot of apps that I've relied on.  Is there some directory where I can find a file that lists all installed apps (or even just the ones that appear in the "Applications" menu)?  Even now, I can't remember the names of some of my most-used apps.

Thanks for any suggestions you may have!

-Mark

---

### Post by phidia on 2008-07-23
Have you tried [System Rescue CD]("http://www.sysresccd.org/Main_Page") on that install. Myself I like to try everything before abandoning an install.
> dpkg --list Should give you a list of your apps. See [this web page]("http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html") too. You might need to mount & chroot into that install.

---

### Post by Elfy on 2008-07-23
/usr/share/menu appears to have everything in there that appear in my menus - or have done since I installed hardy

---

### Post by drs305 on 2008-07-23
> **mjpatey said:**
> 
Once the new install is up and running, I'm going to want to install a lot of apps that I've relied on.  Is there some directory where I can find a file that lists all installed apps (or even just the ones that appear in the "Applications" menu)?  Even now, I can't remember the names of some of my most-used apps.

Thanks for any suggestions you may have!

-Mark

Too late to help you this time, but once you get all the apps reinstalled on your system you can run these commands to save a list of installed apps. Change the path/name to suit yourself:

```
sudo dpkg --get-selections >~/Desktop/installed-pkgs
```	
To install from file list:
```
sudo dpkg --clear-selections
dpkg --set-selections <~/installed-pkgs 	
sudo apt-get dselect-upgrade 

```

I run a backup weekly and run the 'sudo dpkg --get-selections' command to make sure I'll be able to restore all my apps should catastrophe to my drive occur.

---

### Post by mjpatey on 2008-07-23
Awesome.  Thanks, everyone!  There's always more than one way to skin a cat in Ubuntu.  Love it!

-Mark

---

### Post by Dragonbite on 2010-02-17
> **drs305 said:**
> Too late to help you this time, but once you get all the apps reinstalled on your system you can run these commands to save a list of installed apps. Change the path/name to suit yourself:

```
sudo dpkg --get-selections >~/Desktop/installed-pkgs
```	
To install from file list:
```
sudo dpkg --clear-selections
dpkg --set-selections <~/installed-pkgs 	
sudo apt-get dselect-upgrade 

```

I run a backup weekly and run the 'sudo dpkg --get-selections' command to make sure I'll be able to restore all my apps should catastrophe to my drive occur.

Perfect, this is just what I was looking for.

Is there a GUI that does this, like part of Synaptic? I tried the Generate Script menu selection but it did nothing.

---

### Post by drs305 on 2010-02-18
> **Dragonbite said:**
> Perfect, this is just what I was looking for.

Is there a GUI that does this, like part of Synaptic? I tried the Generate Script menu selection but it did nothing.

If you are referring to the "Generate Script" part of the Synaptic way of saving the list of installed apps, part of it is not intuitive.  After you select "File, Save Markings" in Synaptic, you have to select the "Save full state, not only changes" or the generated script will be empty. If you tick the "Save full" option, it should save the complete list, which you can then import into another install.

---

