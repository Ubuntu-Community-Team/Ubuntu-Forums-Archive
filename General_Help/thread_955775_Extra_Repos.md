---
title: "Extra Repos?"
date: 2008-10-22
forum: General Help
---

### Post by A1len on 2008-10-22
I was just wondering if anyone had some good extra repository lists that they wouldn't mind posting under this thread.

thx

---

### Post by mgmiller on 2008-10-22
These are the only 2 I have needed in a long time.  One for picasa and the other for medibuntu for DVD and win32 codecs:

```
## Google Picasa for Linux repository
## GPG key   wget -q -O - http://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
deb http://dl.google.com/linux/deb/ stable non-free

## Medibuntu - Ubuntu 8.04 "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
## GPG key  wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free

```


You will notice as part of this I have given the commands to get the gpg keys as well.  These are run from terminal.

---

### Post by caleb12 on 2008-10-22
Mine sources.list, is attached - injoy!


```
####################################################################################################
####		Determining the fastest server:							####
####	In synaptic, settings, repositories: select Download From, and then 			####
####	Find best server									####
####################################################################################################
####                    How to Add GPG keys                                     		####
####################################################################################################
##              gpg --keyserver subkeys.pgp.net --recv KEY                        		  ##
##              gpg --export --armor KEY | sudo apt-key add -                     		  ##
##                                                                                		  ##
## If you have a gpg key URL use (replace URL with the key address):              		  ##
##                                                                                		  ##
##              wget URL --quiet -O - | sudo apt-key add -                        		  ##
##                                                                                		  ##
## If you have a gpg key file use (replace FILE with the key file):               		  ##
##                                                                                		  ##
##              sudo apt-key add FILE                                             		  ##
####################################################################################################	
## deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted	  ##
####################################################################################################
####			Intrepid Main Repos							####
####################################################################################################
deb http://mirror.anl.gov/pub/ubuntu/ intrepid main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid restricted main multiverse universe
deb http://mirror.anl.gov/pub/ubuntu/ intrepid-updates main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid-updates restricted main multiverse universe
deb http://mirror.anl.gov/pub/ubuntu/ intrepid universe
deb http://mirror.anl.gov/pub/ubuntu/ intrepid-updates universe

deb http://mirror.anl.gov/pub/ubuntu/ intrepid multiverse
deb http://mirror.anl.gov/pub/ubuntu/ intrepid-updates multiverse

deb http://mirror.anl.gov/pub/ubuntu/ intrepid-security main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid-security restricted main multiverse universe
deb http://mirror.anl.gov/pub/ubuntu/ intrepid-security universe
deb http://mirror.anl.gov/pub/ubuntu/ intrepid-security multiverse

####			Backports								####
deb http://mirror.anl.gov/pub/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid-backports main restricted universe multiverse

####			Proposed								####
deb http://mirror.anl.gov/pub/ubuntu/ intrepid-proposed restricted main multiverse universe
deb-src http://mirror.anl.gov/pub/ubuntu/ intrepid-proposed restricted main multiverse universe

####			Canonincal 								####
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner
####################################################################################################
####			My Repos								####
####################################################################################################

####			Network Manager								####
deb http://ppa.launchpad.net/asac/ubuntu intrepid main
deb-src http://ppa.launchpad.net/asac/ubuntu intrepid main
deb http://ppa.launchpad.net/network-manager/ubuntu intrepid main
deb-src http://ppa.launchpad.net/network-manager/ubuntu intrepid main

####			Compiz Repos								####
deb http://ppa.launchpad.net/compiz/ubuntu intrepid main
deb-src http://ppa.launchpad.net/compiz/ubuntu intrepid main

####			Wine Repos								####
deb-src http://wine.budgetdedicated.com/apt hardy main
deb http://wine.budgetdedicated.com/apt hardy main
 
####			Firefox & Pidgin							####
deb http://ppa.launchpad.net/pidgin-developers/ubuntu hardy main
deb http://ppa.launchpad.net/mozillateam/ubuntu intrepid main

####			Ubuntu Tweak								####
deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu intrepid main

####			Medibuntu Repos								####
deb http://packages.medibuntu.org/ intrepid free non-free
deb-src http://packages.medibuntu.org/ intrepid free non-free

####			Skype Repos (using Medibuntu packages instead)				####
# deb http://download.skype.com/linux/repos/debian stable non-free

####			Terminator - end all be all of terminals				####			
deb http://ppa.launchpad.net/gnome-terminator/ubuntu intrepid main

####################################################################################################
####			Other Repos and packages - generally unused or experimental		####
####################################################################################################

####			Tormod Volden - latest ATI drivers					####
####	Generally very unstable, use only as needed, pinned old packages			####
##deb http://ppa.launchpad.net/tormodvolden/ubuntu intrepid main
##deb-src http://ppa.launchpad.net/tormodvolden/ubuntu intrepid main

#### 			Project Neon for Hardy							####
# deb http://ppa.launchpad.net/project-neon/ubuntu hardy main

####			KDE 4 for Hardy 							####
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
```

---

### Post by A1len on 2008-10-22
Thanks to both of you guys!

---

