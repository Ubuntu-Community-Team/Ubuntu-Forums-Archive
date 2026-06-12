---
title: "Migrating data to new installs"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Tobywuk on 2009-04-19
Hello,

As new versions of ubuntu get released on a regular basis, how do you deal with migrating all your data to your new installs?

Is it possible to just simply back up your home directory, then when you do a new install just restore the users home directory to the new installed system?  Would this cause any problems or is it only user data stored in the home directory?

---

### Post by Rocket2DMn on 2009-04-19
Typically people just upgrade their systems using the Update Manager, which means you don't have to reinstall the system.  If you do want to do a fresh install, you should just back up your files to an external hard disk first.  If all your files are in your home directory, that would be all you need to back up.  However, remember that you will need to re-install all your programs if you do a fresh install.  If you are simply going to install the next version, I recommend doing an upgrade rather than a fresh install.

---

### Post by knattlhuber on 2009-04-19
The best way to migrate data to a new install is by creating a separate partition for /home during a fresh install.
Instructions for creating a separate /home partition if you already installed Ubuntu without a /home partition can be found here:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

What I also did to facilitate migration, is creating a post-installation script that automates re-installation of my favourite applications.
It looks a bit like this (shortened, obviously):

```
#! /bin/bash

# Add Medibuntu repo
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

sudo apt-get update

# Multimedia
sudo apt-get install -y alsa-oss faac faad flashplugin-nonfree

# Me own stuff
sudo apt-get install -y amarok
sudo apt-get install -y build-essential
sudo apt-get install -y basket

# Remove exotic fonts
sudo apt-get remove -y ttf-arphic-uming
sudo apt-get remove -y ttf-thai-tlwg

# Create mountpoints
sudo mkdir /media/HP250

# Allow concurrent start of startup scripts
sudo sed 's/CONCURRENCY=none/CONCURRENCY=shell/' -i /etc/init.d/rc

# Grub menu 1 sec timeout
sudo sed 's/^\(timeout.*\)[0-9]\{1,2\}/\11/' -i /boot/grub/menu.lst

# Disable OOo splash screen
sudo sed 's/Logo=1/Logo=0/' -i /etc/openoffice/sofficerc

```

---

