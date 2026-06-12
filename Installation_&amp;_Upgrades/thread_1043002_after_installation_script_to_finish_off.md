---
title: "after installation script to finish off"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by willemtwee on 2009-01-18
I install Ubuntu a lot for family and friends that want to have a Ubuntu Desktop or Laptop. The installation of Ubuntu is rather quick, but after I am done I always have to add the same kind of extra stuff. Like adding repositories, installing extra applications, putting off that irritant beep sound. And maybe I should do other stuf too, but that is for you to make a suggestion. Hopefully you can help and make suggestions to make the after installation script more fluent and less manually.

This is the script that I start now, Help me please to improve the script and have other Ubuntu installers to benefit as well!

Thanx!


#!/bin/bash
#
# backup sources.list
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
# add the following repositories manually to the sources.list
#
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
# deb [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu) intrepid main
# deb-src [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu) intrepid main
#
# add medibuntu and google gpg keys
wget --quiet [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O - | sudo apt-key add -
wget --quiet [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O - | sudo apt-key add -
# update repositories
sudo apt-get update
# install packages
sudo apt-get install vlc -y
sudo apt-get install amsn -y
sudo apt-get install htop -y
sudo apt-get install spamassassin -y
sudo apt-get install clamav -y
sudo apt-get install skype -y
sudo apt-get install wine -y
sudo apt-get install msttcorefonts -y
sudo apt-get install mono mono-runtime -y
sudo apt-get install googleearth-package -y
sudo apt-get install ubuntu-restricted-extras -y
sudo apt-get install inkscape -y
sudo apt-get install acroread mozilla-acroread acroread-plugins -y
sudo apt-get install adobe-flashplugin -y
sudo apt-get install sun-java6-plugin sun-java6-jre -y
sudo apt-get install mozilla-plugin-vlc -y
sudo apt-get install adobe-flashplugin -y
sudo apt-get install w32codecs -y
sudo apt-get install skype -y
sudo apt-get install miro -y
sudo apt-get install xbmc -y
sudo apt-get install planner -y
sudo apt-get install rar -y
sudo apt-get install unrar -y
sudo apt-get install p7zip-full -y
sudo apt-get install ntfs-3g -y
sudo apt-get install firestarter -y
sudo apt-get install nmap -y
sudo apt-get install nmapfe -y
sudo apt-get install likewise-open -y
# put off irritant beep sound
sudo rmmod pcspkr
# update repositories and upgrade packages
sudo apt-get update
sudo apt-get upgrade

---

### Post by hal8000 on 2009-01-18
Everyones requirements are different, but there are many great examples of Open Source Software.

I'm not sure what you're looking for but browse through Synaptic and you will see it is categorized into sections, so if you're looking for audio apps, you'd browse audio.

If you need a linux equivalent of some windows software this link may help:
[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

---

