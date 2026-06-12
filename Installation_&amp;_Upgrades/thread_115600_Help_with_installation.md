---
title: "Help with installation"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by Pleeb on 2006-01-10
Ok so im new to linux in general but on my laptop i was trying to install my wireless card with ndiswrapper 1.7 but I can't the diections at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") this is what I keep getting 

pleeb@ubuntu:~$ cd ndiswrapper-1.7
pleeb@ubuntu:~/ndiswrapper-1.7$ make distclean
bash: make: command not found
pleeb@ubuntu:~/ndiswrapper-1.7$ sudo clean
Password:
Sorry, try again.
Password:
sudo: clean: command not found
pleeb@ubuntu:~/ndiswrapper-1.7$ make
bash: make: command not found
pleeb@ubuntu:~/ndiswrapper-1.7$
 
ny other friend who uses ubuntu can't figure out why the make distclean won't work I would much apericate any help

---

### Post by jasmuz on 2006-01-10
Maybe these links can help in some way[https://wiki.ubuntu.com/HowToSetUpNdiswrapper]("https://wiki.ubuntu.com/HowToSetUpNdiswrapper")
and
[https://wiki.ubuntu.com/SetupNdiswrapperHowto]("https://wiki.ubuntu.com/SetupNdiswrapperHowto")

But what i did for my machine was use the wired ethernet connection, to get the ndiswrapper ndiswrapper-utils and ndisgtk packages.

like this  sudo apt-get install ndiswrapper-utils ndisgtk
Once those packgages are installed you must check under System-->Administration-->Windows Wireless Devices.

Then proceed with giving the installer the .inf file needed.

Activate the card, and test it...once that goes well open a text editor and add to /etc/modules the word ndiswrapper so it gets loaded at boot time.

---

