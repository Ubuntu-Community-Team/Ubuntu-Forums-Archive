---
title: "kdesudo-kde4 cannot be removed"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by sgttomas on 2009-06-16
Hi.  I cannot automatically update my ubuntu because of complication that I somehow created while experimenting with KDE4 on my machine.  

I decided it wasn't for me and I tried to remove KDE4 using Synaptic Package Manager:
Removed the following packages:
adept
adept-batch
adept-installer
adept-manager
adept-notifier
adept-updater
jockey-gtk
jockey-kde
kde4libs-bin
kdebase-bin
kdebase-bin-kde3
kdebase-bin-kde4
kdebase-kio-plugins
kdesktop
kubuntu-kde4-desktop
language-selector
language-selector-qt
ubuntu-desktop
update-manager
update-notifier

 - - - - 

it also upgraded and installed a ton of stuff associated with this action.

Just before this time I also tried to update my system with the autoupdate but I was unable to complete the installation and had to abort.  It didn't really like me doing this, since it couldn't resume at a later time.  I was trying to figure out ways to correct this and this was when I tried removing KDE4.  Ever since, I have had the remnants of KDE4 left somewhere in my system , for instance:

epi@epi-laptop:~$ aptitude search kdesudo-kde4
Bd  kdesudo-kde4                                 - sudo frontend for KDE4  

and after typing in the command to remove KDE4 

sudo aptitude remove kdesudo-kde4
 - - - - -
it spits back at me:

The following packages will be REMOVED:
  kdesudo-kde4 
0 packages upgraded, 0 newly installed, 1 to remove and 955 not upgraded.
Need to get 0B of archives. After unpacking 172kB will be freed.
Writing extended state information... Done
(Reading database ... 179773 files and directories currently installed.)
Removing kdesudo-kde4 ...
Removing `diversion of /usr/lib/kde4/lib/kde4/libexec/kdesu to /usr/lib/kde4/lib/kde4/libexec/kdesu.distrib by kdesudo-kde4'
dpkg-divert: error checking `/usr/lib/kde4/lib/kde4/libexec/kdesu': No such file or directory
dpkg: error processing kdesudo-kde4 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kdesudo-kde4
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
epi@epi-laptop:~$ 
  - - - - - 

The root of this error is that those libraries are literally gone from my computer, but it keeps pointing to them for some reason.  Synaptic tells me that the frontend for KDE4 hasn't been removed and it is listed in the "broken" filter.  Trying to rectify this leads me to updating registries, but I can't do this because of the recursive loop of looking for KDE4 (so I am lead to believe from the messages I get when, for instance, trying:

epi@epi-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kdesudo-kde4
0 upgraded, 0 newly installed, 1 to remove and 955 not upgraded.
1 not fully installed or removed.
After this operation, 172kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 179773 files and directories currently installed.)
Removing kdesudo-kde4 ...
Removing `diversion of /usr/lib/kde4/lib/kde4/libexec/kdesu to /usr/lib/kde4/lib/kde4/libexec/kdesu.distrib by kdesudo-kde4'
dpkg-divert: error checking `/usr/lib/kde4/lib/kde4/libexec/kdesu': No such file or directory
dpkg: error processing kdesudo-kde4 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kdesudo-kde4
E: Sub-process /usr/bin/dpkg returned an error code (1)
 - - - - - - -

I've tried:
epi@epi-laptop:~$ sudo dpkg-reconfigure gdm


but it halts when encountering the errors in trying to remove KDE4 that I've already posted here. 

Now I can't update my ubuntu because it says the software index is broken:
*"It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."*

But I can't fix the software index because my computer isn't sure if I want KDE4 or Hardy Heron (or so I figure, from all the errors I am getting)

HELP!?!??!?!

I only know what I've been copying and pasting from forums, so I'm pretty much a n00b.

HELP!??!?!?!??!?!

---

