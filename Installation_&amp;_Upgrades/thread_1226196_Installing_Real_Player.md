---
title: "Installing Real Player"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by fierojo on 2009-07-29
When I attempted to load Real Player (.DEB file) the installation process starts, but then hangs when the dependencies are being generated.  Any thoughts?
 
Thanks.
 
S. Joe Wynman

---

### Post by TrakerJon on 2009-07-29
[URL="http://ubuntuforums.org/showthread.php?t=1181327"]
http://ubuntuforums.org/showthread.php?t=1181327[/URL]

Many of these installations require access to the Medibuntu Repository and enabling some additional software sources. Directions are on this site: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) or if you have Ubuntu 9.04 "Jaunty Jackalope" simply do the following from a terminal window:

sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install realplayer

---

