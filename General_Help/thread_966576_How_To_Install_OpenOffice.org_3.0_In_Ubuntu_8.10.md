---
title: "How To: Install OpenOffice.org 3.0 In Ubuntu 8.10"
date: 2008-11-01
forum: General Help
---

### Post by GuitarRocker2562 on 2008-11-01
Okay, I am sure some of you may be wondering how to easily upgrade OpenOffice.org from 2.4 to 3.0 in Ubuntu Intrepid Ibex, well it's really easy, and this tutorial will keep your OpenOffice.org installation up-to-date at all times!

Adding the OpenOffice.org repository to your sources list.

1. Open the terminal by going to Applications -> Accessories -> Terminal
2. Type 
```
sudo gedit /etc/apt/sources.list
```
3. At the bottom of the file, add the line
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```
4. Click on save, and then close the file.

Installing OpenOffice.org 3.0

1. Update apt-get's cache.
```
sudo apt-get update
```
2. Upgrade OpenOffice.org
```
sudo apt-get upgrade
```
3. Volia you have the latest version of OpenOffice.org installed.

---

