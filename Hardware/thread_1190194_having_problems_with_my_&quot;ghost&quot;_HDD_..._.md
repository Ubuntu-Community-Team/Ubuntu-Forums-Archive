---
title: "having problems with my &quot;ghost&quot; HDD ... wish to migrate and join you [xp user]"
date: 2009-06-17
forum: Hardware
---

### Post by C0NSTANTIN on 2009-06-17
MB: **nForce 680i LT**
HDD: **ST3340620AS**
Seagate Baracudda 7200.10 / 320 GB / S-ATA II

Steps i took thus far:

-windows xp sp2 wipe-out
-[COLOR=Red]clean-instal[/COLOR] Xubuntu with [swap] and [/home] as logical partitions all of them using [COLOR=Red]ext4[/COLOR] file system
-auto-upgraded
-messed arround with compiz/emerald packages
-rebooted
**ERROR "Alert! /dev/disk/my-uuid/<hdd id> not found / dropping onto a shell"**
-tried "mount" in shell using several arguments -> doesn't work
-tried some sodo scripts in the live xubuntu terminal -> does nothing

-entered BIOS, HDD [COLOR=Red]was[/COLOR] there!
-booted winXP install CD and [COLOR=Red]formated the 40GB [/root][/COLOR]
-runned xubuntu Live CD, still that /dev/disk/my-uuid error
-runned Knopix Live CD, didn't found my HDD
-runned Symphony OS Live CD, still didn't found my HDD
-installed WinXP sp2 on 20GB of the former linux-root partition
-xubuntu partitioner still insists i don't have a HDD
-runned winXP installation CD and [COLOR=Red]deleted [swap][/COLOR]
-the 4 gb released from [swap] won't cluster up with the other half of the former linux-root partition

Windows XP partitioner sees:
c: 20GB ntfs running XP
20 GB free space [with the first 20 GB made up root in xubuntu]
4 GB free space [former swap partition]
275 GB unknown partition [[COLOR=Red]this was my /home[/COLOR] ... and i have data on it i [COLOR=Black]must[/COLOR] recover]

Xubuntu partitioner sees:
nothing

Live CDs [xubuntu, knopix, symphony OS] sees:
no HDD

Installed Windows XP sees:
just the 20GB c:\

pls help :(

Right now i am on the Live Xubuntu CD ....

I am planning to check out the 20 and 4 gb partitions to see if i can make them add up and make a temporal ntfs partition ... surf the net for ext4 -> ntfs data recoverer or something ...

edit:
i want to migrate once and for all ... so sick of windows and corporate system.
i chose xubuntu because i wanted a light reliable linux that could support compiz and emerald later on ...
goal was a vista-like candy eye os that would use far less resources...
xubuntu+compiz+emerald=579mb ram vs Vista=1200gb
now i just want to recover my data on home :(( had all my projects there ..

---

### Post by C0NSTANTIN on 2009-06-18
Recovering the Data from the ext4 /home partition:

recovering the /home partition
-download and install the craked [piracy fan .. srry] version of [www.PTDD.com's](www.PTDD.com's) Partition Table Doctor 3.0
-the program will see ext4 file system as ext3 file system

recovering the data from the newly recovered partition
-download and install the craked [again .. srry] version of ...srry... this one's freeware :p
[http://www.data-recovery-software.net/Linux_Recovery.shtml](http://www.data-recovery-software.net/Linux_Recovery.shtml)
-again ... the program will see ext4 file system as ext3 file system
-run a scan first then recover

this worked for me.

so now i recovered all my 17GB of data... 

next step ... reinstalling xubuntu 9.04

planning on formating all partition tables ... making sure there isn't a trace of bad code not letting live CD xubuntu finding the HDD's uuid ...

---

