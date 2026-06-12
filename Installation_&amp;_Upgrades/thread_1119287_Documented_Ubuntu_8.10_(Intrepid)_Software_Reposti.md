---
title: "Documented Ubuntu 8.10 (Intrepid) Software Repostitory SourceList"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by TweetyBird777 on 2009-04-07
from /etc/apt/sources.list

####### Setup:
#
# Step 1
#
# Go to Applications -> Accessories -> Terminal
# Execute all gpg and wget commands in the Terminal
#
# Go to System -> Administration -> Software Sources
# Go to Authentication tab
# Load any text files contains a PGP public key using the Import Key File... button.
#
# Step 2
#
# Go to Applications -> Accessories -> Terminal
#   cd ~
#   sudo cp /etc/apt/sources.list /etc/apt/sources-backup.list
#   sudo gedit /etc/apt/sources.list
#     - replace the existing sources.lst file with the contains of this file
#
####### To restore the original sources.list file:
#
# Go to Applications -> Accessories -> Terminal
#   sudo cp /etc/apt/sources-backup.list /etc/apt/sources.list
#
###############################################################################################################
  
 
######### Official Intrepid Repositories #########
 
####### Main
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted
 
####### Updates
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
 
####### Universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe
 
####### Multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
 
####### Backports & Proposed
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports restricted main multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
 
####### Partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
 
####### Security
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-security multiverse

###############################################################################################################
  
 
################## Other Repositories ##################

####### Wine ([http://www.winehq.org/](http://www.winehq.org/))
#
# Method 1 - Use gpg commands to authenticate repository
#
# gpg --keyserver subkeys.pgp.net --recv 5A9A06AEF9CB8DB0
# gpg --export --armor 5A9A06AEF9CB8DB0 | sudo apt-key add -
#
# Method 2 - Use wget command to authenticate repository
#
# wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
#
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main
deb [http://ppa.launchpad.net/ubuntu-wine/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ubuntu) intrepid main
# installing Wine: sudo aptitude update && sudo aptitude install wine

####### Wine-Doors ([http://wddb.wine-doors.org/](http://wddb.wine-doors.org/))
#
# Method 3 - Load PGP key manually to authenticate repository
#
#  -----BEGIN PGP PUBLIC KEY BLOCK-----
#  Version: SKS 1.0.10
#  
#  mI0ESYH+FAEEALHuCHrCQSs/Gc6f857vbbxvBkGW5TFKMaYjmIovO1UGvIT2FLSmr03rou10
#  JhAugN9Khni8ojQETzIT9cmneH7HgJs294xuuurpW8mBjMumlpAR9t6mW/wzlCj7TGEd4a8q
#  hZh7P6TJhbAn4MT7eam8mI0Rw5V9rFri8oXFPU6XABEBAAG0KExhdW5jaHBhZCBQUEEgZm9y
#  IFdpbmUtRG9vcnMgRGV2ZWxvcG1lbnSItgQTAQIAIAUCSYH+FAIbAwYLCQgHAwIEFQIIAwQW
#  AgMBAh4BAheAAAoJEEml8p2BrJmABR4EAKa9OP22Mapx0bs7LJhAjMR1UcqaZ+0E8T3aR/CM
#  k0VzgabzwCjABBrv7+M9ywI5WWCm2eCkSD3Y8SncUG7SE2UbnYKZcA7NLpXMPgqFy2U9fAGk
#  snmMipQ2USMcV+LzG+Fer9zV7Mo2a5ZbP3Gea0+O81NJFsqmtztV3P3yR8Ns
#  =YOW7
#  -----END PGP PUBLIC KEY BLOCK-----
#
# Save the above key in a text file. 
# Go to System -> Administration -> Software Sources
# Go to Authentication tab
# Load the text file by pressing the Import Key File... button.
#
deb [http://ppa.launchpad.net/wine-doors-dev-team/ppa/ubuntu](http://ppa.launchpad.net/wine-doors-dev-team/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/wine-doors-dev-team/ppa/ubuntu](http://ppa.launchpad.net/wine-doors-dev-team/ppa/ubuntu) intrepid main

####### MoBlock ([http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)  [http://mobloquer.foutrelis.com/](http://mobloquer.foutrelis.com/))
# gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
# gpg --export --armor 9072870B | sudo apt-key add -
# sudo aptitude update
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) intrepid main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) intrepid main

