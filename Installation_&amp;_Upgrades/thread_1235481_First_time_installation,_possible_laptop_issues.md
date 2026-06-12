---
title: "First time installation, possible laptop issues?"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by RitterEvans on 2009-08-09
Hey all,

Have decided to give Ubuntu a boot on recommendation of a few friends and am running into a few problems..

First off I tried to install 9.04 onto a laptop already running XP and with 3 other partitions. Using the partition manager in the installer I attempted to erase these 3 and instate 3 new partitions, one /, one /home and a swap. Attempting installs from the CD and/or the hard drive (using Unetbootin) have results in failures, with the installer errors being essentially "Unable to unmount /cdrom, try again?" which brings me back to the partition manager.

I then tried to install 8.10, and whilst this version installed, it shows the boot logo and then loads to a blank screen.

All this has left me fairly scratching my head...

Another, possibly related issue is the curiousity that seems to be my desktop resolution in both Installers. When the Live CD loads, the mouse is presented to me as being in the bottom right quadrant of the screen whilst Ubuntu seems to think this is the middle of the screen, judging from its autoplacement of various windows.

This one's really baffling me guys, any help appreciated!

---

### Post by jerrrys on 2009-08-09
I installed Ubuntu 8.04 on a HP6000 laptop yesterday and was up and running in minutes.  The point being that your problems can be resolved, but if you want to get around the head scratching, 8.04 has a habit of working out of the box.

About partitioning, I do not partition like this.  Maybe someone more knowledgeable in this will come along.

---

### Post by phillw on 2009-08-09
[SIZE=2]As you seem to have so many variables (partitions).... 

The following article should explain it to you. Basically, one partition for XP, and an area for linux to use.

So, in your case - identify your XP partition, get rid of the others - to turn them into free-space, then make this one area ready for linux.

Be aware that re-partitioning can destroy data, so ensure you have your XP installation backed up.

[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)

I'm surmising that you want the XP/Linux how-to, with the XP having been put on 1st sub-choice.

It does install 9.04 - just use the instructions, it refers to 8.10 - it matters not, it is the methodolgy that works

It's an excellent how-to (I used the Vista version)

Let us know how you get on.

Regards,

Phill.
[/SIZE]

---

### Post by RitterEvans on 2009-08-11
I managed to get 8.10 installed, but now only recieve a blank screen on boot...
I'm running a Fujitsu Siemens A7610w laptop, with an AMD 1.8Ghz cpu and an S3 graphics adapter, and found buried deep in the forums of their site a post that gestured toward somebody else having a similar issue with the same machine.

Can Ubuntu run S3 graphics cards, or do I need to download a driver seperately and find some way of loading it at the same time as the Ubuntu installer? Or might anybody have another suggestion? I'm quite anxious to get it installed as I've never used this OS before and would like to play with it ;)

Cheers all!

---

