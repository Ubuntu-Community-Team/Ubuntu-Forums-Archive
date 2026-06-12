---
title: "what exactly is apt-get?"
date: 2005-11-17
forum: General Help
---

### Post by Specialsauce on 2005-11-17
im totally a n00b, and i cant even get the internet set up..... and i hear alot about 'apt-get', but i have no clue what it is? what does this function do, and how is it useful?

---

### Post by DJ_Max on 2005-11-17
[https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto)
[http://www.us.debian.org/doc/manuals/apt-howto/index.en.html](http://www.us.debian.org/doc/manuals/apt-howto/index.en.html)

---

### Post by kruz on 2005-11-17
hey man im kruz
and welcome to ubuntu

apt-get is a program preinstalled in ubuntu breezy badger(which is prolly what u have if ur here)

that when u type the program name
if it finds it in the specified websites, it downloads it
configures it
checks depencies
and installs it
all by itself!!
basic usage

ill give u a tut
open console
and type
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo gedit /etc/apt/sources.list

it will open up in a notepad looking program
untick all the websites for most files
meaning take the # out before the word deb

now go to file>save>save as
and overwrite sources.list

now close that and go back to console and type

sudo apt-get update
sudo apt-get install (program name)
for example lets install xmms for listenin to files

sudo apt-get install xmms

oh crap it says we need missing files?

sudo apt-get -f install

then type xmms

hope this helps

---

### Post by Specialsauce on 2005-11-17
thanks...!

---

### Post by xequence on 2005-11-17
Basically apt is something you use to install things. You type "sudo apt-get install" and the program and it downloads and installs for you. You can also use it to remove the program to, replace "install" with "remove".

For example, "sudo apt-get install kubuntu-desktop" would download and install the kubuntu implemintation of KDE for you. When its finished you would have it completly installed and ready to use.

Wikipedia:
> Advanced Packaging Tool, or APT, is a package management system used by Debian and its derivatives. APT was originally designed to work with .deb packages on Debian systems, but it has since been modified to work with RPM packages via apt4rpm, and to run on other operating systems such as Mac OS X (see fink). On systems with package management based on .deb, such as Debian, APT is a front-end for dpkg.

APT simplifies the process of installing and removing software on Unix systems, by automating the retrieval, (from the Internet, local network, or CD) the configuration, the compiling (sometimes) and the installation of software from APT sources.


---

### Post by SickTwist on 2005-11-18
What the others say is correct. Apt-get is a method for installing and removing packages (programs, documentation, artwork, sounds). However, it is not the *only* way.

If you prefer to use a mouse rather than type commands in a terminal, you could use Synaptic which is a program that can achieve the same things that apt-get can. To run Synaptic, click on System --> Administration --> Synaptic Package Manager. You are able to search through an abundance of different programs, all of which can be installed easily. My favorite part is being able to use these tools to upgrade *every* installed package whenever a new version of Ubuntu is released. There is *nothing* comparable to this feature in the Windows world. ;)

Once you become familiar with the names of packages, you may find that it is more efficient for you to use apt-get than synaptic. However, they are both there and whichever one you use is up to you.

---

### Post by Rev. Nathan on 2005-11-19
So my question is if you download a package from the internet, such as an application not found in synaptic, like LiVES, for example, what do I do to install it? I could never figure out how to compile a package, and it would never work.
Do I extract it, cd to the directory, and type 'apt-get install LiVES'... or... what do I do?

---

### Post by matthewv on 2005-11-19
No. You type (in terminal)
```
sudo dpkg -i <nameofpackage.deb>
```

PS: I love your amaroK logo

---

### Post by darkmatter on 2005-11-19
yes...see above...

apt-get is a package management system for dpkg...synaptic is, in turn, a front end (GUI) for apt-get.

apt-get/Synaptic are for fetching .debs from the net/CD/local repository, otherwise a .deb must be installed with dpkg.

---

### Post by matthewv on 2005-11-19
[QUOTE=darkmatter]yes...see above...

apt-get is a package management system for dpkg...synaptic is, in turn, a front end (GUI) for apt-get.

apt-get/Synaptic are for fetching .debs from the net/CD/local repository, otherwise a .deb must be installed with dpkg.[/QUOTE]
and Add Applications is a front-end for synaptic...

---

### Post by samdude9 on 2005-11-19
apt-get is a update system.
its (jut about) that simple!

---

### Post by RAOF on 2005-11-19
[QUOTE=samdude9]apt-get is a update system.
its (jut about) that simple![/QUOTE]
That's a bit too simplistic.  Because I like the look of my own type, I'll add my own description: apt-get is an application manager - it deals with adding (downloading/installing), updating, and removing (uninstalling) applications.  And all the libraries they depend on, but that's sort of secondary.

---

### Post by Rev. Nathan on 2005-12-13
[QUOTE=matthewv]No. You type (in terminal)
```
sudo dpkg -i <nameofpackage.deb>
```

PS: I love your amaroK logo[/QUOTE]
Sorry for the rather large bump here, but is this also valid for .tar.gz packages I download? You know, the stuff you download, and if you extract it, it gives you instructions on compling a install-sh file, and then you have to... well... I could never get those to work. So does this do it for me, or what?

---

