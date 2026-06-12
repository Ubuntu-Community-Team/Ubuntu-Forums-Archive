---
title: "change permissions from root to usr for ext3 data partition?"
date: 2008-07-13
forum: General Help
---

### Post by streamsanddragonflies on 2008-07-13
hi! I'm sure there is a simple answer...I have a large ext3 data partition (sda6) which I want to use to render and store multimedia files.  At install Ubuntu gave only root read/write access for creating folders and directories.  I did some sudo mkdir and managed to move some media files there but when I tried to use the dvd:rip app. I could not get it to operate via that partition.

I was trying to save the following components on the data part. rather than 
in the /home default since it is too small for the project.

media/sda6/dvd-rip/dvdrip-data/vob
media/sda6/dvd-rip/dvdrip-data/avi
media/sda6/dvd-rip/dvdrip-data/tmp
and a prompt to choose where to save project as well.
 
dvd:rip gets stuck at the first step (storage selection)

"An internal exception was thrown!
The error message was:

mkdir /media/sda6/dvdrip-data: Permission denied at /usr/share/perl5/Video/DVDRip/Project.pm line 309"

I'm sure that changing the file permissions for that partition will do the trick.  Also I don't understand why a data partition needs root privileges!
I can't figure out how fix this-I want this whole partition to be non-root pls.?!

I'm a bit worried because I want to have a separate /home partition and even was thinking of /usr but I hope I don't to have to root to and from them?!

---

### Post by bodhi.zazen on 2008-07-14
use chown and chmod

you can use the -R flag to make it recursive

sudo chown -r user.users /media/sda6
sudo chmod 770 /media/sda6

change "user" to your user log in name.

---

### Post by mc4man on 2008-07-14
i wonder if just using Authorizations  to give yourself Explicit Authorization 'to mount filesystems from internal drives' would take care of all of that. I've used it on my partitions that don't mount at boot without issue.

---

