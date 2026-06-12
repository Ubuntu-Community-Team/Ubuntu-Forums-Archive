---
title: "[SOLVED] vlc installation issue"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2008-12-06
i have tried to install by doing the following and am having an issue i would like to get a older version if recommended and possible.

richlyn@richlyn-desktop:~$ sudo apt-get update
[sudo] password for richlyn: 
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release             
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
richlyn@richlyn-desktop:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
richlyn@richlyn-desktop:~$ 


have also tried synaptic package manager its not  listed there!

please help
Thanks!

---

### Post by 2hot6ft2 on 2008-12-06
Well that command wouldn't get it anyway but you should run that a couple times then try
sudo apt-get install vlc

Looks like you may have synaptic open while you ran that since it says lock at the bottom so close synaptic first as it locks it, same as update manager does. Only use 1 installer at a time.

---

### Post by richlyn9 on 2008-12-08
Thanks a ton! that sure did work....

---

