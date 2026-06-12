---
title: "Graphical grub editor ubuntu 9,04"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by gordo97 on 2009-10-01
Just installed ubuntu 9.04 which duel boots with Windows and I am a newbie!

Came across a Grapgical grub editor QGRUBEditor which is dowmloadble as package

qgrubeditor_2.5.0-1_i386.deb and the following commandline was given to install qgrub

sudo dpkg -i qgrubeditor_2.5.0-1_i386.deb

Is this an acceptable command?  Ubuntu 9.04 would not execute it.  The package is on the desktop.  How should it be installed?

Is there a more recent version or alternative to qgrub?
I have seen menu.lst is used for editing the grub loader.  I need to change the grub boot order.  I have 3 Windows partitions and ubuntu.  I need to make one windows partition the default boot item in grub.

The graphical presentation of qgrub looks good and reasonably fool proof, providing it works.  

Can someone please help,  thanks

gordo97

---

### Post by oldos2er on 2009-10-01
There is an updated version of that program; however, it is an KDE app. If you have no other KDE apps installed, installing it will pull in quite a few dependencies.
```
sudo apt-get update && sudo apt-get install kgrubeditor
``` will do it.

 If you still wish to install the older Gnome version that you have downloaded (whether that's wise or not, I can't say), first run ```
cd Desktop
``` in a terminal, then retry your dpkg command.

---

### Post by rreese6 on 2009-10-01
My question, Since it seems like you already have the duel boot working, why do you think you need this program?

---

### Post by oldfred on 2009-10-02
If you just want it first:
You can also move the windows stanzas above the automagic line and leave the default to 0. In your menu.lst find these lines:

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
[COLOR=Red]Put windows stanzas here[/COLOR]
### BEGIN AUTOMAGIC KERNELS LIST

gksudo gedit /boot/grub/menu.lst

The ### begin line is about line 52 in my menu.lst

---

