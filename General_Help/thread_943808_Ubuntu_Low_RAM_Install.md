---
title: "Ubuntu Low RAM Install"
date: 2008-10-10
forum: General Help
---

### Post by weatherkid on 2008-10-10
I got a attack plan, I just don't know if it will work. What I want to do it install Ubuntu on 153 MB of RAM. I was going to install just the base system then install the desktop later. I know there is a CD just for the base system. I was going to put the desktop on a CD and install it from there. Is there a CMD to install from a Debian Package from a cd on a base system only install. Thanks ahead of time.

---

### Post by roger_1960 on 2008-10-10
Hi

You should download, burn and install Ubuntu Server edition 8.04 Then from terminal install the desktop.  It should work with your spec - to quote from the ubuntu site:

Ubuntu Server Edition is meant to run on any Intel or AMD x86, AMD_64, EM_64T processors as well as Sun Sparc T1 processors. It requires a minimum of 128Mb of RAM and 1Gb of disk space. Depending on your needs, you might manage with less than this. However, most users risk being frustrated if they ignore these suggestions.

I dont think ubuntu desktop edition will install on 153Mb

---

### Post by lavinog on 2008-10-10
I think the alternate install will work too.

---

### Post by marshag63 on 2008-10-10
I recommend using the alternate CD as well.  The server install gives you  server software - which you probably don't need.  Do a command line install - actually, there are many options you can choose from on the alternate install CD - from a true command line only setup to a regular install (via text install).

Good luck and enjoy!

mdg

---

### Post by Sam on 2008-10-10
Also you should try XFCE instead of Gnome. It has a small memory footprint. If you do a command line install using the alternate CD, install the xubuntu-desktop package.

---

### Post by yaknowwat on 2008-10-10
Xubuntu really wont be light enough for a system like that.

LXDE desktop setup should be chosen instead.

Mandriva 2009 Mini CD is capable of installing LXDE and is pretty nice to use.

the closest you'll get to lxde for ubuntu in ubuntulite (which is getting a name change soon due to legal issues )

[http://lxde.org](http://lxde.org)

They state what OS's use LXDE on their project page.

---

### Post by weatherkid on 2008-10-11
Slight problem guys, I don't have a internet on the computer I'm going to put Ubuntu so I need like a Full Deb. Package for a desktop.

---

### Post by marshag63 on 2008-10-11
weatherkid, the alternate install CD will do a full install - it just uses the text-based installer.  (Look at its size 699 MB - that's the full CD install - just uses a text based installer).

Good luck!  Let us know how it goes.

mdg

---

### Post by ugm6hr on 2008-10-11
> **marshag63 said:**
> weatherkid, the alternate install CD will do a full install - it just uses the text-based installer.  (Look at its size 699 MB - that's the full CD install - just uses a text based installer)

But is unlikely to be usable with <256MB RAM.

If you need an Ubuntu-based distro with an installation CD, try Xubuntu AlternateCD, which should at least allow you to install.  However, it is only marginally more usable than full-blown Ubuntu.

If you're prepared to use something unrelated to Ubuntu, try this list:
[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by lavinog on 2008-10-11
> **yaknowwat said:**
> Xubuntu really wont be light enough for a system like that.

LXDE desktop setup should be chosen instead.

Mandriva 2009 Mini CD is capable of installing LXDE and is pretty nice to use.

the closest you'll get to lxde for ubuntu in ubuntulite (which is getting a name change soon due to legal issues )

[http://lxde.org](http://lxde.org)

They state what OS's use LXDE on their project page.

I have ubuntu 7.10 installed on a computer with only 128mb of ram and it still functions as a desktop.

---

### Post by marshag63 on 2008-10-12
With about an 800 MB swap partition it should work decent.  I've had Ubuntu's cousin, Linux mint, running with 256 MB ram (gnome desktop).

As far as additional packages, you can download anything you might need from Ubuntu's repositories and put it on a CD-ROM.  Then in Synaptic, add the CD as a repository.  Hope that helps. 

Good luck!  Let us know how it goes.


mdg

---

