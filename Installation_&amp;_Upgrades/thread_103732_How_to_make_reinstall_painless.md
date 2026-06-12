---
title: "How to make reinstall painless ?"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by B0rsuk on 2005-12-14
Hey

Long story short, I need to reinstall Kubuntu. It's not like I broke anything, I just realised 3GB is not enough for my / partition. By the way I'll remove 7GB winxp partition altogether; I found myself not using Windows anymore.
 I have 7MB free at the moment. There's so much more software available on repositories (more than in Windows, that is).And yes, I'm trying not to install unnecessary software. 
Things I need help with:

**How to extract a list of installed packages ?** preferably in a text file. I played around with Adept, apt-get and apt's config files and couldn't find anything. The idea is to look at the list once I do a fresh install, and install the "missing" packages manually. Because, you know, Kubuntu's install CD contains very little software by my standard - while installation itself takes little time, installing additional packages and customization takes quite a lot. I'm an IT student, so I use a lot of software that doesn't come by default (build essential, cvs, indent, blah blah... it's very annoying to forget one of them and having to use apt/adept each time)

Of course, I won't format/touch my /home partition, so no configuration lost here.

What else would you save in first priority ? I suppose xorg.conf is a good idea, just to make sure. /etc/network/interfaces, too.

Any other ideas to minimise damage and time lost ?

---

### Post by az on 2005-12-14
1.  If you have not cleared your cache of downloaded debs, you can make them into a cd:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

or
2.  If you did, you can still list your installed packages

dpkg -l
and use that list to install stuff on your clean install

or
3. You can try doing

sudo dpkg --get-selections >file

and save that file to floppy or usb drive and then reinstall and do

sudo dpkg --set-selections <file

and install them with dselect install or apt-get dselect-upgrade

or
4.  You can probably just copy your Ubuntu install partition to squash your winXp partition, delete the former 3 gig partition and resize the first partition back to the whole drive.  You have to grow the filesystem on the partition, too.  Do not forget to edit fstab and /boot/grub/menu.list and then chroot into the filesystem and run

grub-install /dev/hda (if that is the correct drive)
 

Number four is the quickest way, but you need to boot the install cd make your way to hardware detection and then , CTRL-ALT-F2 to the shell and do everything with the parted command line.

---

### Post by Herman on 2005-12-14
Ooops-simultaneous post with azz.

---

