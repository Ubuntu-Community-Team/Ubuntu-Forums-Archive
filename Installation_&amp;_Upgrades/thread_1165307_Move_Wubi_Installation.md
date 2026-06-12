---
title: "Move Wubi Installation"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by PureLoneWolf on 2009-05-20
Hi all

I seem to have a fairly unique requirement as far as my searches around the forum can discover.

I intend to move my wubi install to a dedicated partition and ultimately to remove windows.  Unfortunately, the space issues on my various drives are limiting that at the moment, so I need to move things around and replace a disk.

The smallest disk I have is a 160gb and, typically, this is where I chose to install my wubi install.

I have windows on /dev/sda1 and the wubi ubuntu on /dev/sdg1

I need to move my wubi install to any other partition (there are a number), which will then allow me to resize /dev/sda1 so that I can LVPM to a dedicated partition.

I presumed that I could edit the windows boot.ini and some grub files to point to the new location (ie /dev/sdh1)

I am happy to lose Windows in the process of all of this, but I really don't want to lose the (360gbs worth) of files on the Windows partition and I (of course) would rather not lose my current Ubuntu setup as it has taken me some time to get it to where I want it etc..

Sorry for the long winded/rambling post, I saw a similar question asked that was responded to with "Use LVPM" and wanted to be clear about my intentions to aviod this.

Is this possible?

Many thanks

---

### Post by Mark Phelps on 2009-05-21
AFAIK, using LVPM is the only way to cleanly "move" the installation.

You MIGHT be able to do what you want using the following approach.
1) Use AptOnCD to make a list of all your added packages
2) Plugin an external drive and copy off the entire contents of your /home directory and all subdirectories, including all hidden directories and files.
3) Uninstall the Wubi installation
4) Install Ubuntu afresh
5) Use the AptOnCD info to identify which packages to reinstall
6) Mount your saved /home partition and selectively copy files and directories over your existing /home partition files and directories

One wrinkle to this approach is that not EVERYTHING that is customized after install is written to a /home directory. Some stuff is written to places like /usr/share, /usr/local/bin, etc.  To find EVERYTHING that you added after the initial setup is going to be a daunting task.

---

