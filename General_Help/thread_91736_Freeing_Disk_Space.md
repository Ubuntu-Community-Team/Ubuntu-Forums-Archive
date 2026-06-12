---
title: "Freeing Disk Space"
date: 2005-11-17
forum: General Help
---

### Post by Czar on 2005-11-17
Dear All,

I am using Ubuntu on a fairly legacy laptop w/ only a 2GB hard drive.  After the installation and removing a few unused applications I am left with only 192MB.  

Help, what would you recommenced being removed to create at least 500MB of free space.

---

### Post by SickTwist on 2005-11-18
Remove OpenOffice.org2. If you need a spreadsheet and/or word processor I recommend Gnumeric and AbiWord.

You can also run this command to remove all of the package files that were used temporarily to install everything on your system:

sudo apt-get clean

Basically it just clears the package cache and will not affect anything that is already installed.

---

### Post by Chickenmonger on 2005-11-18
You could also use a smaller window manager like XFce instead of Gnome.

Try du -h at a shell prompt to see the relative sizes of the directories under the current path. That might help pin down what's taking up so much HD space.

---

### Post by SickTwist on 2005-11-18
To add to Chickenmonger's suggestion, these piped commands will sort the file sizes and display the 20 largest files and directories under the current path:

du -a | sort -n | tail -20

---

### Post by Czar on 2005-11-18
Thanks for all these suggestions!  They are the exact type of things I was looking for. ;-)

---

### Post by metoo on 2005-11-19
Install localepurge which will delete man pages and locales for other then your prefered language.

Use synaptic to check the fonts, I had bengalie(y?) and other fonts that I will never need.

Then check out /usr/share/doc
208MB here, scan the entries and keep what you think you might need. You can always re-install packages:
apt-get install --reinstall package-name

---

