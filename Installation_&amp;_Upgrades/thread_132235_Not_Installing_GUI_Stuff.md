---
title: "Not Installing GUI Stuff?"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by kLOTTiS on 2006-02-17
hey guys,
im new to linux and im trying to install ubuntu from a cd, i have a amd athlon 2400+ (32bit) 512mb ram and a 5gb linux partition, but after installing it it says it could not install all of the components, ~150mb of it isnt installed so it boots into the component install program thing and i select all of the components using + key and hit g for install, it installs all of the 150ishmb of stuff exept for 3 components, it boots to linux after to a black screen and plays a african drum noise, but the screen stays black

i can use ctrl+alt+f1 and log in, but when i try to install the xserver-xorg stuff that somone on another forum suggested, it says it cant find it or its not installed?

can anyone help please? i really want to use linux but i havnt got off to a smooth start!:confused:

---

### Post by stalefries on 2006-02-17
It seems that it doesn't have enough room to complete the install. I would try a "sudo apt-get clean", as that will clean out a lot of files that were used during the install. If after doing that, it still does not have enough room, I would try expanding the linux partition, and re-installing.

---

### Post by kLOTTiS on 2006-02-18
i used gparted to check my used space on my partition, and only had 3.3gb used

i resized the partition to 6.8gb

i reinstalled ubuntu and took photos of most of the errors so i can post them

after the african drums i used ctrl+alt+f1 and logged in, and then ran these commands

	$ sudo apt-get install xserver-xorg

i received

	reading package lists... done
	building dependancy tree... done
	E: couldnt find package xserver-xorg
	~ $

i then tried

	$ sudo dpkg-reconfigure xserver-xorg

responded

	~
	/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed


then there was another command that i used which i have forgotten which responded in a page long response

narrowed down to only important this it said

	errors were encountered while processing:
	  evolution
	  evolution-exchange
	  ubuntu-desktop
	E: sub-process /usr/bin/dpkg returned an error code (1)

$


i forgot to mention that i am dual booting with windows xp home and using GRUB

---

### Post by kLOTTiS on 2006-02-18
i ended up installing fedora core

---

