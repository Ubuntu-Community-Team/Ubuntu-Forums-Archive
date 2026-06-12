---
title: "Ubuntu Intrepid cannot be remastered: Ubiquity problem in OpenGEU"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by darkmaster on 2009-03-10
Hallo people, this is critic for me since if I don't solve it, there won't be a new OpenGEU release (I'm the creator of OpenGEU). I'm having troubles remastering Intrepid. I tried using Reconstructor, then UCK and then the official way described in the wiki:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

What I do is:
1) download the latest Ubuntu 8.10 and rip it. Then I immediately add my repos and gpg key.
2) apt-get update
3) apt-get upgrade
4) completely uninstall Gnome following this command:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
Of course, instead of installing kde, I install opengeu-desktop
5) I install the extra packages for the iso:
unrar unace p7zip p7zip-full arj abiword abiword-plugins claws-mail gimp gnome-games gnome-orca xscreensaver libdeskbar-tracker pidgin transmission-gtk vinagre xsane rhythmbox totem-gstreamer gnash jokosher hydrogen avidemux kino streamtuner sound-juicer ubiquity etkchanger firefox
That's because in step number 4 ubiquity is uninstalled.
6) apt-get clean and apt-get autoclean
7) I set the default session:
rm /usr/bin/x-window-manager
ln -s /usr/local/bin/enlightenment_start /usr/bin/x-window-manager
8) Change the files inside isolinux, like the png picture and the menu entries, so that OpenGEU is mentioned rather than ubuntu..
9) I change the contents of 50mirror ubuntu to add my repos.
10) I change an option into the ubiquity app launcher, so that it is not only shown in gnome and xfce
11) I change GDM, Usplash, etc.
12) Set my prefered files in etc/skel

Then I compile the iso and everything goes OK but... when I try to install it with ubiquity, at a certain percentage the installer tells me there's been an Imput/Output error and that this is often due to a bad working disc... but I'm using an iso :(

How is it possible? This is the way I always created OpenGEU 'till now. I never had problems except for this Intrepid release. Please help, this is really critical for me :(

Just for you to know, I tried modifying nothing but language packs, or installing Abiword and removing openoffice alone, to see if the problem was on my packages and not on Ubuntu side. No success. The installation after a remaster fails in ANY CASE I tried.

More than this, I even tried to run Ubiquity from terminal but there's no output error, so I cannot understand what's the problem.
More details can be found here:

[http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=44&func=view&catid=3&id=1266#1266](http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=44&func=view&catid=3&id=1266#1266)

What really makes me sad is that even manual reconstructing the distro without any automated tool or scripts generates no working installer... why? :_(

I really need help people. Ubuntu should be moddable. Right now, it is not.

---

### Post by darkmaster on 2009-03-16
Problem solved. Looks like the problem is VMWare Fusion: It is not possible to remaster intrepid in the latest VMWare Fusion. Hardy works, Intrepid does not, at least on my system. Using VirtualBox Solved the problem. Weird.

---

