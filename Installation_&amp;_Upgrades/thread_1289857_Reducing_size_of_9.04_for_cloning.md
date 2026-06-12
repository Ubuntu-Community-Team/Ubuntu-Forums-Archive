---
title: "Reducing size of 9.04 for cloning"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by PhysicsBrown on 2009-10-12
I'd like to try whatever I can to reduce the size of my Ubuntu 9.04 installation. It *should* be easy to uninstall a bunch of low-priority stuff, such as all the games and the Presentation (Impress) and Drawing features of OpenOffice. I've used Applications -> Add/Remove to uninstall some things, but am not sure this is actually reducing the size of the installation or if perhaps it is retaining all the files somewhere.
 
I'm trying to "clone" an installation of Ubuntu 9.04 to a bunch of old laptops for my physics students. Each laptop has a CD-ROM and a single USB 1.1 port. Trying to use a nice utility called remastersys to build a live CD containing my system, I run into a tough problem: The custom.iso file it creates is too big to fit on a CD. And these laptops are not capable of booting from a USB port.
 
Any suggestions how I can reduce the size of the installation? When I do a raw installation of 9.04, then use remastersys to create a custom.iso file, it is barely under the 700 MB limit for a CD. But then Update Manager needs to do a huge number of updates, which brings the system size to over 800 MB. And then I also need to install the Java and Flash plug-ins. This all has to be set up by me at home, because the school district won't allow these laptops to be connected to their network! :confused:
 
As a last resort, I can try removing OpenOffice totally. But it would be nice to retain the word processor and spreadsheet for my students to use.

---

### Post by prshah on 2009-10-13
> **PhysicsBrown said:**
> 
Any suggestions how I can reduce the size of the installation? 

I'd suggest you start with a [minimal installation]("https://help.ubuntu.com/community/Installation/MinimalCD"), then add on packages as required. Trying to remove only Impress will not free up much space, as most of it's code will be shared with the other apps in the office suite; ie, open-office-base will take up the most space, I believe.

You can replace openoffice with lighter alternatives such as abiword, gnumeric, etc. if you feel it necessary.

Once you have a nice compact up-to-date installation in place, you can replicate it with remastersys.

---

### Post by earthpigg on 2009-10-13
what prshah said is correct.

i am very familiar with this process.

ubuntu is designed to squeeze as much as possible into that one CD-R, so as soon as you start adding things to it, you will have problems.

understand that what you want to do is essentially create a custom distribution of ubuntu.

when you do the minimal install and start adding packages, avoid meta packages!

example: instead of installing ubuntu-desktop, install gnome-core.

the best way to work on this is in a virtual machine.

[URL="http://sites.google.com/site/masonux/home/notes-to-myself"]
this link[/URL] describes the exact process that i use on a regular basis to accomplish what you are trying to accomplish (my .iso is under 350 mb).

your main 'apt-get install' line would be different, but the rest should apply exactly the same.

maybe something like:

```
sudo apt-get isntall xorg gdm gnome-core ubiquity synaptic firefox-3.5 pidgin remastersys jockey-gtk network-manager-gnome gnome-power-manager ubuntu-restricted-extras gcalctool openoffice.org
```

aaaand restart your (virtual) machine.


document the hell out of what steps you take. feel free to use my notes to myself as a start for your own notes to ***yourself*** document.

---