####### Compiz ([http://www.compiz-fusion.org/](http://www.compiz-fusion.org/))
# PPA - no GPG
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main
# installing Compiz: sudo aptitude update && sudo aptitude install compiz compizconfig-settings-manager

####### Ubuntu Tweak ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/))
# gpg --keyserver subkeys.pgp.net --recv 6AF0E1940624A220
# gpg --export --armor 6AF0E1940624A220 | sudo apt-key add -
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
# installing Ubuntu Tweak: sudo aptitude update && sudo aptitude install ubuntu-tweak

####### Open Office ([http://www.openoffice.org/](http://www.openoffice.org/))
# gpg --keyserver subkeys.pgp.net --recv 60D11217247D1CFF
# gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

####### Abiword ([http://www.abisource.com/](http://www.abisource.com/))
# PPA - no GPG
deb [http://ppa.launchpad.net/abiword-stable/ubuntu](http://ppa.launchpad.net/abiword-stable/ubuntu) intrepid main

####### Back Track ([http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)  [http://wiki.remote-exploit.org/index.php/Main_Page](http://wiki.remote-exploit.org/index.php/Main_Page))
# wget -q [http://repo.offensive-security.com/dist/bt4/binary/public-key](http://repo.offensive-security.com/dist/bt4/binary/public-key) -O- | sudo apt-key add 
deb [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/

####### Remastersys ([http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html))
# no GPG
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/
# installing Remastersys: sudo aptitude update && sudo aptitude install remastersys

####### Virtualbox ([http://www.virtualbox.org/](http://www.virtualbox.org/))
# wget -q [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc) -O- | sudo apt-key add -
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

####### Medibuntu ([http://www.medibuntu.org/](http://www.medibuntu.org/))
# wget -q [http://fr.packages.medibuntu.org/medibuntu-key.gpg](http://fr.packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid non-free free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
# installing Medibuntu: sudo aptitude update && sudo aptitude install libdvdcss2

####### GnomeDo ([http://do.davebsd.com/wiki/index.php?title=Main_Page](http://do.davebsd.com/wiki/index.php?title=Main_Page))
# gpg --no-default-keyring --keyring /tmp/gnome-do.keyring --keyserver keyserver.ubuntu.com --recv A5D19FDCAA6ABB440CD3464628A8205077558DD0
# gpg --no-default-keyring --keyring /tmp/gnome-do.keyring --export --armor  A5D19FDCAA6ABB440CD3464628A8205077558DD0 | sudo apt-key add -
# rm /tmp/gnome-do.keyring
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
# installing GnomeDo: sudo aptitude update && sudo aptitude install gnome-do

###############################################################################################################
 
 
####### Notes

# The repository components are:
#
#    *      Main - Officially supported software.
#    *      Restricted - Supported software that is not available under a completely free license.
#    *      Universe - Community maintained software, i.e. not officially supported software.
#    *      Multiverse - Software that is not free. 
#
# see also [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

# If you get error message:
# 
# W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures 
# couldn't be verified because the public key is not available: NO_PUBKEY 
# FC66403D8670A035
#
# Use this template
#
#    gpg --keyserver subkeys.pgp.net --recv KEY
#    gpg --export --armor KEY | sudo apt-key add -
#
# Replace the word "KEY" with the numbers in the eror message. 

#
# run gpg commands in terminal
#

# what are backports/proposed/updates/security repositories?
#
# see [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

