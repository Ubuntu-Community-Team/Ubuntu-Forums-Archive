---
title: "Cannot install win32/VLC/media player! plz help"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by kunaly2k on 2009-03-11
Friends i am a newbie to linux and downloaded Xubuntu intrepid ibex but was frustrated to extent when i came to know that i cannot play mp3's and videos! After some research i downloaded the win32 and some lib codecs and vlc player & media player in .deb format but whenever i try to install any of them it shows a message "Dependency not satisfied" :-( plz friends help me out with this thing by any helpful links or softwares! PLZ!
P.S. My pc is not connected to net so please guide me through the offline method of installation. Thanks

---

### Post by rahulkumarc on 2009-03-11
Hi,

First since you are on Ubuntu dont worry about win32 anymore :D

Next try few of these below:

do you have internet connection:
Yes - run sudo apt-get install vlc - in a terminal & follow instructions.
Alternatively click applications -> System -> synaptics package manager 
under that quick search for vlc, right click with the mouse and click mark for install and then click apply.

No - **THIS IS NOT A VERY NICE WAY or SUGGESTED EITHER** download the following deb packages from [http://archive.ubuntu.com/ubuntu/pool/universe/](http://archive.ubuntu.com/ubuntu/pool/universe/)

libdvbpsi4 libdvdnav4 libiso9660-4 libsdl-image1.2 libtar libvcdinfo0 libvlc0 libxosd2 mozilla-plugin-vlc vlc vlc-nox

OR

go to a firend with internet connection and ubuntu install vlc on their system and copy the required deb files from /var/cache/apt/archives/ . This  is where the packages are downloaded on ubuntu, before being installed. :D

Reply back if you have any problems.

PS:. this is the way you install all/any files on ubuntu available on the ubuntu apt repo.

---

### Post by kunaly2k on 2009-03-12
thanks bro! i downloaded all the packages you mentioned but many of them also depend on some more packages :-( which i have to download! do you know any easy linux version which comes with all mp3 and avi divx xvid codecs preinstalled? thanks for your help!

---

### Post by Partyboi2 on 2009-03-12
If you don't have Internet connection you could use a program called [[COLOR=Blue]keryx[/COLOR]]("http://keryx.betaserver.org/") to install packages.

---

### Post by avtolle on 2009-03-12
> **kunaly2k said:**
> thanks bro! i downloaded all the packages you mentioned but many of them also depend on some more packages :-( which i have to download! do you know any easy linux version which comes with all mp3 and avi divx xvid codecs preinstalled? thanks for your help!
You might take a look at Linux Mint; there is a version with the XFCE desktop for lower resource machines.

---

