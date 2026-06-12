---
title: "Can't install NDISwrapper..."
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by Balistic on 2007-05-29
Hi,
I have a dell e1705, with Intel wireless N, I'm trying to install the NDISwrapper but wasn't able to in any of the conventional ways.  I downloaded the latest version of the NDISwrapper and placed it on Ubuntu's desktop, then I opened the synaptic package manager, but I can't locate anything that has to do with NDISwrapper there, I also tried inserting the live cd, but for some reason I can't get synaptic to read from it.  also tries installing automatix but I get an error message saying "Error: dependency is not satisfyable python2.4" so I can't even install automatix.
I'm starting to wonder if there's something I'm doing wrong or its just that the installation I have of feisty is messed up..?  I haven't seen anyone with so many problem trying to install that NDISwrapper thing...
Anyway, you have any suggestions?

---

### Post by TheRingmaster on 2007-05-29
use automatix, it can install and configure ndiswrapper for you.

[www.getautomatix.com](www.getautomatix.com)

---

### Post by maksei on 2007-05-29
you seem to need to edit your apt sources
you can do this with
sudo apt-setup

or 

sudo apt-cdrom 
if you have repositories on cdrom

or by hand by editing the text file
/etc/apt/sources.list

you can do the same from synaptic, just have to click around the menus

---

### Post by Balistic on 2007-05-29
> **TheRingmaster said:**
> use automatix, it can install and configure ndiswrapper for you.

[www.getautomatix.com](www.getautomatix.com)

Dude... like I said I tried installing automatix but I got an error message.

---

### Post by Balistic on 2007-05-29
damn, no matter what I do, I can't get ndiswrapper-utils to show on my repository.
Is there anyway to d/l it?  Maybe I just need to reformat nad try to get a better dist?

---

### Post by rondackcpu on 2007-05-29
Balistic,

Someone suggested, correctly, I think, that Synaptic is not looking in the right places.  Here's my suggestion:  open "Software Sources" (System>Administration>Software Sources) and select all the offered choices.  Click close.  The system will respond that your lists are not up to date -- click "reload".  A bunch of files will be downloaded.  When it ends, there is a little bug in Ubuntu that greys out the dialog box.  Click on the upper right hand corner close box.  It will repeat the request to reload.  Ignore that.  Click the big close box.

Then try Synaptic again.  Ndiswrapper should now show up.  Click on both ndiswrapper-common and ndiswrapper-utils-1.8.  Accept any dependencies.  Click apply.  Click again to download.

If you need a further recipe for the application of ndiswrapper, get back to us.

Good luck.

CRS

---

### Post by jglen490 on 2007-05-29
Have you tried looking on your install CD for the .deb files?  That's where I found ndiswrapper and -utils for Dapper.  Look through your CD using Konq or your choice of file browser and install direct from the CD.

---

### Post by mikledet on 2007-05-30
I have the same situation, though now I managed to download and install manually the ndiswrapper-common and ndiswrapper-utils, and they do show up now in synaptic manager.  Now I have on my desktop the ndiswrapper installation files, so how do I install it?  I don't have network access yet, (since my problem is with the wireless driver...) so please advice of a method to install without a network connection.

---

### Post by zekica on 2007-05-30
To install ndiswrapper you need to download those two packages:
[http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common)
[http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)

You should then copy them for example to your Desktop.
Then you can double-click on **ndiswrapper-common_*_all.deb** and then on **ndiswrapper-utils-1.9_*_i386.deb**. This will install ndiswrapper.

Then you will need to find Windows drivers for your wireless card (.inf/.ini, .sys and maybe .bin files), copy them to one folder (for example Desktop) and then type the following in terminal:
[B]cd Desktop
sudo ndiswrapper -i *.inf[/B] (or *.ini)
[B]echo ndiswrapper | sudo tee -a /etc/modules
modprobe ndiswrapper[/B]

This should install the drivers.

---

