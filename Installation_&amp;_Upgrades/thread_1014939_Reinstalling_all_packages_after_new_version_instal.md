---
title: "Reinstalling all packages after new version install"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2008-12-18
Hi,
I'm on Kubuntu Intrepid with quite a lot of additional packages installed (besides those installed during the initial installation). Having a separate /home partition, I fresh reinstall to each new version (rather than upgrade).

Is there a utility, or script, which records all additional installed packages (prior to installing the new version), and after the new install, automatically:

a. Modifies the new sources.list
b. Installs the latest version of all the packages that were installed prior to the fresh system installation.

Thanks a lot upfront !

Michael Badt

---

### Post by Diabolis on 2008-12-18
For that purpose I keep a script with a list of all the packages that I have installed. So in every new install I just run the script.

---

### Post by ajgreeny on 2008-12-18
Short of copy/paste for the sources.list file, I don't know how you could do that, but for the list of installed packages use the following:-

HowTo: Create a list of installed packages

I found out how to do this recently and thought it might be helpful to some people. To output this information to a file in your home directory you would use, ```
dpkg --get-selections > installed-software
```
And if you wanted to use the list to reinstall this software on a fresh ubuntu setup, ```
dpkg --set-selections < installed-software
```
followed by ```
dselect
```

Have a look at **man dpkg** in terminal for more info.

---

### Post by unutbu on 2008-12-18
Edit: Oops... Too slow! :)

```
dpkg --get-selections > package-list     # dumps a list of all packages 

```
Save package-list on to a safe partition or something like a USB thumb drive.
Reinstall your operating system
Copy package-list to someplace Ubuntu can read.
```

sudo dpkg --set-selections < package-list    # sets package selections
sudo apt-get update                          # makes apt aware of available packages
sudo apt-get dselect-upgrade                 # installs/upgrades the selections
```

---

### Post by mibadt on 2008-12-19
Bless you all !!
Thanks a bundle .

Michael Badt

---

