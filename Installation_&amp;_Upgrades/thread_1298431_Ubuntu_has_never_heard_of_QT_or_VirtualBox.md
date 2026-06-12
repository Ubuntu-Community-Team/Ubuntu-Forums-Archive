---
title: "Ubuntu has never heard of QT or VirtualBox?"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by brianpatrick on 2009-10-22
Hi,
I have some old software which only runs on windoz (please hold the tomatoes). Dragon Naturally Speaking does not run on Ubu 9.04, Suse 11.1 or Fedora 12. I thought I would try the latest Ubu 9.10. 

One would think that having C++ libraries and a good virtual machine would be 2 of the most essential items to build into any credible Linux distro. QT and VirtualBox are giants in their respective fields, but the Ubuntu gang has never heard of them? It's inconceivable. 

On my pristine install, "virtualbox" in Synaptic returned zero hits. After adding this line to my /etc/apt/sources.list
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free
it suddenly shows as installed, but it is not. The kernel module has never been installed, and the QT QUI has never been installed. 
root@trex:/home/brianp/download/qt# VirtualBox &
[1] 4143
root@trex:/home/brianp/download/qt# WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.31-14-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.
VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: libQtGui.so.4: cannot open shared object file: No such file or directory

Even the error messages are non-sequitur. Following the above instructions:
root@trex:/home/brianp/download/virtualbox# sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found

Synaptic shows it as installed while at runtime, none of the prerequisites have ever been installed. 

In Synaptic, QT shows 4 packages, none of which contain the letters 'QT'. I installed 300+ MB of the entire QT 4.5 software development kit, figuring I would probably need to compile something with it. Is it possible that the entire development environment does not contain a QT GUI? 

Searching for the missing library, libQtGui, it is installed:
root@trex:/home/brianp/download/virtualbox# locate libQtGui
/opt/qtsdk-2009.04/lib/libQtGui.so.4
/opt/qtsdk-2009.04/lib/libQtGui.so.4.5.3
/opt/qtsdk-2009.04/qt/lib/libQtGui.la
/opt/qtsdk-2009.04/qt/lib/libQtGui.prl
/opt/qtsdk-2009.04/qt/lib/libQtGui.so
/opt/qtsdk-2009.04/qt/lib/libQtGui.so.4
/opt/qtsdk-2009.04/qt/lib/libQtGui.so.4.5
/opt/qtsdk-2009.04/qt/lib/libQtGui.so.4.5.3

I tried setting the QTDIR:
root@trex:/home/brianp/download/qt# set QTDIR = /opt/qtsdk-2009.04/qt
>> failed: libQtGui.so.4: cannot open shared object file

Does anybody have VirtualBox running on Karmic? Could the Ubu Elves please ensure that both VB and QT install painlessly and transparently on a default install? PLEASE!

Thank you,

    BrianP

---

### Post by earthpigg on 2009-10-22
hi,

there are several things you are doing... oddly... that appear to be giving you problems.

1) > On my pristine install, "virtualbox" in Synaptic returned zero hits.

system -> admin -> software sources. make sure ***all available software*** is what synaptic is searching through. then refresh synaptic.

VirtualBox OSE will then be found.

i have a feeling that you did that on your previous/first ubuntu install, but then forgot that you ever did it, so did not remember to do it on this current/second install.

2) edit: nvm

3) > Could the Ubu Elves please ensure that both VB and QT install painlessly and transparently on a default install? PLEASE!

the Sun Microsystems elves have done so: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) > Please choose the appropriate package for your Linux distribution:

    * Ubuntu 9.10 ("Karmic Koala") i386 | AMD64 

[here]("http://sites.google.com/site/masonux/home/notes-to-myself#TOC-Tools") is my personal opinion on the difference between Virtual Box OSE (Open Source Edition) that you can get in the repos, and the proprietary version you can download from the link above.

---

### Post by jeremyswalker on 2009-10-22
Just to chime in...

@earthpigg: His line in sources.list is correct. That is the proprietary Virtualbox repository for Ubuntu. As shown here: [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

As for your problem, OP, have you tried uninstalling and reinstalling?

---

### Post by earthpigg on 2009-10-22
> **jeremyswalker said:**
> Just to chime in...

@earthpigg: His line in sources.list is correct. That is the proprietary Virtualbox repository for Ubuntu. As shown here: [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

As for your problem, OP, have you tried uninstalling and reinstalling?

yeah, i saw that and removed my mistaken comment. :D

---

### Post by emra2emra on 2009-10-23
Isn't Gnome != QT?
 
If you want QT you should run kubuntu?

---

### Post by earthpigg on 2009-10-23
> **emra2emra said:**
> Isn't Gnome != QT?
 
If you want QT you should run kubuntu?

you can run either from either, and it isn't at all uncommon to end up having both full toolkits installed.

---

### Post by cb951303 on 2009-10-23
> **emra2emra said:**
> Isn't Gnome != QT?
 
If you want QT you should run kubuntu?

virtualbox doesn't depend on any KDE parts/libraries. it depends on QT which is a general use GUI toolkit that happens to look native on GNOME. so no, he should not run kubuntu to work with virtualbox.

---

